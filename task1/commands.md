# task1 终端常用命令练习笔记

> 练习环境：Ubuntu 22.04 LTS
> 记录人：@dantaipenghui-hue

本笔记整理任务一阶段在终端练习过的常用 Linux 命令，按用途分类并附练习示例。

## 1. 文件与目录操作

| 命令 | 功能说明 | 练习示例 |
| ---- | -------- | -------- |
| `pwd` | 显示当前所在目录 | `pwd` → `/home/dantaipenghui` |
| `ls` | 列出目录内容 | `ls -la` 查看含隐藏文件与权限 |
| `cd` | 切换目录 | `cd ~/task1`，`cd ..` 返回上级 |
| `mkdir` | 新建目录 | `mkdir -p task1/notes`（`-p` 支持多级创建） |
| `touch` | 新建空文件 | `touch hello.cpp` |
| `cp` | 复制 | `cp hello.cpp backup/` |
| `mv` | 移动 / 重命名 | `mv old.md README.md` |
| `rm` | 删除 | `rm notes.txt`，删目录用 `rm -r dir/` |

> 注意：`rm` 删除不可恢复，谨慎使用 `rm -rf`。

## 2. 查看文件内容

- `cat file`：一次性输出整个文件
- `head -n 20 file`：查看文件前 20 行
- `tail -n 20 file`：查看文件后 20 行；`tail -f log` 实时追踪日志
- `less file`：分页查看（`q` 退出，`/关键词` 搜索）

## 3. 用户与权限

- `whoami`：查看当前用户名
- `ls -l` 输出解读：如 `-rwxr-xr--`，依次为 属主 / 属组 / 其他人 的 `r(4) w(2) x(1)` 权限
- `chmod +x run.sh`：为脚本添加可执行权限
- `chmod 755 file`：属主 rwx，属组和其他人 r-x
- `sudo`：以管理员权限执行命令

## 4. 系统信息查看

| 命令 | 作用 |
| ---- | ---- |
| `uname -a` | 查看内核版本 |
| `lsb_release -a` | 查看发行版信息（验证 Ubuntu 22.04） |
| `df -h` | 查看磁盘占用 |
| `free -h` | 查看内存占用 |
| `top` | 动态查看进程与资源占用 |

## 5. 进程管理

- `ps aux`：列出当前所有进程
- `top`：动态监控进程
- `kill <pid>`：结束进程，`kill -9 <pid>` 强制结束
- `command &`：后台运行，`nohup command &` 退出终端后仍运行
- `Ctrl + C`：中断当前前台命令

## 6. 软件包管理（apt）

```bash
sudo apt update                   # 更新软件源索引
sudo apt upgrade                  # 升级已安装的软件包
sudo apt install git              # 安装软件
apt list --installed | grep git   # 查询软件是否已安装
sudo apt remove git               # 卸载软件
```

## 7. 查找与文本处理

- `find . -name "*.cpp"`：按名称查找文件
- `grep -rn "TODO" .`：递归搜索文本并显示行号
- 管道 `|`：`ls -la | grep task`，把前一个命令的输出作为后一个命令的输入
- 重定向：`echo "hello" > a.txt` 覆盖写入，`>>` 追加写入

## 8. 其他实用技巧

- `man <命令>`：查看命令手册（`q` 退出）
- `history`：查看历史命令
- `Tab` 键：自动补全命令与路径
- `clear` 或 `Ctrl + L`：清屏

## 9. 练习中遇到的问题

1. 目标名含空格时（如 `task 1`）会被当成两个参数，需要加引号；采用规范命名（如 `task1`）可避免此类问题，此前误建的 `task 1` 文件已整改。
2. `rm` 提示权限不足时需 `sudo`，但应先确认目标路径，避免误删系统文件。                                        
