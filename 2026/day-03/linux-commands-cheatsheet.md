# Linux Commands Cheat Sheet – Day 03

## 1. Process Management

- `ps aux` – List all running processes
- `ps -ef` – Full process listing with parent-child info
- `top` – Real-time CPU and memory usage
- `htop` – Interactive process viewer (if installed)
- `uptime` – How long system has been running + load
- `free -m` – Memory usage in MB
- `vmstat` – CPU, memory, and I/O statistics
- `kill <PID>` – Terminate a process by PID
- `kill -9 <PID>` – Force kill a stuck process
- `nice` – Start process with priority
- `renice` – Change priority of running process

---

## 2. File System & Disk

- `ls -lh` – List files with size info
- `pwd` – Show current directory
- `cd` – Change directory
- `du -sh <dir>` – Disk usage of directory
- `df -h` – Disk space usage
- `stat <file>` – Detailed file information
- `find /path -name file` – Search for files
- `chmod` – Change file permissions
- `chown` – Change file ownership
- `mount` – Show mounted file systems

---

## 3. Logs & System Inspection

- `journalctl` – View system logs
- `journalctl -u <service>` – Logs for a service
- `tail -f /var/log/syslog` – Live log monitoring
- `less <file>` – Scroll through large files
- `grep "error" file` – Search text inside files

---

## 4. Networking & Troubleshooting

- `ip addr` – Show network interfaces and IPs
- `ip route` – Display routing table
- `ping <host>` – Check network connectivity
- `curl <url>` – Test HTTP endpoints
- `ss -tuln` – Show listening ports
- `netstat -tuln` – Network connections (older systems)
- `dig <domain>` – DNS lookup
- `traceroute <host>` – Trace network path

---

## 5. Service Management (systemd)

- `systemctl status <service>` – Check service health
- `systemctl start <service>` – Start a service
- `systemctl stop <service>` – Stop a service
- `systemctl restart <service>` – Restart service
- `systemctl enable <service>` – Start service on boot

---

## DevOps Tip
Most production issues start with:
- `top`
- `journalctl`
- `df -h`
- `ip addr`
- `curl`

Master these first.