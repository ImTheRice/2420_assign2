# 2420_assign2

Robeen Maharjan

## Files & Folders In Use

 - html **folder**
 
 - src **folder**
 
 - Caddyfile
 
 - caddy.service
 
 - hello_web.service

## Digital Ocean Infrastructure

![DOI](/Images/DOI.png)

## SSH Into Servers
 
![SSH](/Images/sshlogin.png)

note your ssh key and its location may differ 

## Install Volta, Fastify, Node, & Npm  

 1. Login as root into your servers
 
 2. Install Volta with `curl https://get.volta.sh | bash`
 
 ![Volta](/Images/installvolta.png)
 
 3. Refresh the termincal by using `exit` and re entering the server
 
 4. Install Node with `volta install node` << This will also install npm

 ![Node](/Images/installnode.png)
 
 5. Install fastify with `npm i fastify`

 ![Fastify](/Images/npmifastify.png)

## Downloading Caddy  

**(NGINX LAST WEEK)**

  1. Get Caddy with `wget https://github.com/caddyserver/caddy/releases/download/v2.6.2/caddy_2.6.2_linux_amd64.tar.gz`
 
  2. Untar with `tar xvf caddy_2.6.2_linux_amd64.tar.gz`
  
  3. You will have three files on each server
  
  ![Caddy](/Images/untar.png)
  
  4. Change the caddy file’s owner and group to root with `sudo chown root: caddy`

  5. Copy the caddy file to bin directory `sudo cp caddy /usr/bin/`
  
## Moving Folders **(BOTH SERVERS)**

  1. `sudo mv html /var/www/`
  
  2. `sudo mv src/* /opt/node/` << This will move the file inside src into /opt/node/
  
  3. The html should look like this: 
 
  ![html](/Images/makehtml.png)
  
  note the letter X in the html should be changed with `vim` to differentiate the two

## Moving Files **(BOTH SERVERS)**

  1. Create directory `sudo mkdir /etc/caddy/`

  2. The `CaddyFile` should be moved with `sudo CaddyFile mv /etc/caddy/`
 
  the file should look like this:
 
  ![CaddyFile](/Images/caddyfile.png)

  3. The `caddy.service` and `hello_web.service` should be moved with `sudo mv caddy.service /etc/systemd/system` & `sudo mv hello_web.service /etc/systemd/system ` 
  
  4. The caddy service file look like this:
  
  ![Caddyservice](/Images/caddyservice.png)
  
## Starting Services **(BOTH SERVERS)**
  
  1. Reload systemctl with `sudo systemctl daemon-reload`
  
  2. Enable with `sudo systemctl enable hello_web.service` & `sudo systemctl enable caddy.service`
  
  3. Check with `sudo systemctl status hello_web.service` & `sudo systemctl status caddy.service`
  
  4. Both should state `Active`
  
  5. You should be able to now view the boad loader's IP and see:
  
  ![Success](/Images/server1.png)
  
  ![Success](/Images/server2.png)
  
  6. And the Ip followed with /api should return

  ![Success](/Images/api1.png)
  
  ![Success](/Images/api2.png)
