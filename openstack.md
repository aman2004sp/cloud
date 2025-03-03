# OpenStack-work

## Installing OpenStack in ubuntu using MicroStack 
```
sudo snap install microstack --beta
```
![Screenshot (30)](https://github.com/user-attachments/assets/f46dff66-c1b5-4266-ae3a-de9ee9bb6aef)


### 1. Initialize MicroStack
```
sudo microstack init --auto --control
```
This command:

* Sets up OpenStack services.
* Configures networking.
* Enables an internal bridge for virtual machines.

![Screenshot (31)](https://github.com/user-attachments/assets/55d49d17-1945-492f-89aa-a79d1aaf29a6)



### 3. Access OpenStack Dashboard
Once initialized, you can access the Horizon web dashboard:

-> Find the dashboard IP address:
```
ip a | grep inet
```
for example:-
![Screenshot (37)](https://github.com/user-attachments/assets/d32d0316-3d25-44eb-9298-67a2e616d139)


-> for password 
```
sudo snap get microstack config.credentials.keystone-password
```

-Go to web browser and search this above IP address:
```
http://<your-ip>:80
```
![Screenshot (33)](https://github.com/user-attachments/assets/e18d589b-a98e-45a9-b0af-1fe8ce6f67c8)


## Log in using the default credentials:

* Username: admin
* password: (from above)
![image](https://github.com/user-attachments/assets/18e701dd-5f18-4b59-9538-ce371884bb6f)

