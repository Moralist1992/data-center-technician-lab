# Linux Basic Commands

## Identity and system
```bash
whoami
hostname
uname -r
uname -a
```

## Files
```bash
pwd
ls
ls -la
cd /path
```

## Storage
```bash
lsblk
lsblk -f
df -h
```

## Memory and processes
```bash
free -h
ps aux
top
```

## Network
```bash
ip addr
ip link
ip route
```

## Logs
```bash
journalctl -b
journalctl -b -1
dmesg
```

## Services
```bash
systemctl status <service>
systemctl is-system-running
```

## Pager
```bash
journalctl -b | less
```
Press `q` to exit `less`.

The important skill is understanding what information a command provides and why you would use it, not memorizing every option.
