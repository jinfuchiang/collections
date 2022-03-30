## Shell
### 公私钥 for ssh
```shell
ssh-keygen -t ed25519 -C "jinfuchiang@outlook.com"
# Copies the contents of the id_ed25519.pub file to your clipboard
clip < ~/.ssh/id_ed25519.pub
# 将粘贴板的内容追加至服务器的~/.ssh/authorized_key文件
```
### pacman包升级操作
- 更新包数据库后应立即更新所有已安装的包
- 原因：<a href = "https://wiki.archlinux.org/title/System_maintenance#Partial_upgrades_are_unsupported">Arch不支持部分更新包</a>
- 使用下述命令确保总能安全地升级
```shell
# S表示sync y表示部分更新包数据库
# yy代表全面更新包数据库 u代表更新所有已安装的包
# 加packages表示安装包
pacman -Syu [packages]
pacman -Syyu [packages]
# never do: pacman -Sy && pacman -S [packages]
```
