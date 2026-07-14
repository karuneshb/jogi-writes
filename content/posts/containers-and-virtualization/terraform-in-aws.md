---
Category:
- Containers-and-Virtualization
- DevOps
Credits: 'Pearson course on LinkedIn: Essential Terraform in AWS by Dave Prowse'
Reference: https://github.com/daveprowse/tac-course
Status: In progress
createdAt: '2026-07-08T23:55:00.000Z'
title: Terraform in AWS
updatedAt: '2026-07-14T23:07:00.000Z'
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

```powershell
terraform init
```

Initialize this in the working folder. If its green, terraform has been initalized successfully.

Some new filles will likely be added to the working directory.

One of that will be a lock file `.hcl`which is manually generated. This file contains the hashes of the service provided we have initialized.

## Getting an ami image ID

```powershell
#We are pulling a Linux 2023 image
aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 --query "Parameters[0].Value" --output text

#TO get the latest Ubuntu image
aws ssm get-parameters --names /aws/service/canonical/ubuntu/server/24.04/stable/current/amd64/hvm/ebs-gp3/ami-id --query "Parameters[0].Value" --output text
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

## Formatting the Code

```powershell
terraform fmt
```

This command automatically standardizes the code with the Terraform conventions. It does not add or remove any characters, except tab spaces and spaces, with the purpose of aligning the code with the right indents.

## Viewing the Terraform Plan

```powershell
terraform plan
```

This command shows the infrastructure plan that we are going to be using. It shows all the possible configurations we have provided so far, like `ami`, `instance_type`, `tags`, etc. Most of the fields will be `(known after apply)` because the service provider itself has not been initialized, or told that we want to run these services. They will be assigned once `terraform apply` is triggered.

The terraform plan command scans code, but it does not fix the code.

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

A last-known good state will automatically be backed up and a new file will be created with the extension `.tfstate.backup`. This file will go away automatically when we run the command `terraform apply` again. In any case our main `.tf` file will not be touched.

# AWS Configuration with Security Groups

We will be adding two more resources that will configure the security groups for the deployed instances. The two security groups will be `aws_security_group` for `ssh` and `https`.

```powershell
resource "aws_instance" "lesson_04" {
  ami           = "ami-0c7c4e3c6b4941f0f"
  instance_type = "t3.micro"
  vpc_security_group_ids = [
    aws_security_group.sg_ssh.id,
    aws_security_group.sg_https.id
  ]

  tags = {
    Name      = "Lesson-04-VM-SG"
  }
}

resource "aws_security_group" "sg_ssh" {
  ingress {
    cidr_blocks = ["0.0.0.0/0"]
    protocol    = "tcp"
    from_port   = 22
    to_port     = 22
  }

  egress {
    cidr_blocks = ["0.0.0.0/0"]
    protocol    = "-1"
    from_port   = 0
    to_port     = 0
  }
}

resource "aws_security_group" "sg_https" {
  ingress {
    cidr_blocks = ["192.168.0.0/16"]
    protocol    = "tcp"
    from_port   = 443
    to_port     = 443
  }

  egress {
    cidr_blocks = ["0.0.0.0/0"]
    protocol    = "-1"
    from_port   = 0
    to_port     = 0
  }
}
```

The `ingress` and `egress`fields decide what connections are to be allowed inbound and outbound respectively.

## Exploring the Terraform Registry

> 💡 [https://registry.terraform.io/providers/hashicorp/aws/latest/docs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

Use this resource to learn about all the resources of not just AWS, but other providers. You can explore this registry to know more about how to use a particular resource and its code template.

## Validating and Creating Infrastructure

```powershell
#command entered:
terraform apply

#Output in terminal after running the command:
aws_security_group.sg_https: Creating...
aws_security_group.sg_ssh: Creating...
aws_security_group.sg_ssh: Creation complete after 4s [id=sg-090d75c7db447e08b]
aws_security_group.sg_https: Creation complete after 4s [id=sg-038e99a8b4d590599]
aws_instance.lesson_04: Creating...
aws_instance.lesson_04: Still creating... [00m10s elapsed]
aws_instance.lesson_04: Creation complete after 13s [id=i-0034798dcc99f27d0]

Apply complete! Resources: 3 added, 0 changed, 0 destroyed.
```

Terraform does not run the code in the order it is written. It runs the code in order with what it thinks should be done first.

So in our case, it created network infrastructure and security groups, and then building instances that use this infrastructure and security groups.

You may inspect the state file to validate the security groups present on the AWS Mangement Console.

> 💡 **Why does the SSH connection to the AWS Debian instance fail with 'Permission denied (publickey)'?**  
> The SSH connection fails with 'Permission denied (publickey)' because AWS requires you to use an SSH key pair for authentication instead of passwords. Even though the security group allows SSH on port 22, you need the correct private key that matches the public key associated with the instance to connect. This is a security measure AWS enforces to ensure secure access to your instances.

    The SSH connection fails with 'Permission denied (publickey)' because AWS requires you to use an SSH key pair for authentication instead of passwords. Even though the security group allows SSH on port 22, you need the correct private key that matches the public key associated with the instance to connect. This is a security measure AWS enforces to ensure secure access to your instances.

Similarly, the destroy command destroys the resources, groups and infrastructure in a reverse order.

```powershell
#command entered:
terraform destroy

yes

