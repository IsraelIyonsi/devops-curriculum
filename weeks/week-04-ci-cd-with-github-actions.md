# Week 4: CI/CD with GitHub Actions

Days 22 to 28. Red licence.

Goal: by Friday a merge to main reaches the live server with no human in the loop, a bad test blocks the merge, and a rollback has been timed.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. What CI/CD is and the problem it solves; CI versus CD versus continuous deployment; pipeline stages
2. GitHub Actions anatomy: workflow files, triggers, jobs, steps, runners
3. Status checks, required checks and branch protection
4. Caching, artifacts, matrix builds
5. Secrets and masking; least-privilege GITHUB_TOKEN permissions; OIDC to the cloud as a concept (used in week 6)
6. Building and pushing images tagged with the SHA; build once, deploy many
7. Trivy in the pipeline; failing on critical findings
8. Environments, required reviewers, concurrency groups
9. Deployment strategies: recreate, rolling, blue-green, canary
10. Deploying over SSH with a dedicated, command-restricted deploy key; smoke tests
11. Rollback by redeploying a previous tag; workflow_dispatch with inputs
12. Database migrations in a pipeline; expand and contract
13. Flaky tests; pipeline duration budgets; pinning actions by SHA; the tj-actions/changed-files compromise of March 2025
14. Branching rules for a team; what Jenkins, GitLab CI and Azure Pipelines share with Actions

## Tasks

### Day 1 (Mon)
- [ ] First workflow: lint and test on every pull request; make it a required check
- [ ] Break a test on purpose and watch the merge button lock

### Day 2 (Tue)
- [ ] Build and push both images with SHA tags; cache layers; measure the time saved
- [ ] Add the Trivy step; fail on critical

### Day 3 (Wed)
- [ ] Deploy to the VM on merge to main over SSH with a restricted deploy key; smoke test the health endpoint
- [ ] Rollback workflow that takes a SHA; production environment with one required approval

### Day 4 (Thu)
- [ ] Pin every action by SHA; set least-privilege permissions
- [ ] Time the pipeline; get it under ten minutes; write the team's branching rules

### Day 5 (Fri, project)
- [ ] Draw the pipeline from commit to running process
- [ ] Practise and time a rollback to the previous SHA
- [ ] Induced failures with debug log: secret missing from the environment; stale cache; deploy passes while the app returns 500; a flaky test; an expired token
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary
- [ ] Python and bash: top ten client IPs in the Nginx access log, both ways

## Done when
- [ ] A failing test blocks the merge
- [ ] A merge reaches the live URL with no manual step
- [ ] Rollback practised and timed
- [ ] The deploy key is restricted to the deploy command, and you can say why OIDC replaces it in week 6

## Learning resources (free unless marked)

- GitHub Actions docs, start with "Understanding GitHub Actions": https://docs.github.com/en/actions
- Security hardening for GitHub Actions: https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions
- docker/build-push-action: https://github.com/docker/build-push-action
- Trivy GitHub Action: https://github.com/aquasecurity/trivy-action
- Martin Fowler, Continuous Integration: https://martinfowler.com/articles/continuousIntegration.html
- Deployment strategies explained (blue-green, canary, rolling): https://martinfowler.com/bliki/BlueGreenDeployment.html and https://martinfowler.com/bliki/CanaryRelease.html
- Accelerate, Forsgren, Humble and Kim (book, paid): the four DevOps metrics every interviewer has read about
