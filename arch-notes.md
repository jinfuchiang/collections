### Why my system time is not sync with Internet?
1. Check if ntp server is available: `sudo vim /etc/systemd/timesyncd.conf`
2. Check ntp service is start `sudo timedatectl set-ntp true`
3. Restart(Optional)`sudo systemctl restart systemd-timesyncd`
