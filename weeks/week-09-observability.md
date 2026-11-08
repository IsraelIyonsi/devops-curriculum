# Week 9: Observability

Days 64 to 70. Green licence opens: AI may implement from your written spec; you review every line and own it.

Goal: by Friday you know the app is unhealthy before a user does: dashboards that answer one question each, two alerts that reach a phone, and a written service level objective with an error budget.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. Monitoring versus observability; metrics, logs and traces as three views of one system
2. The four golden signals; RED for services, USE for resources; writing the SLIs for the sample app before installing anything
3. Prometheus: the pull model, scrape targets and service discovery, exporters, labels and cardinality
4. PromQL: rate, sum by, histogram_quantile; why a p95 is not an average
5. kube-prometheus-stack; Grafana; a dashboard that answers one question
6. Structured logs; Loki with Grafana Alloy as the agent (Promtail reached end of life in March 2026); LogQL; correlation IDs
7. OpenTelemetry; distributed tracing; one end-to-end trace in Tempo or Jaeger
8. Alerting: Alertmanager routing; symptom-based alerts; alert fatigue; on-call hygiene
9. Service level objectives, error budgets, burn-rate alerts
10. Runbooks linked from every alert; load testing with k6

## Tasks

### Day 1 (Mon)
- [ ] Write the SLIs for the API and the worker: what to measure, where, and what good looks like
- [ ] Read the app's metrics endpoint and map each metric to a golden signal

### Day 2 (Tue)
- [ ] Install kube-prometheus-stack; find the app's metrics in Prometheus
- [ ] Build a RED dashboard for the API and a saturation dashboard for nodes and pods

### Day 3 (Wed)
- [ ] Loki with Alloy; query the app's errors by correlation ID
- [ ] Enable the app's OpenTelemetry export; follow one request through a trace

### Day 4 (Thu)
- [ ] Two alerts, error rate and p95 latency, routed to your phone through Alertmanager
- [ ] Write the SLO document: 99.5 percent availability, the error budget, the burn-rate alert
- [ ] A runbook for each alert

### Day 5 (Fri, project)
- [ ] A k6 load test that burns budget and trips an alert within two minutes
- [ ] Induced failures with debug log: memory leak toggle; pool exhaustion toggle; a label with a user ID that explodes cardinality; an alert with a broken PromQL expression that never fires
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary

## Done when
- [ ] An induced failure fires an alert within two minutes and the runbook leads to the fix
- [ ] The dashboard answers "is the app healthy right now" in one glance
- [ ] You can explain p95 versus average to a product manager in plain words

## Learning resources (free unless marked)

- Google SRE book, Monitoring distributed systems: https://sre.google/sre-book/monitoring-distributed-systems/
- Google SRE workbook, Implementing SLOs: https://sre.google/workbook/implementing-slos/
- Prometheus overview and first steps: https://prometheus.io/docs/introduction/overview/
- PromQL basics: https://prometheus.io/docs/prometheus/latest/querying/basics/
- kube-prometheus-stack chart: https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack
- Grafana Loki docs: https://grafana.com/docs/loki/latest/
- Grafana Alloy docs: https://grafana.com/docs/alloy/latest/
- OpenTelemetry docs, concepts: https://opentelemetry.io/docs/concepts/
- k6 docs: https://grafana.com/docs/k6/latest/
- Alertmanager configuration: https://prometheus.io/docs/alerting/latest/configuration/
