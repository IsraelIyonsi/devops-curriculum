# Week 10: Security and reliability

Days 71 to 77. Green licence.

Goal: by Friday no secret lives in Git or a ConfigMap, the pipeline refuses a critical vulnerability, a database restore has been timed, and you have run an incident and written the postmortem.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. Secrets: why not Git, environment files or ConfigMaps; AWS Secrets Manager and Parameter Store; the External Secrets Operator; sealed secrets; rotation
2. The first five minutes after a leak: revoke and rotate, check CloudTrail for what it touched, purge the history, postmortem
3. Supply chain: Trivy for images and infrastructure code; dependency scanning; SBOMs; image signing in concept (Sigstore cosign); pinning versions and actions
4. IAM least-privilege review; IAM Access Analyzer
5. Pod security standards; network policies (on EKS only with the VPC CNI policy feature turned on); read-only filesystems; dropped capabilities
6. TLS everywhere with cert-manager
7. Backups and the restore drill; recovery point and recovery time objectives
8. High availability versus disaster recovery; Multi-AZ; disruption budgets; graceful shutdown; timeouts and retries
9. Incident response: severity levels, the incident commander and communications roles, keeping a timeline, status updates
10. Blameless postmortems: the template, action items with owners and dates
11. Game day

## Tasks

### Day 1 (Mon)
- [ ] Move every secret into Secrets Manager; sync them with External Secrets; delete the hand-managed Kubernetes Secrets
- [ ] Rotate the database password without downtime; prove the app never noticed

### Day 2 (Tue)
- [ ] Make the Trivy gate block on critical; prove it with an old base image
- [ ] cert-manager issuing certificates on the gateway; IAM review with Access Analyzer, findings fixed
- [ ] Network policies: the database answers only to the API pods, proved from another pod; pod security standards enforced on the namespace

### Day 3 (Wed)
- [ ] Restore the database from backup into a fresh instance against a timer; record the RPO and RTO achieved
- [ ] Write the backup and restore runbook from what you just did

### Day 4 (Thu)
- [ ] Game day: the instructor breaks three things; you run the incident, keep the timeline, post status updates
- [ ] Postmortem within 24 hours, blameless, with owners and dates on every action item

### Day 5 (Fri, project)
- [ ] Verify no secret exists in Git history, a ConfigMap or a hand-managed Secret
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary

## Done when
- [ ] No secret in Git history, a ConfigMap or a hand-managed Kubernetes Secret
- [ ] An old base image blocks the pipeline; the database answers only to the API pods
- [ ] Restore completed under 30 minutes with data loss inside the RPO
- [ ] The postmortem follows the template and every action item has an owner and a date

## Learning resources (free unless marked)

- External Secrets Operator: https://external-secrets.io
- AWS Secrets Manager user guide: https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html
- cert-manager docs: https://cert-manager.io/docs/
- Pod Security Standards: https://kubernetes.io/docs/concepts/security/pod-security-standards/
- Network policies: https://kubernetes.io/docs/concepts/services-networking/network-policies/
- Network policies on EKS with the VPC CNI: https://docs.aws.amazon.com/eks/latest/userguide/cni-network-policy.html
- OWASP Kubernetes Top Ten: https://owasp.org/www-project-kubernetes-top-ten/
- Sigstore cosign: https://docs.sigstore.dev
- SLSA supply chain levels: https://slsa.dev
- Google SRE book, Managing incidents: https://sre.google/sre-book/managing-incidents/
- Google SRE book, Postmortem culture: https://sre.google/sre-book/postmortem-culture/
- PagerDuty incident response guide: https://response.pagerduty.com
