# Assignment 6 — AWS Deployments (Krishna)

**Repository:** https://github.com/krishnaChandak044/tutedude-assignment-6-aws

Includes Flask and Express source plus Terraform scaffolds for the three required deployment modes: single EC2, separate EC2, and ECS/Fargate with ECR, VPC and ALB. See `terraform/` for configurations and `app/` for the Docker Compose local stack.

## Status and safe deployment
No AWS account/CLI credentials are configured in the workstation, so no cloud resources were created and there is no public deployment URL. This is a reproducible implementation package, not evidence of a live AWS deployment. Set region, region-specific AMI, EC2 key-pair name, and your public IP CIDR in `terraform/variables.tf`/tfvars. Then initialize and inspect a plan before applying. Do not apply until cost and IAM access are reviewed. Stop EC2 or destroy resources when finished; ALB/NAT/ECS-related resources may continue to incur charges.

EC2 bootstrap scripts are intentionally conservative placeholders for source synchronization and systemd service installation; add repository clone URLs and configured service unit files before applying. ECS task definitions/services and ECR image pushes are documented as follow-on setup in `terraform/ecs/README_NOTES.md`.
