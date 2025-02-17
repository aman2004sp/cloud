
```markdown
# Terraform and AWS CLI Setup Guide

## `sudo apt-get update && sudo apt-get install -y gnupg software-properties-common`
```bash
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
```
This command updates the package list and installs the `gnupg` and `software-properties-common` packages, which are required to securely add external repositories.

## `wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg`
```bash
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
This command downloads the HashiCorp GPG key and stores it to validate the integrity of the packages from HashiCorp repositories.

## `echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list`
```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
This command adds HashiCorp’s repository to the system's list of sources, enabling the installation of Terraform.

## `sudo apt-get update && sudo apt-get install terraform`
```bash
sudo apt-get update && sudo apt-get install terraform
```
This command updates the package list again and installs Terraform from the HashiCorp repository that was added.

## `terraform --version`
```bash
terraform --version
```
This command checks and displays the version of Terraform installed on the system, ensuring that Terraform is correctly installed.

## `sudo apt install awscli`
```bash
sudo apt install awscli
```
This command installs the AWS Command Line Interface (CLI), enabling interaction with AWS services directly from the terminal.

## `aws configure`
```bash
aws configure
```
This command sets up the AWS CLI with your AWS credentials, region, and default output format.

### Store credentials in `~/.aws/credentials`:
```plaintext
[default]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY
region = eu-west-2
```
This configuration sets your AWS credentials and default region in the AWS CLI.

## `mkdir terraform-ec2 && cd terraform-ec2`
```bash
mkdir terraform-ec2 && cd terraform-ec2
```
This command creates a new directory called `terraform-ec2` and changes the working directory into it.

## Create a file named `main.tf` with the following configuration:
```plaintext
provider "aws" {
    profile = "default"
    region  = "eu-west-2"
}

resource "aws_instance" "UGO_Server" {
    ami           = "ami-0cbf43fd299e3a464"
    instance_type = "t2.micro"

    tags = {
        Name = "MyNCAAInstance"
    }
}
```
This configuration file defines the AWS provider and the configuration for an EC2 instance using a specified AMI and instance type.

## `terraform init`
```bash
terraform init
```
This command initializes the Terraform working directory by downloading required provider plugins and setting up the environment for running further commands.

## `terraform plan`
```bash
terraform plan
```
This command generates and shows an execution plan, indicating what Terraform will do if you apply the configuration.

## `terraform apply -auto-approve`
```bash
terraform apply -auto-approve
```
This command applies the changes described in the configuration without requiring a confirmation prompt.

## `terraform destroy -auto-approve`
```bash
terraform destroy -auto-approve
```
This command destroys all the resources managed by Terraform, again without requiring a confirmation prompt.
```

