# Assignment 6 — AWS Deployments (Krishna)

**Repository:** https://github.com/krishnaChandak044/tutedude-assignment-6-aws

## Included

- Flask/Express source and container definitions in `app/`.
- Terraform module `terraform/single_ec2` for both apps on one EC2 instance.
- Terraform module `terraform/separate_ec2` for Flask and Express on separate EC2 instances in a VPC/subnet with security groups.
- Terraform module `terraform/ecs` for two ECR repositories, VPC/public subnets, ECS/Fargate tasks/services, CloudWatch log group, ALB and `/api/*` routing.
- Per-module `variables.tf`, `outputs.tf`, S3 remote backend configuration and example tfvars.

## Validation and live status
All six Terraform roots across Assignments 6 and 8 passed `terraform validate`. AWS resources were not deployed: AWS CloudShell currently reports that account verification is in progress and it cannot create the shell environment (up to two days). No AWS CLI credentials are available locally, so there is no public URL or AWS runtime screenshot yet. The console currently shows $100 credits; EC2/Fargate, public IPv4, ALB, CloudWatch and storage usage can consume credits or incur charges beyond them.

## Deploy after account verification
1. Configure an AWS CLI identity with least privilege, select `ap-southeast-2`, and create a private, versioned, encrypted S3 state bucket.
2. For `single_ec2` and `separate_ec2`, set the region-valid Ubuntu AMI, EC2 key pair and your public IP `/32` in tfvars. Run `terraform init` (see module README for S3 backend flags), `terraform validate`, review `terraform plan`, then apply.
3. For `ecs`, first apply with `deploy_services=false` to create ECR/VPC/ECS/ALB resources. Build and push images using `terraform/ecs/push-ecr-images.sh` with the two ECR URIs from Terraform outputs. Apply again with `deploy_services=true` to run the services.
4. Capture real URLs and screenshots, then run `terraform destroy` in each module to stop billable resources. ECR images and the S3 state bucket may require separate cleanup if no longer needed.

No deployed URL is claimed in this package.
