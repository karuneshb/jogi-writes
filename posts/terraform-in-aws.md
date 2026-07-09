---
createdAt: "2026-07-08T23:55:00.000Z"
updatedAt: "2026-07-09T01:10:00.000Z"
Status: "In progress"
Credits and Reference: "Pearson course on LinkedIn: Essential Terraform in AWS by Dave Prowse"
Dave Prowse: "https://github.com/daveprowse/tac-course"
title: "Terraform in AWS"
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
