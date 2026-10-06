# Block 06 — Linux for Data Center Technicians

## Purpose
For L1, Linux knowledge means being able to use the command line safely, read system state and logs, and understand where an OS problem fits in the larger server stack.

## Basic commands
```bash
whoami
hostname
uname -r
uname -a
pwd
ls -la
lsblk -f
df -h
free -h
ps aux
top
ip addr
ip link
ip route
journalctl -b
dmesg
systemctl status <service>
systemctl is-system-running
```

## SSH
SSH accesses the Linux operating system through the command line. It is different from BMC management.

```text
SSH → Linux / OS
BMC → physical server / hardware management
Remote Console → physical server console
```

## Safety
Understand a command before running it. Reading state is generally safer than changing state. Use approved runbooks and documentation. Do not guess on production systems.

## Honest interview statement
> My professional command-line experience has mainly been in Windows. I have recently started learning Linux and Bash for infrastructure work. I understand the basic concepts and commands, and I am continuing to build this skill.
