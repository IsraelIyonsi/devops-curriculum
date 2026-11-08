# Week 6: Infrastructure as code with Terraform

Days 36 to 42. Yellow licence.

Goal: by Friday everything built by hand last week is destroyed and recreated by terraform apply with no console steps, and the pipeline plans infrastructure changes on every pull request.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. Why infrastructure as code: drift, repeatability, review, disaster recovery; declarative versus imperative; idempotence
2. Installing Terraform; providers; init; the first resource; plan, apply, destroy
3. Reading a plan: create, update in place, replace, destroy; why a replace on anything stateful is the red flag
4. State: what it is, local versus remote, the S3 backend with native locking (use_lockfile, Terraform 1.10 and later; DynamoDB locking as the legacy you will still meet)
5. Variables, outputs, locals, tfvars
6. Data sources, references and the dependency graph
7. Modules: inputs and outputs; splitting into network, compute and database
8. moved and import blocks; replace; lifecycle ignore_changes
9. Environments: one root per environment, separate state, the same modules
10. Secrets: let the service own them (RDS-managed master password); ephemeral resources and write-only arguments; sensitive outputs; why state must be encrypted and restricted
11. fmt, validate, tflint, Checkov
12. CI: plan on pull request and apply on merge with approval, both through an OIDC-assumed role
13. Drift: how to detect it and the three ways to resolve it
14. The rest of the landscape: Ansible (configuration management versus provisioning); CloudFormation, Bicep, Pulumi, CDK in a sentence each; OpenTofu and why it exists

## Tasks

### Day 1 (Mon)
- [ ] Recreate last week's VPC in Terraform; read the plan line by line before applying
- [ ] Change a CIDR and read what the plan wants to replace; do not apply it

### Day 2 (Tue)
- [ ] Move state to S3 with locking; open two terminals and watch the lock refuse the second apply
- [ ] Split into network, compute and database modules; add outputs the other modules consume

### Day 3 (Wed)
- [ ] dev and prod roots with separate state and tfvars
- [ ] Create the OIDC provider and a role for GitHub Actions; the pipeline runs plan on pull request and apply on merge with approval

### Day 4 (Thu)
- [ ] Let RDS manage its master password; confirm no secret appears in state or plan output
- [ ] Add fmt, validate, tflint and Checkov to the pipeline; fix what Checkov finds
- [ ] One hour on Ansible as a concept; one sentence each on the alternatives; read the OpenTofu story

### Day 5 (Fri, project)
- [ ] Destroy last week's hand-built environment; terraform apply from zero; confirm the app answers
- [ ] Edit a security group in the console; show the drift on the next plan; resolve it
- [ ] Rename the database resource in code; read the plan that would replace it; fix it with a moved block
- [ ] Induced failures with debug log: stuck state lock; provider version bump; a secret leaking into plan output
- [ ] Oral drill; destroy

### Weekend
- [ ] ai-log, one-page summary
- [ ] Ansible exercise: one playbook that installs and configures Nginx on a throwaway VM

## Done when
- [ ] terraform destroy then apply yields a working app with no console step
- [ ] A console change shows as drift on the next plan
- [ ] A reviewer can read the plan on a pull request and say what will change; no long-lived cloud key exists in repository secrets
- [ ] You can explain state, and why it is remote and locked, to someone non-technical

## Learning resources (free unless marked)

- Terraform tutorials, get started on AWS: https://developer.hashicorp.com/terraform/tutorials/aws-get-started
- Terraform AWS provider docs: https://registry.terraform.io/providers/hashicorp/aws/latest/docs
- The S3 backend, including use_lockfile: https://developer.hashicorp.com/terraform/language/backend/s3
- Terraform state purpose and remote state: https://developer.hashicorp.com/terraform/language/state
- moved and import blocks: https://developer.hashicorp.com/terraform/language/moved and https://developer.hashicorp.com/terraform/language/import
- Ephemeral resources and write-only arguments: https://developer.hashicorp.com/terraform/language/resources/ephemeral
- Configuring OpenID Connect in AWS for GitHub Actions: https://docs.github.com/en/actions/security-for-github-actions/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services
- Checkov: https://www.checkov.io/1.Welcome/Quick%20Start.html
- tflint: https://github.com/terraform-linters/tflint
- OpenTofu: https://opentofu.org
- Ansible, getting started: https://docs.ansible.com/ansible/latest/getting_started/index.html
