# Week 5: Cloud fundamentals on AWS

Days 29 to 35. Yellow licence opens: AI may scaffold boilerplate; you write every resource and every decision.

Goal: by Friday the app runs on AWS in the shape a real team would use, built by hand so that next week's Terraform replaces something you understand. Each topic names the Azure equivalent.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. The shared responsibility model; regions and availability zones; console versus CLI; short-lived CLI credentials
2. The Free plan and its credits; budgets and billing alarms; what costs money: NAT hours and data, data transfer out, every public IPv4 address, idle volumes, snapshots
3. IAM: users, groups, roles, policies; how a request is evaluated (explicit deny beats allow; identity versus resource policies; trust versus permission policies; AssumeRole); least privilege; why servers get roles, never keys
4. CloudTrail: the record of who did what
5. VPC: CIDR, public and private subnets, route tables, internet gateway, NAT gateway
6. Security groups versus NACLs; VPC endpoints (an S3 gateway endpoint removes NAT charges); peering versus Transit Gateway in one line
7. EC2: instance types, AMIs, user data, instance roles, IMDSv2, Session Manager instead of a bastion
8. S3: buckets, bucket policies, block public access, versioning, lifecycle rules, storage classes
9. RDS: managed Postgres, subnet groups, Multi-AZ, automated backups, parameter groups
10. ALB: listeners, target groups, health checks
11. CloudWatch: metrics, logs, alarms
12. Tagging; the Friday teardown discipline
13. The Azure map: subscriptions and resource groups, Entra ID and managed identities, VNet and NSG, VM, Blob, Azure Database for PostgreSQL, Application Gateway
14. Python with boto3: list untagged resources and estimate their cost

## Tasks

### Day 1 (Mon)
- [ ] Harden the account: MFA, admin user, budget alarm, CLI configured with short-lived credentials
- [ ] Create a role, assume it from the CLI, and read the AssumeRole call in CloudTrail

### Day 2 (Tue)
- [ ] Draw the VPC first: two public and two private subnets across two zones, route tables, IGW, one NAT gateway
- [ ] Build it; prove a private instance can reach the internet through NAT and cannot be reached from it

### Day 3 (Wed)
- [ ] EC2 in a private subnet with no public IP, reached through Session Manager; an instance role
- [ ] RDS Postgres in the private subnets; ALB in the public subnets with a health check on the API
- [ ] Backups to S3 through the instance role; block public access on the bucket

### Day 4 (Thu)
- [ ] CloudWatch alarms on CPU and ALB 5xx; tag everything
- [ ] Write the boto3 script that lists untagged resources
- [ ] Tear everything down; confirm the next day's bill is zero

### Day 5 (Fri, project)
- [ ] Rebuild the topology cleanly, logging every manual step (next week's Terraform must cover all of them)
- [ ] Prove the database is unreachable from the internet with a scan from outside; prove no keys sit on the instance
- [ ] Estimate the monthly cost with the pricing calculator
- [ ] Induced failures with debug log: security group blocks the health check; route table missing the NAT route; IAM policy denies the S3 write; RDS in the wrong subnet group; NAT gateway left running overnight
- [ ] Oral drill; teardown

### Weekend
- [ ] ai-log, one-page summary
- [ ] Python: extend the boto3 script into a cost report by tag

## Done when
- [ ] The app answers through the ALB DNS name
- [ ] The database is unreachable from the internet, proved
- [ ] No access keys exist on the instance
- [ ] Monthly cost estimated and under the budget; everything torn down with zero residual charges

## Learning resources (free unless marked)

- AWS Skill Builder, Cloud Practitioner Essentials (free course): https://explore.skillbuilder.aws
- IAM policy evaluation logic: https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html
- Amazon VPC user guide: https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
- EC2 instance metadata and IMDSv2: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html
- AWS Well-Architected Framework: https://aws.amazon.com/architecture/well-architected/
- AWS Pricing Calculator: https://calculator.aws
- boto3 documentation: https://boto3.amazonaws.com/v1/documentation/api/latest/index.html
- Azure for AWS professionals (the service map): https://learn.microsoft.com/en-us/azure/architecture/aws-professional/
