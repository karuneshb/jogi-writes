---
Category:
- Containers-and-Virtualization
- DevOps
Credits: 'Pearson course on LinkedIn: Essential Terraform in AWS by Dave Prowse'
Reference: https://github.com/daveprowse/tac-course
Status: In progress
createdAt: '2026-07-08T23:55:00.000Z'
title: Terraform in AWS
updatedAt: '2026-07-13T03:19:00.000Z'
---


# What’s Terraform?

- HashiCorp’s IaC (infrastructure-as-code) tool
- The tool we may use would be Terraform CLI
- Can be used with many popular cloud service providers (CSP) like AWS, GCP, Azure, VMware!
- Declarative code
- Ideal for constantly changing servers and infra deployments and modifications
- Terraform documentation: [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)

# Core Principles

| Versioned Infrastructure       | Multiple versions of code that should be under source code  |
| ------------------------------ | ----------------------------------------------------------- |
| Idempotence                    | Consistency, 1x or 1000x                                    |
| Self-Describing Infrastructure | The infrastructure <u>**is**</u> the code. Easily readable. |

_Note: While its easy to create and destroy infrastructure, bear caution while doing so as it may lead to unwanted data loss, or higher costs_

- Templates are available online to use

## Why Terraform?

- Robust with multiple CSPs
- Quick and Efficient
- Easy to read
- Use of state; allows to track changes between deployments
- Compatible with version control
- But, does not support user-defined functions

# Getting Started

### Installing Terraform

Using powershell

```powershell
#To install TF directly through the command line on PowerShell
winget install HashiCorp.Terraform
#Confirm installation as prompted

#To get started, while using autocomplete, powershell may show
# "terraform.exe" which is also fine
terraform -h

#initialize TF to initialize the directory, must be used before starting with anything, TF
terraform init
```

Using package manager

Using direct download

Using terminal on Mac

## How does Terraform work

1. Write the code
2. Initialize the directory
3. Apply your infrastructure

```powershell
terraform init

terraform apply
```

- Terraform codeblock architecture

```powershell
#This is the terraform block
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16" # the ~ operator ensures only the latest ofmajor version 4
										      # will be installed
    }
  }

						#can have more providers too
  required_version = ">= 1.2.0" #required version of TF
}


#This is the provider block. This is where provider and its regions and
#other provisioning information is written

provider "aws" {
  region = "us-east-2"
}

#Resource block is where we configure the infrastructure to be deployed
#When you change region, even ami below has to be changed

resource "aws_instance" "lesson_03" {
  ami           = "ami-0c7c4e3c6b4941f0f"
  instance_type = "t3.micro"

  tags = {
    Name = "Lesson-03-AWS-Instance"
  }
}
```

## Terraform Workflow

| Write                  | Code your TF configs in its own working directory. Then initialize that directory.              |
| ---------------------- | ----------------------------------------------------------------------------------------------- |
| Plan                   | Verify the config is valid and review the TF plan.                                              |
| Apply                  | Build the infrastructure based on the TF config.                                                |
| Use terraform commands | _init, fmt, validate, plan,_ _**apply**\_\_,_ _**destroy**_                                     |
|                        | \***\*terraform apply** will make chnages to infra and to the state of the file; cannot go back |

# Configuring AWS

## Installing AWS CLI on Windows

```powershell
#PowerShell as admin
Start-Process msiexec.exe -ArgumentList '/i https://awscli.amazonaws.com/AWSCLIV2.msi /qn /norestart' -Wait

#Close and reopen the PowerShell terminal
aws --version
```

## Creating a user and generating AWS Keys

1. Go to AWS Management Console —> Creating a new non-root user —> Create Access Keys —> Choose the CLI option —> Next —> Download `.csv` file
2. Open powershell and link these keys to Terraform.
3. The tool will prompt you for four items sequentially. Paste your keys and press Enter after each:

