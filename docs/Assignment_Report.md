# Assignment 6 deployment report

## Architecture
Flask backend and Express frontend are included. Three target architectures are specified: both processes on one EC2 host; two EC2 hosts on a custom public VPC subnet; and container images in ECR deployed as ECS services behind an ALB.

## Commands for actual deployment
From the desired Terraform directory, prepare credentials and variables with AWS IAM least privilege and set a region-valid Ubuntu AMI, SSH key pair, and restricted CIDR. Run `terraform init`, `terraform validate`, `terraform plan -out=tfplan`, review, then `terraform apply tfplan`. Build/push ECR images and complete ECS task definitions before applying the ECS stack. Capture actual AWS console/terminal output and URLs after deployment.

## Current evidence
AWS CLI/credentials are not present. No plan/apply, EC2, ECR, ECS, or URL evidence exists. The configs are starter scaffolds; the user-data scripts and ECS services need completion before a real apply. Do not submit this as a live deployment proof.