#Output
aws_instance.lesson_04: Destroying... [id=i-0034798dcc99f27d0]
aws_instance.lesson_04: Still destroying... [id=i-0034798dcc99f27d0, 00m10s elapsed]
aws_instance.lesson_04: Still destroying... [id=i-0034798dcc99f27d0, 00m20s elapsed]
aws_instance.lesson_04: Still destroying... [id=i-0034798dcc99f27d0, 00m30s elapsed]
aws_instance.lesson_04: Still destroying... [id=i-0034798dcc99f27d0, 00m40s elapsed]
aws_instance.lesson_04: Still destroying... [id=i-0034798dcc99f27d0, 00m50s elapsed]
aws_instance.lesson_04: Destruction complete after 51s
aws_security_group.sg_https: Destroying... [id=sg-038e99a8b4d590599]
aws_security_group.sg_ssh: Destroying... [id=sg-090d75c7db447e08b]
aws_security_group.sg_https: Destruction complete after 0s
aws_security_group.sg_ssh: Destruction complete after 1s

Destroy complete! Resources: 3 destroyed.
```

# AWS Configurations with SSH and Outputs

For this exercise, I created two folders namely, `instance` and `keys`. Since I am using Windows, I will be doing it on PowerShell.

```powershell
New-Item -Name "instance" -ItemType Directory
New-Item -Name "keys" -ItemType Directory
```

Generating key pair to use with AWS SSH.

```powershell
#To check if you system has SSH, which most definitely will be present
ssh -V

#Generate a key pair with ED cypher
ssh-keygen -t ed25519

#To save it in the same folder (not default), we already have a keys folder, so we
#will add the key pair in that folder.

#When prompted where to save
keys/aws_key

#Make sure that these keys are not publically available as they could compromise the
#security of SSH and ultimately AWS. Do not push them on GitHub if you are planning
#on doing what I am doing
```

## Building Terraform Files

I know you may think this is getting repetitive, but trust me, this one is not the same! We were writing code in a single file before this. Now we are going to create a couple of files, each independent of one another, yet related to the overall infrastructure.

```powershell
#Make the following files in the /instances directory
New-Item -Name "version.tf"
New-Item -Name "provider.tf"
New-Item -Name "main.tf"
New-Item -Name "outputs.tf"
```

Fill the fiels###########################################

```powershell
#For version.tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 6.0"
    }
  }

  required_version = ">= 1.5.0"
}
```

```powershell
#For provider.tf
provider "aws" {
  region = "us-east-1"
}
```

For this exercise, we will be using Ubuntu. Go here to get the latest image ID for ubuntu for your region [Getting an ami image ID](https://app.notion.com/p/3970336b2cc2806190dbd4038e3dd6a7#39c0336b2cc28025b6f4fed85ee9756c).

Copy the public key from the /keys/aws-keys.pub and paste in the field `public_key`. It should look something like this:

![image.png](/images/image.png)

Along with https, and SSH, we now have another http security group, and its configuration has been added in the `main.tf` file.

Copy over the code to `outputs.tf` as well!

```powershell
#Code for outputs.tf
# watch for an error here!

output "public_dns" {
  description = "DNS name of the EC2 instance"
  value       = aws_instance.lesson_05.public_dns
}

output "public_ip" {
  description = "Public IP address of the EC2 instance"
  value       = aws_instance.lesson_05.public_ip
}

```

Once all the files are saved, go ahead and let do `terraform init`, `terraform fmt`, `terraform validate`, `terraform apply`. Now, if you observer carefully, you shall see that after plan/apply, there is some extra information. That is the `Outputs:` which is done by our [`outputs.tf`](http://outputs.tf/) file to see some specific configurations or assignments or status of any properties of the instance. Some may need to be applied to get a real value instead of `(known after apply)`.

## Connecting via SSH to an Instance

We can use the `public_ip`field we got from the output to use to connect over SSH to the instance. We will also use the private key generated earlier from `/keys/aws_key`. The default username for Ubuntu systems is `ubuntu`.

```powershell
#Using the IP address assigned to me by AWS
ssh -i "../keys/aws_key" ubuntu@54.90.112.237

#Or you can use the public_dns address to SSH
ssh-i "../keys/aws_key" ubuntu@ec2-54-90-112-237.compute-1.amazonaws.com

#Or create a variable which directly takes input from the outputs file
ssh -i "../keys/aws_key" ubuntu@$(terraform output -raw public_ip)

#Or DNS
ssh -i "../keys/aws_key" ubuntu@$(terraform output -raw public_dns)
#We are using the -raw tag to get just the IP address and ignore the inverted commas

#Type yes when/if prompted and enter the passphrase if you had created it while
#creating the key pair

#To exit from the Ubuntu, press CTRL+D or type exit
```

While connecting later, you can use `terraform output` command to check your IP address. Using a variable is ideal for making scripts and sharing the code, while the other users of the same command can connect to their respective instances with a dedicated IP/DNS.

## Re-init or Reinitializing the working directory

There may be some cases where we might face errors or issues while applying infrastructure. We can start from square one while retaining the .tf files by using a simple command. To do this is fairly simple!

```powershell
#Use the rm commands
rm -r .terraform
rm terraform.tfstate
rm terraform.tfstate.backup
rm .terraform.lock.hcl
```

> 💡 Never imply what you want to apply! - Dave Prowse

# Terraform with Cloud-Init and Viewing Resources
