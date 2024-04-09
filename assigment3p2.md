# Assignment 3 Part 2
## Installing UFW
```bash
# Install ufw
sudo pacman -S ufw
# Start the service
sudo systemctl enable --now ufw.service
# --now starts and enable the service now

# check the status of ufw
sudo ufw status verbose
# it should be inactive since it was just installed
```
## Setting up UFW
```bash
# setup ufw by using the commands: allow, deny and limit
# ex sudo ufw allow from 203.0.113.0/24 to any port 22
# ex sudo ufw deny from 203.1.113.4
# ex ufw limit ssh
# allow SSH and http
sudo ufw allow SSH
sudo ufw allow http
# limit SSH 
sudo ufw limit SSH
# now start the firewall
sudo ufw enable 
```