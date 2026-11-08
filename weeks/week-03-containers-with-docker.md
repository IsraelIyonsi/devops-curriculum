# Week 3: Containers with Docker

Days 15 to 21. Red licence.

Goal: by Friday the whole stack starts with one command on any machine, and the images are small, non-root and scanned.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. What a container is: an isolated process with namespaces, cgroups and a layered filesystem; container versus VM
2. Installing Docker; docker run, ps, logs, exec, stop, rm; image versus container
3. Registries, tags and digests; pull and push; why a tag can move
4. Dockerfile basics: FROM, WORKDIR, COPY, RUN, ENV, EXPOSE, CMD, ENTRYPOINT
5. Layers and cache ordering; .dockerignore
6. Multi-stage builds; small base images; running as a non-root USER
7. CMD versus ENTRYPOINT; COPY versus ADD
8. Volumes versus bind mounts; where data lives and when it is lost
9. User-defined networks; DNS by service name; publishing ports
10. Configuration at runtime: environment, files, secrets; why nothing secret goes in an image
11. Health checks, restart policies, memory and CPU limits; exit codes 137 and 1
12. Debugging a container that exits at once
13. Compose: services, depends_on with a health condition, profiles, env files
14. Image scanning with Trivy; fixing a critical CVE by changing the base image

## Tasks

### Day 1 (Mon)
- [ ] Run the provided app image; exec into it; list its layers with docker history
- [ ] Look at the namespaces from the host; explain in notes why it is not a VM

### Day 2 (Tue)
- [ ] Write Dockerfiles for the API and the worker; multi-stage; non-root user
- [ ] Shrink the API image to the target for your stack; record before and after sizes
- [ ] Reorder lines to break the cache on purpose, then fix the order

### Day 3 (Wed)
- [ ] Run Postgres with a named volume; connect the API by service name on a user-defined network
- [ ] Add health checks, restart policies and a memory limit; trigger exit 137 and read it

### Day 4 (Thu)
- [ ] Compose file for Nginx, API, worker and Postgres with health-gated startup
- [ ] Scan every image with Trivy; fix one critical finding by changing the base image

### Day 5 (Fri, project)
- [ ] Push images to GHCR tagged with the Git SHA; document the one-command cold start
- [ ] Prove docker compose up works on a clean machine first time; prove data survives down and up
- [ ] Induced failures with debug log: memory limit kills the worker; API before the database; wrong volume path; port conflict; file missing because of .dockerignore
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary
- [ ] Python: a YAML validator that loads the compose file and reports services without a health check

## Done when
- [ ] Cold start works first time on a clean machine
- [ ] API image under the stack's size target
- [ ] Every process runs as non-root
- [ ] You can explain each Dockerfile line and its order

## Learning resources (free unless marked)

- Docker, get started guide: https://docs.docker.com/get-started/
- Dockerfile reference: https://docs.docker.com/reference/dockerfile/
- Building best practices (multi-stage, cache, non-root): https://docs.docker.com/build/building/best-practices/
- Docker Compose docs: https://docs.docker.com/compose/
- Trivy docs: https://trivy.dev/latest/docs/
- Liz Rice, "Containers from scratch" (conference talk, search the title on YouTube): a container built with a few syscalls, the best 40 minutes on what a container is
- Docker Hub official images, read the Postgres image page: https://hub.docker.com/_/postgres
