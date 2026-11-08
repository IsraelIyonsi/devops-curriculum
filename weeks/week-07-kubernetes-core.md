# Week 7: Kubernetes core

Days 43 to 49. Yellow licence.

Goal: by Friday the app runs on a local cluster with probes, limits, routing and autoscaling, has survived a rolling update under load, and you have fixed five induced failures using nothing but kubectl output.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. Why orchestration: what a VM and Compose cannot do (scheduling, self-healing, scaling, rolling updates, discovery)
2. Architecture: control plane (API server, etcd, scheduler, controller manager) and nodes (kubelet, kube-proxy, containerd through the CRI, the CNI, CoreDNS); why Kubernetes no longer uses Docker
3. A kind cluster; kubectl get, describe, logs, exec, apply, delete; contexts and namespaces
4. Pods; labels and selectors; what happens when you kubectl apply (authentication, authorisation, admission, etcd, controllers, scheduler, kubelet)
5. ReplicaSets and Deployments; rolling updates and rollbacks
6. Jobs and CronJobs (the backup moves here)
7. Services: ClusterIP, NodePort, LoadBalancer; cluster DNS
8. Ingress (frozen but everywhere) and Gateway API (GatewayClass, Gateway, HTTPRoute); a controller on kind; why the ingress-nginx retirement matters
9. ConfigMaps and Secrets; environment versus mounted files; why a Secret is only base64
10. Probes: liveness, readiness, startup; what each one does when it fails
11. Requests and limits; quality of service classes; OOMKilled
12. The Horizontal Pod Autoscaler and metrics-server; PodDisruptionBudgets
13. Graceful shutdown: SIGTERM, preStop, terminationGracePeriodSeconds
14. Taints and tolerations, node affinity and anti-affinity, DaemonSets
15. StatefulSets, PersistentVolumeClaims, StorageClasses (Postgres on kind)
16. Debugging: CrashLoopBackOff, ImagePullBackOff, Pending, OOMKilled; describe, logs --previous, events

## Tasks

### Day 1 (Mon)
- [ ] Create a kind cluster; tour it with kubectl; find every control plane and node component as a pod or process
- [ ] Apply a single pod and watch it get scheduled; delete it and explain why nothing replaces it

### Day 2 (Tue)
- [ ] Deployments for the API and the worker; roll out a bad image tag; roll back
- [ ] Move the backup to a CronJob

### Day 3 (Wed)
- [ ] Services for the API and Postgres; prove DNS by service name from inside a pod
- [ ] Install a Gateway API controller (Envoy Gateway or Traefik); route the host to the API with TLS
- [ ] ConfigMap and Secret injected; change a value and see what does and does not pick it up

### Day 4 (Thu)
- [ ] Probes, requests and limits on every workload; HPA on the API with metrics-server
- [ ] Graceful shutdown: preStop and a grace period; prove no dropped requests during a rollout
- [ ] Postgres as a StatefulSet with a PersistentVolumeClaim

### Day 5 (Fri, project)
- [ ] kubectl apply from the repository onto a fresh cluster yields a working app
- [ ] Rolling update under a continuous request loop with zero failed requests
- [ ] Five induced failures with a written diagnosis path each: wrong image tag; readiness probe on the wrong path; memory limit below need; Service selector typo; CPU request larger than any node
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary

## Done when
- [ ] Fresh cluster plus apply from the repository equals a working app
- [ ] Zero failed requests during a rollout
- [ ] Each induced failure has symptom, command, evidence and fix written down
- [ ] You can explain the apply path from API server to running container

## Learning resources (free unless marked)

- Kubernetes concepts (read Overview, Workloads, Services and Networking, Configuration): https://kubernetes.io/docs/concepts/
- Kubernetes basics, interactive tutorial: https://kubernetes.io/docs/tutorials/kubernetes-basics/
- kubectl quick reference: https://kubernetes.io/docs/reference/kubectl/quick-reference/
- kind: https://kind.sigs.k8s.io/docs/user/quick-start/
- Gateway API: https://gateway-api.sigs.k8s.io
- Envoy Gateway: https://gateway.envoyproxy.io
- Configure liveness, readiness and startup probes: https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/
- Pod lifecycle and termination: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/
- learnk8s, a visual guide to troubleshooting deployments: https://learnk8s.io/troubleshooting-deployments
- Kubernetes the hard way (optional, for the architecture): https://github.com/kelseyhightower/kubernetes-the-hard-way
