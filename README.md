# terraform-aws-ec2-s3-project
Terraform project that provisions an EC2 instance with SSH access, a versioned S3 bucket, and IAM role-based access between them.

# Terraform AWS Infrastructure Project

## Project Overview

This project was developed to get my feet wet using Terraform. The goal for this scenario based project was to build a basic, secure AWS environment for a new development team using Terraform. All code was written from scratch based on Terraform and AWS documentation.

## Scenario

As a Cloud Administrator at a small tech company, I was tasked with provisioning infrastructure for an incoming development team. The environment needed to support secure testing of applications and basic file storage capabilities in AWS.

## Infrastructure Provisioned

The following AWS resources were created using Terraform:

### 1. EC2 Instance
- Operating System: Amazon Linux 2
- Instance Type: `t2.micro`
- Tags:  
  - `Name = DevOpsTestServer`

### 2. Security Group
- Inbound Rules:  
  - Allow SSH (port 22) **only from my IP address**
- Outbound Rules:  
  - Allow **all outbound traffic**

### 3. S3 Bucket
- Uniquely named using a combination of my initials and a random number
- Versioning enabled
- Tags:  
  - `Environment = DevOpsTest`

### 4. IAM Role and Policy
- IAM Role attached to the EC2 instance
- Custom policy granting read and write access to the S3 bucket

### 5. Outputs
- The EC2 instance's public IP address
- The name (ID) of the S3 bucket

## File Structure

- `main.tf`: Defines the infrastructure resources
- `variables.tf`: Declares input variables for flexibility
- `outputs.tf`: Outputs key information after deployment
- `.terraform.lock.hcl`: Locks provider versions for consistent behavior
- `.gitignore`: Excludes state files, Terraform cache, and sensitive data

## Notes

- Project was tested using `terraform init`, `terraform plan`, and `terraform apply`
- Code is organized and written following Terraform best practices for readability and maintainability
