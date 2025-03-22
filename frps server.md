# frps-work
## Install FRP on your EC2 instance
```
wget https://github.com/fatedier/frp/releases/download/v0.49.0/frp_0.49.0_linux_amd64.tar.gz
```

![Screenshot (20)](https://github.com/user-attachments/assets/24dbcecc-6ef6-4304-8e4b-0345438e9ffd)

### -> Extract the downloaded FRP archive:
```
tar -xvzf frp_0.49.0_linux_amd64.tar.gz
cd frp_0.49.0_linux_amd64
```
![Screenshot (21)](https://github.com/user-attachments/assets/22dcae55-8d4d-4358-987d-7cf7d835359f)



-> Move the binaries to a system path
```
sudo mv frps /usr/local/bin/
sudo mv frpc /usr/local/bin/
```

### -> Configure FRP
Server Configuration
```
sudo mkdir -p /etc/frp
```
Create the FRP server configuration file
```
sudo nano /etc/frp/frps.ini
```
Example configuration for the server:
``` txt
[common]
bind_port = 7000
vhost_http_port = 8080
vhost_https_port = 443
```
![Screenshot (21)](https://github.com/user-attachments/assets/29ea9b20-b3d7-4fc2-b3d0-759ff0b3f641)


### -> Client Configuration (frpc)
-> Create the client configuration file:
```
nano frpc.ini
```
-> In frpc.ini file put this Example :
```
[common]
server_addr = your-ec2-public-ip
server_port = 7000

[web]
type = tcp
local_ip = 127.0.0.1
local_port = 80
remote_port = 8080
```
![Screenshot (25)](https://github.com/user-attachments/assets/c277f902-1cf0-446a-9541-456179022561)


### ->  Start the FRP Server (frps)
-> Start the server in the background:
```
sudo frps -c /etc/frp/frps.ini &
```
![Screenshot (26)](https://github.com/user-attachments/assets/bd689ac0-5932-439b-8b72-84d820e57a42)


-> To make FRP run as a service on startup, you can create a systemd service file:
```
sudo nano /etc/systemd/system/frps.service
```



