# Assignment 3
## Create a new directory
```bash
mkdir -p /web/html/nginx-2420
# mkdir creates a new directory 
# the p option allows to create parent directories
# if they don't exist
```
## Install software
```bash
sudo pacman -S vim nginx
# pacman is the installation manager for arch
# use it to install vim and nginx
# the -S option install it
# use sudo to execute commands that need authorization
```
## Start nginx
```bash
sudo systemctl start nginx
# systemctl manages services
# start starts the service
sudo systemctl status nginx
# checks the status of the service
sudo systemctl enable nginx
# creates a link to the service to start on boot up
```
## Create document to serve
```bash
cd /web/html/nginx-2420
# use cd to go to the directory
vim nginx-2420
# use vim to create and edit the file
```
## Copy this to vim
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2420</title>
    <style>
        * {
            color: #db4b4b;
            background: #16161e;
        }
        body {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            text-align: center;
            font-family: sans-serif;
        }
    </style>
</head>
<body>
    <h1>All your base are belong to us</h1>
</body>
</html>
```
## Save the file
Press esc and type `:wq` to save and exit 
## Edit the nginx config file
```bash
cd
# use cd to go back to the home directory
cd /etc/nginx
# go to config directory of nginx
# etc is usually where config files go to
vim nginx.conf
```
## Create separate server block
```bash
# edit the config file if needed
sudo mkdir sites-available
sudo mkdir sites-enabled
# create new directories in ngnix directory

# create a new file in sites-available directory
cd sites-available
vim nginx-2420
# type this:
server {
    listen  80;
    server_name localhost;

    location / {
        root    /web/html/nginx-2420
        index   nginx-2420.html
    }
}
# save it
# create symlink to enable the site
sudo ln -s /etc/nginx/sites-available/example.conf /etc/nginx/sites-enabled/nginx-2420
```
# Restart nginx
```bash
sudo systemctl restart nginx
# restart nginx to enable the changes to the site's configuration
```