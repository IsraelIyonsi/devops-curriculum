# Week 8: Kubernetes in production, then the day-60 gate

Days 50 to 56, then the gate on days 57 to 60. Yellow licence; AI off for the gate.

Goal: by Friday the app runs on a real cluster in AWS, deployed by the pipeline with short-lived credentials, with access controls a reviewer can verify. A student who passes the gate starts applying for jobs that week.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. Helm: charts, templates, values, releases, upgrade and rollback, chart repositories; Kustomize as the overlay alternative
2. Managed versus self-managed clusters; what EKS runs for you; node groups; what it costs; k3s on one instance as the budget path
3. Creating the cluster from the Terraform module handed over as a Yellow-licence scaffold; kubeconfig from the CLI
4. Access entries (not the deprecated aws-auth ConfigMap); RBAC roles and bindings; service accounts
5. EKS Pod Identity for new clusters; IAM roles for service accounts for the clusters you will inherit; the difference between them
6. The AWS Load Balancer Controller; Gateway API or Ingress on EKS
7. StorageClasses on EKS (the EBS CSI driver); why the database stays on RDS for a small team
8. Quotas and limit ranges; admission control in concept
9. Deploying from CI: the pipeline assumes a role through OIDC, writes a kubeconfig at run time, runs helm upgrade
10. Cluster upgrades: deprecated APIs, control plane first, node groups rolling with disruption budgets
11. Revision of weeks 1 to 8 for the gate

## Tasks

### Day 1 (Mon)
- [ ] Write a Helm chart for the app with values files per environment; install, upgrade, roll back

### Day 2 (Tue)
- [ ] Read the EKS Terraform scaffold line by line; apply it (or k3s on a Spot instance on the budget path); write down the monthly cost before creating it
- [ ] Deploy the chart; expose the API through the AWS Load Balancer Controller

### Day 3 (Wed)
- [ ] Access entry plus a namespaced read-only binding for a developer identity; prove a delete is denied
- [ ] Pod Identity for the backup CronJob to write to S3; remove any S3 permission from the node role

### Day 4 (Thu)
- [ ] The pipeline deploys the chart on merge through an OIDC-assumed role; no kubeconfig in repository secrets
- [ ] Destroy and recreate the cluster from Terraform plus the pipeline alone
- [ ] Revision: the week summaries from weeks 1 to 7, read aloud

### Day 5 (Fri, project)
- [ ] A merge updates the running app on the cluster within ten minutes
- [ ] Oral drill

### The gate (days 57 to 60, AI and internet off except the cluster)
- [ ] 60-question oral screen across weeks 1 to 8; 45 clean answers to pass
- [ ] Whiteboard the path from a commit to a running pod, naming every credential and gate
- [ ] 30-minute break-fix on a cluster the instructor has sabotaged
- [ ] CV and LinkedIn written from the project log and reviewed
- [ ] First ten applications sent

Day 61 is an applications day. Days 62 and 63 are off. Week 9 starts on day 64, a Monday.

## Done when
- [ ] A merge updates the cluster within ten minutes
- [ ] The read-only user cannot delete a pod, proved with the denied command
- [ ] No long-lived kubeconfig or cloud key in repository secrets
- [ ] The cluster's monthly cost is written down before it is created

## Learning resources (free unless marked)

- Helm docs, start with "Using Helm" and "Chart template guide": https://helm.sh/docs/
- Kustomize: https://kustomize.io
- Amazon EKS best practices guide: https://docs.aws.amazon.com/eks/latest/best-practices/
- EKS access entries: https://docs.aws.amazon.com/eks/latest/userguide/access-entries.html
- EKS Pod Identity: https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html
- IAM roles for service accounts: https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html
- AWS Load Balancer Controller: https://kubernetes-sigs.github.io/aws-load-balancer-controller/
- terraform-aws-modules/eks (the scaffold's base): https://github.com/terraform-aws-modules/terraform-aws-eks
- k3s docs (budget path): https://docs.k3s.io
- Kubernetes RBAC: https://kubernetes.io/docs/reference/access-authn-authz/rbac/
