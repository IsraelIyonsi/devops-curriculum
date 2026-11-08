# Week 11: GitOps and the capstone rebuild

Days 78 to 84. Green licence.

Goal: by Friday the whole platform can be rebuilt from an empty AWS account in under two hours with no console steps, a peer has done it from the README alone, and the deployment path has moved to GitOps.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. GitOps principles: Git as the single source of truth; push versus pull deployment
2. ArgoCD: installing it, Applications, the app-of-apps pattern, sync policies, self-heal, drift
3. The config repository: environments as directories; promotion by pull request; the pipeline bumps an image tag instead of deploying
4. Progressive delivery: Argo Rollouts canary gated on the error rate, as a concept and one demo; feature flags
5. Platform engineering: golden paths, what a platform team offers, developer experience as a product
6. Using AI in operations safely: agent credentials and least privilege, reviewing generated infrastructure code, hallucinated flags
7. Cost review: right-sizing, Spot, NAT, schedules for dev, retention
8. Documentation: the architecture diagram, runbooks, architecture decision records, the README a stranger can follow
9. The cold rebuild method: order of operations, what to script, where it usually stalls

## Tasks

### Day 1 (Mon)
- [ ] Install ArgoCD; put the app under an Application; change the pipeline so it only builds, scans and bumps the tag in the config repository
- [ ] kubectl edit a managed resource and watch self-heal revert it

### Day 2 (Tue)
- [ ] One canary rollout gated on the error rate (demo); write up when you would and would not use it
- [ ] The AI-in-operations session: write your own rules for what an agent may touch

### Day 3 (Wed)
- [ ] Cost review: cut the monthly bill by the amount set in the brief and list each saving
- [ ] Architecture diagram, runbooks index, three architecture decision records, README rewritten for a stranger

### Day 4 (Thu)
- [ ] Capstone day one: from an empty account, rebuild everything from Terraform, Helm, ArgoCD and the pipelines only, against a timer; log every stall

### Day 5 (Fri, project)
- [ ] A peer rebuilds from your README with no help; fold their notes back into it
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary; practise the two-minute platform pitch

## Done when
- [ ] Nothing is clicked in the console during the rebuild
- [ ] A peer succeeds from the README alone
- [ ] Every control from weeks 9 and 10 is present in the rebuilt platform
- [ ] Monthly cost under budget, with the savings listed

## Learning resources (free unless marked)

- OpenGitOps principles: https://opengitops.dev
- ArgoCD docs, getting started: https://argo-cd.readthedocs.io/en/stable/getting_started/
- Argo Rollouts: https://argoproj.github.io/rollouts/
- Architecture decision records: https://adr.github.io
- CNCF platforms white paper: https://tag-app-delivery.cncf.io/whitepapers/platforms/
- AWS Well-Architected, cost optimization pillar: https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html
- Team Topologies, Skelton and Pais (book, paid): where platform teams come from
