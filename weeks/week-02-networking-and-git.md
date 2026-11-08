# Week 2: Networking, Git and how the web works

Days 8 to 14. Red licence.

Goal: by Friday the app sits behind Nginx on a real domain with a valid certificate, and every config file lives in Git.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. IP addresses, ports, TCP versus UDP; localhost versus a public address
2. The request path: URL, DNS, TCP handshake, TLS, HTTP request, response
3. The tools: dig, nslookup, curl -v, traceroute, tcpdump basics
4. Private versus public addresses, CIDR notation, subnets, gateways, NAT
5. Firewalls with ufw; the security group idea you will meet in week 5
6. Reverse proxies; layer 4 versus layer 7 load balancing; a minimal Nginx config
7. HTTP status codes by class; 502 versus 504; headers; X-Forwarded-For
8. DNS record types (A, AAAA, CNAME, MX, TXT, NS, SOA); TTL and caching; why no CNAME at the apex
9. TLS: certificates, chains, certificate authorities, SAN and expiry; Let's Encrypt and certbot
10. HTTP to HTTPS redirect, HSTS; openssl s_client; SSL Labs or testssl.sh
11. Git: init, add, commit, log, diff, .gitignore
12. Branches, merge, rebase, conflicts; why you never rebase a shared branch
13. GitHub: remotes, push and pull, pull requests, reviews, protected branches
14. Tags and semver; revert versus reset; recovering with reflog
15. Secrets never go in Git; what to do in the first five minutes after a leak

## Tasks

### Day 1 (Mon)
- [ ] Trace a request to your own server with dig, curl -v and traceroute; capture one handshake with tcpdump
- [ ] Draw the request path from browser to Postgres and write it up in notes/day-08.md

### Day 2 (Tue)
- [ ] Put Nginx in front of the API as a reverse proxy; pass the client IP through
- [ ] Lock ufw to 22, 80 and 443; read the Nginx access and error logs
- [ ] Stop the API and read the 502; make Nginx wait on a slow upstream and read the 504

### Day 3 (Wed)
- [ ] Point a domain (or free subdomain) at the VM; watch the TTL with dig
- [ ] Issue a Let's Encrypt certificate with certbot; redirect HTTP to HTTPS; add HSTS
- [ ] Verify with openssl s_client and SSL Labs; run a renewal dry run

### Day 4 (Thu)
- [ ] Create a repository for the week 1 scripts, unit files and Nginx config, with a .gitignore
- [ ] Branch, open a pull request, review it yourself, merge, tag v0.1.0
- [ ] Delete a commit on purpose and recover it with reflog; resolve a rebase conflict

### Day 5 (Fri, project)
- [ ] README that draws the request path; all configs committed
- [ ] Induced failures with debug log: swap in a staging certificate; stop the API; change DNS with a long TTL and wait; a rebase that conflicts
- [ ] Oral drill

### Weekend
- [ ] ai-log, one-page summary
- [ ] Python: an HTTP health checker that polls the site and exits non-zero on failure

## Done when
- [ ] SSL Labs grade A or testssl.sh clean
- [ ] curl to the HTTP address returns a 301 to HTTPS
- [ ] The renewal dry run succeeds
- [ ] You can draw the request path on a whiteboard, unaided

## Learning resources (free unless marked)

- What happens when you type a URL, the long answer: https://github.com/alex/what-happens-when
- Cloudflare Learning Center, DNS: https://www.cloudflare.com/learning/dns/what-is-dns/
- Cloudflare Learning Center, TLS handshake: https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/
- Nginx beginner's guide: https://nginx.org/en/docs/beginners_guide.html
- Let's Encrypt, getting started: https://letsencrypt.org/getting-started/
- certbot instructions for Nginx on Ubuntu: https://certbot.eff.org
- SSL Labs server test: https://www.ssllabs.com/ssltest/
- Pro Git, chapters 1 to 3 and 7.1 to 7.7: https://git-scm.com/book/en/v2
- Learn Git Branching, interactive: https://learngitbranching.js.org
- GitHub docs, about pull requests: https://docs.github.com/en/pull-requests
