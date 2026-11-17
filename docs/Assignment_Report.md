# Assignment 6 — AWS application deployment report

## Architecture
Flask backend and Express frontend are included. Three target architectures are specified: both processes on one EC2 host; two EC2 hosts on a custom public VPC subnet; and container images in ECR deployed as ECS services behind an ALB.

## Implementation and validation
Terraform configurations are included for single EC2, separate EC2 instances in a VPC, and ECR/ECS Fargate with an ALB. All six Terraform roots across Assignments 6 and 8 passed `terraform validate`. The ECS configuration supports a staged image workflow: create the infrastructure with `deploy_services=false`, push the Docker images to ECR, then enable services.

## Current evidence
AWS CloudShell reported account verification in progress and could not create a shell environment. No plan/apply, EC2, ECR, ECS, or public URL evidence exists. See the README and `terraform/README.md` for deployment steps and required variables. The archive does not claim a live deployment.