```powershell
aws configure

'''
AWS Access Key ID [None]: [Paste your Access Key ID from the CSV]
AWS Secret Access Key [None]: [Paste your Secret Access Key from the CSV]
Default region name [None]: us-east-1 (or whichever AWS region you plan to deploy your labs in, such as us-west-2)
Default output format [None]: json




'''
**Get-ChildItem -Path "C:\Users\$env:USERNAME\.aws" -Force

'''
You shall see**





'''
```

(Optional)

1. Verify that CLI keys are stored safely. And another command to peek inside these files to make sure default profile is set up

```powershell
Get-ChildItem -Path "C:\Users\$env:USERNAME\.aws" -Force


Get-Content -Path "C:\Users\$env:USERNAME\.aws\credentials"
```

By configuring a global `[default]` profile token through `aws configure`, local Terraform scripts will seamlessly pull state authentication permissions without exposing vulnerable parameters in plaintext configuration assets.

# First Terraform Configuration with AWS

## Initializing the Directory

> 💡 terraform init

Initialize this in the working folder. If its green, terraform has been initalized successfully.

Some new filles will likely be added to the working directory.

One of that will be a lock file `.hcl`which is manually generated. This file contains the hashes of the service provided we have initialized.

## Getting an ami image ID

```powershell
aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 --query "Parameters[0].Value" --output text
```

Use this command on powershell to get an ami image id that you could use with your Terraform infrastructure.

## Validating the Code

```powershell
terraform validate

#Expected output
Success! The configuration is valid.
```

Since Terraform depends only on the functions created by Terraform, it does not accept user-created functions. That makes it easier to debug the code. Even if you are using a code editor like VS Code, or working on PowerShell, it is so much easier to do this.

This inspects the code and ensures that the code itself is valid or not.

## Viewing the Terraform Plan

```powershell
terraform plan
```

This command shows the infrastructure plan that we are going to be using. It shows all the possible configurations we have provided so far, like `ami`, `instance_type`, `tags`, etc. Most of the fields will be `(known after apply)` because the service provider itself has not been initialized, or told that we want to run these services. They will be assigned once `terraform apply` is triggered.

We can also save the plan as a file to save it for later with the command

`terraform plan -out=plan_v1_0_0` or any name that seems appropriate.

> 💡 To apply the plan, use the command: `terraform apply "plan_v1_0_0"`  
> Note: A new instance will be created and running on AWS as soon as apply command is successfully executed.

    Note: A new instance will be created and running on AWS as soon as apply command is successfully executed.

## Applying the Infrastructure in AWS

Inspecting the .tfstate file gives a .json file. All the keys and values written here are exchanged when an instance was created on AWS and Terraform communicated with the AWS API.

Any change made to any instance deployed using Terraform will be updated and shown in the .tfstate file.

## Destroying the Infrastructure

```powershell
#Using apply subcommand
terraform apply-destroy

# OR using alias
terraform destroy
```

The console gives information that relates to the updates in the state file. Some of them are as follows:

```powershell
 # aws_instance.lesson_03 will be destroyed
  - resource "aws_instance" "lesson_03" {
      - ami                                  = "ami-0fd6240f599091088" -> null
      - arn                                  = "arn:aws:ec2:us-east-1:397393880874:instance/i-0cb342a36d1825c05" -> null
      - associate_public_ip_address          = true -> null
      - availability_zone                    = "us-east-1c" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 2 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - id                                   = "i-0cb342a36d1825c05" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t3.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0e42dcd7873c7551b" -> null
      - private_dns                          = "ip-172-31-23-128.ec2.internal" -> null
      - private_ip                           = "172.31.23.128" -> null
      - public_dns                           = "ec2-54-227-175-23.compute-1.amazonaws.com" -> null
      - public_ip                            = "54.227.175.23" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [
          - "default",
        ] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0c37d1cd375ae465b" -> null
```

Notice the value are going to be changed to null once this operation is confirmed.

> 💡 Bear extra caution while destroying an instance. Make sure it’s purpose has been fulfilled, and no other operations are running on the instance when you are deleting it.
>
> This is significant especially in production environments, or labs where data, processes and other operations are critical.

    This is significant especially in production environments, or labs where data, processes and other operations are critical.
