# Zero to DevOps: The 90 Day Fast Track

A curriculum that takes a complete beginner to an intermediate DevOps engineer in 90 days: able to pass a technical screen by day 60 and to build, run and defend a production platform by day 90.

Every topic is taught as what it is, why it exists and how it breaks, because that is what short interview questions test. One sample application (an API, a worker and Postgres) travels the whole delivery path: a server, a container, a pipeline, a cloud account, Terraform, a cluster, dashboards, secrets, GitOps.

- Full curriculum, with lesson tables, projects and interview drills: [CURRICULUM.md](CURRICULUM.md)
- Living draft for comments and edits: https://claude.ai/artifact/Eh8kKJNmELS5QzNJLCi7P4
- Open decisions and next deliverables: [tasks/todo.md](tasks/todo.md)

![Programme roadmap](docs/roadmap.png)

## The weeks

Click a week for its topics in learning order, the day-by-day task checklist, the done-when criteria and the learning resources.

| Week | Days | Theme | Ships by Friday |
| --- | --- | --- | --- |
| [Week 1](weeks/week-01-linux-and-the-shell.md) | 1 to 7 | Linux and the shell | The app as systemd services on a server, backed up nightly |
| [Week 2](weeks/week-02-networking-and-git.md) | 8 to 14 | Networking, Git and how the web works | Nginx, a real domain, HTTPS, configs in Git |
| [Week 3](weeks/week-03-containers-with-docker.md) | 15 to 21 | Containers with Docker | One-command Compose stack, small non-root scanned images |
| [Week 4](weeks/week-04-ci-cd-with-github-actions.md) | 22 to 28 | CI/CD with GitHub Actions | Merge means deployed, with a timed rollback |
| [Week 5](weeks/week-05-cloud-fundamentals-on-aws.md) | 29 to 35 | Cloud fundamentals on AWS | ALB, private compute, private RDS, roles not keys |
| [Week 6](weeks/week-06-infrastructure-as-code-with-terraform.md) | 36 to 42 | Infrastructure as code with Terraform | The environment recreated from zero by terraform apply |
| [Week 7](weeks/week-07-kubernetes-core.md) | 43 to 49 | Kubernetes core | The app on a cluster, surviving induced failures |
| [Week 8](weeks/week-08-kubernetes-in-production-and-the-day-60-gate.md) | 50 to 60 | Kubernetes in production, then the hiring gate | Pipeline deploys to a real cluster; the day-60 gate |
| [Week 9](weeks/week-09-observability.md) | 64 to 70 | Observability | Dashboards, alerts that fire, an SLO |
| [Week 10](weeks/week-10-security-and-reliability.md) | 71 to 77 | Security and reliability | External secrets, a blocked CVE, a timed restore, a postmortem |
| [Week 11](weeks/week-11-gitops-and-the-capstone-rebuild.md) | 78 to 84 | GitOps and the capstone rebuild | The platform rebuilt from an empty account in under two hours |
| [Week 12](weeks/week-12-interview-sprint-and-the-final-gate.md) | 85 to 90 | Interview sprint, then the final gate | System design, break-fix, capstone defence |

Day 61 is an applications day and days 62 and 63 are off, so week 9 starts on a Monday.

## How a week runs

Monday to Thursday: one lesson a day, a 40-minute concept session (what, why, how it breaks) then a three-hour lab on the sample app. Friday: the project against the week's done-when criteria, the induced failures, then the oral drill: fifteen short questions, 60 seconds each, editor closed. Weekend: catch-up, the ai-log, and a one-page summary that becomes revision material for the gates.

The AI licence is printed on every week: Red (weeks 1 to 4) means AI explains and quizzes only; Yellow (weeks 5 to 8) means it may scaffold boilerplate; Green (weeks 9 to 12) means it may implement from your written spec while you review and own every line. Both gates run with the tools off.
