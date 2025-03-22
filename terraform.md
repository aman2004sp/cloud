# Terraform-work

### Introduction
Terraform is a popular Infrastructure as Code (IaC) tool developed by HashiCorp, and it’s widely used for provisioning, managing, and automating infrastructure across various cloud providers
(e.g., AWS, Azure, Google Cloud) and on-premises environments.


## Installation  (Linux)

### 1. Update the System:
```
sudo apt update && sudo apt upgrade -y
```
![Screenshot (1)](https://github.com/user-attachments/assets/b9d99020-b516-4adc-9ca8-c6623d5e1edc)


### 2. Install Dependencies:
```
sudo apt install -y gnupg software-properties-common curl
```
![Screenshot (2)](https://github.com/user-attachments/assets/facd499e-105e-4e07-aa1e-a8d9400845ce)


### 3. Add the HashiCorp GPG Key:
```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

![Screenshot (3)](https://github.com/user-attachments/assets/b7e41f16-8b0a-41d9-8dbb-dc963a21fe6f)

### 4. Add the HashiCorp Repository:
```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
![Screenshot (4)](https://github.com/user-attachments/assets/93a1e4fa-dee8-483d-96d1-b67fd0939e85)

### 5. Install Terraform:
```
sudo apt update
sudo apt install terraform -y
```
-> Verify Terraform
```
terraform -version
```

![Screenshot (6)](https://github.com/user-attachments/assets/ddac5ae5-0fb1-4404-919c-d4d8424693d4)


------------------------------------------------------------------------------------------------------
## AWS CLI installation 
```
sudo snap install aws-cli --classic
```
![Screenshot (7)](https://github.com/user-attachments/assets/42525147-97d8-4586-823f-ea6b75783205)

-------------------------------------------------------------------------------------------------------

## AWS setup

### 1. IAM (Identify and Access management)
**-> Go to user groups in IAM -> Create a User Group
![Screenshot (8)](https://github.com/user-attachments/assets/5ac466a3-65fc-4a06-a0b9-0435fdb2bad0)
![Screenshot (9)](https://github.com/user-attachments/assets/7a470d2b-d1f8-48ed-91aa-e2c6af81ced3)


-----------------------------------------------------------------------------------------------------------------------
## Configure AWS:
```
aws configure


```

![Screenshot (11)](https://github.com/user-attachments/assets/39325b89-43f9-4feb-929c-9ad02f6555c3)

-> Manually Adding AWS Credentials
-
```
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY
region = us-east-1
```
-> Writing the Terraform Configuration File
-
```
mkdir terraform-ec2 && cd terraform-ec2

```

![Screenshot (12)](https://github.com/user-attachments/assets/50d5ae46-f690-40f1-88ad-083d84a6e1d5)

-> let's create a EC2 instance through code: - 
Create a file named ***main.tf***, and add the following configuration:

``` for example
provider "aws" {
    profile = "default"
    region  = "ap-south-1"
}

resource "aws_instance" "UGO_Server" {
    ami           = "ami-0cbf43fd299e3a464"
    instance_type = "t2.micro"

    tags = {
        Name = "MyNCAAInstance"
    }
}
```
use command 
```
nano main.tf
```

## Initializing and Applying Terraform

we need to initialize Terraform first !!
```
terraform init
```
![Screenshot (13)](https://github.com/user-attachments/assets/5907cf48-0f45-4071-b942-e7405edbfa69)

-> Check the Execution Plan
by Running
```
terraform plan
```
![Screenshot (16)](https://github.com/user-attachments/assets/1bb302e3-9c78-40fc-8f23-354101b64406)


-> Deploy your EC2 instance:
```
terraform apply -auto-approve
```
![Screenshot (18)](https://github.com/user-attachments/assets/8eae6744-ab7d-45a1-9ba8-42d96e823ac4)










