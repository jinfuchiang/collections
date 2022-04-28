### Why my system time is not sync with Internet?
1. Check if ntp server is available: `sudo vim /etc/systemd/timesyncd.conf`
2. Check ntp service is start `sudo timedatectl set-ntp true`
3. Restart(Optional)`sudo systemctl restart systemd-timesyncd`
### [硬盘空间不够怎么办？](https://segmentfault.com/a/1190000041433509)
1. `df -h` 查看linux服务器的文件系统的磁盘空间，包括每个磁盘中的可用磁盘空间
2. `du -sh ./* | sort -hr | head -n 10` 目录文件大小排序
