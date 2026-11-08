# DevOps curriculum: tasks

## Open decisions (Israel)
- [ ] Cloud: AWS primary with Azure named per lesson, or Azure primary
- [ ] Pace: 25 h/week over 90 days; 60-day-only (weeks 1 to 8 plus gate); or part-time at 12 h/week (about six months)
- [ ] Cluster cost: EKS by default, or k3s on one instance for everyone
- [ ] Sample application stack: .NET, Node or Go (sets the image size targets in week 3)
- [ ] Delivery mode: cohort with live Friday drills, or self-paced with recorded drills and a booked gate

## Verify before writing the weekly briefs
- [ ] Whether EKS is allowed on the AWS Free plan (accounts opened after July 2025), or students must upgrade to Paid before week 8
- [ ] Current replacements for ingress-nginx (Gateway API controllers) and Promtail (Grafana Alloy) named in weeks 7 and 9

## Next deliverables
- [ ] Sample app repository: API, worker, Postgres; health and metrics endpoints with a latency histogram; structured JSON logs with correlation IDs; OpenTelemetry traces; SIGTERM handling; a migration; fault toggles (memory leak, pool exhaustion, slow query)
- [ ] Twelve weekly briefs with acceptance criteria, the full question bank and model answers
- [ ] Sabotage scripts per week for break-fix
- [ ] Game-day runbook for week 10
- [ ] Gate packs: 60-question and 90-question oral exams, system design prompts, break-fix environments

## Done
- [x] 2026-11-08 Curriculum drafted, reviewed by an independent DevOps reviewer (20 findings), fixes applied
