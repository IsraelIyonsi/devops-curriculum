# Week 1: Linux and the shell

Days 1 to 7. Red licence: AI explains and quizzes; it writes nothing for you.

Goal: by Friday the sample app runs on a Linux server you set up, survives a reboot, and backs itself up at night.

[Back to the week list](../README.md#the-weeks)

## Learn, in this order

1. What a server is and what an operating system does for a program: processes, memory, files, users
2. The AWS account: root user MFA, an admin user, a budget alarm, how the Free plan credits work
3. Launching a public Ubuntu VM, creating an ssh key pair, first login
4. The shell: prompt, commands and arguments, man pages, tab completion, history
5. The filesystem: /, /etc, /var, /opt, /home, /tmp; absolute and relative paths; ls, cd, pwd, find
6. Users and groups, sudo, creating a service user that cannot log in
7. Permissions and ownership: rwx, chmod, chown, umask; why 600 for keys and 755 for scripts
8. Packages: apt update and install; where binaries and config files land
9. Processes: ps, top and htop, PIDs, signals, kill; what PID 1 is
10. systemd: unit files, enable and start, status, restart policies, ordering and dependencies
11. Logs: journalctl, /var/log, tail -f
12. Ports and sockets: ss -tulpn; what "address already in use" means
13. Environment variables and config files; where a service reads its settings
14. Text tools: cat, less, grep, awk, sed, cut, sort, uniq, wc; pipes and redirection
15. Bash scripting: variables, if, loops, functions, exit codes, set -euo pipefail
16. cron: crontab syntax, logging a job's output, why jobs fail silently
17. Disk and memory: df, du, free; the deleted-file-still-open trap
18. First Python: read a file, parse lines, print a summary (the same log parser as the awk version)

## Tasks

### Day 1 (Mon)
- [ ] Open the AWS account: MFA on root, an admin user, a budget alarm at your limit
- [ ] Launch a public Ubuntu VM (EC2 on credits, or a small VPS); log in with a key
- [ ] Create your own user with sudo; disable password login over ssh; confirm it is refused
- [ ] Write notes/day-01.md: what a process, a file, a user and a permission are, in your own words

### Day 2 (Tue)
- [ ] Install Postgres and the app runtime with apt; find where each put its config and logs
- [ ] Create a service user; place the app under /opt/app with correct ownership and permissions
- [ ] Create the database and run the app once by hand to prove it starts

### Day 3 (Wed)
- [ ] Write systemd units for the API and the worker; enable them on boot
- [ ] Reboot and confirm both come back; read their logs with journalctl
- [ ] Find the API's port with ss; start a second copy on the same port and read the error

### Day 4 (Thu)
- [ ] Write a bash backup script for Postgres with set -euo pipefail and rotation of old files
- [ ] Schedule it with cron; log its output; prove the file appears at the scheduled time
- [ ] Write the log parser twice: once with grep, awk and sort, once in Python

### Day 5 (Fri, project)
- [ ] Assemble: app as services, backup on cron, key-only ssh, firewall open on 22 and 80 only
- [ ] Induced failures, each with a debug log entry (symptom, command, evidence, fix): fill the disk; kill the database process; break permissions on /opt/app; start a process on the app's port
- [ ] Oral drill: 15 questions, 60 seconds each, editor closed

### Weekend
- [ ] ai-log.md for the week; one-page summary of week 1

## Done when
- [ ] The server reboots and the app comes back without a human
- [ ] Password login over ssh is refused
- [ ] The backup file appears on schedule and restores into an empty database
- [ ] You can explain every line of the unit file and the script

## Learning resources (free unless marked)

- The Linux Command Line, William Shotts, free PDF: https://linuxcommand.org/tlcl.php (chapters 1 to 10, 24 to 27)
- Ubuntu Server documentation: https://ubuntu.com/server/docs
- systemd unit files, the manual: https://www.freedesktop.org/software/systemd/man/latest/systemd.unit.html
- explainshell, paste any command and see what each part does: https://explainshell.com
- Bash Guide (Greg's wiki): https://mywiki.wooledge.org/BashGuide
- OverTheWire Bandit, a shell game for practice: https://overthewire.org/wargames/bandit/
- The official Python tutorial, sections 1 to 7: https://docs.python.org/3/tutorial/
- AWS account root user best practices: https://docs.aws.amazon.com/IAM/latest/UserGuide/root-user-best-practices.html
- AWS Free Tier: https://aws.amazon.com/free/
