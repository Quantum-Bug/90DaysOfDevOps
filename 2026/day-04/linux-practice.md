# Linux Practice – Processes and Services

## 1. Process Checks

### Command 1: List running processes
`bash`
  
`ps aux | head`

Observation:

- Shows all running processes
- Includes PID, CPU, memory usage, and command name

![image](/2026/day-04/images/aux.png)

### Command 2: Real-time process monitoring
`top`

Observation:

- Identified processes using highest CPU
- Useful during performance issues

![image](/2026/day-04/images/top.png)

## 2. Service Checks (systemd)
### Selected Service: ssh
### Command 3: Check service status

`systemctl status ssh`

Observation:

- Service is active and running
- Shows main PID and recent logs
- Confirms SSH is enabled at boot

![image](/2026/day-04/images/status_ssh.png)

### Command 4: List running services

`systemctl list-units --type=service --state=running`

Observation:

- Displays all active services
- Helps identify what is currently running on the system

![image](/2026//day-04/images/systemctl_running.png)

### Command 5: View service logs
`journalctl -u ssh -n 20`

Observation:

- Shows last 20 log entries for SSH service
- Useful for debugging login or connection issues

### Command 6: Monitor system logs

`tail -n 50 /var/log/syslog`

Observation:

- Displays recent system activity
- Helpful for catching errors or warnings

![image](/2026/day-04/images/tail.png)

## Mini Troubleshooting Flow (Example)

**Scenario:** SSH connection feels slow

Steps followed:

1. Checked SSH service status using `systemctl status ssh`

2. Viewed recent SSH logs using `journalctl -u ssh`

3. Monitored system load using `top`

**Result:**

SSH service was healthy

No errors in logs

System load was normal

# Key Takeaways

- `ps` and `top` help understand process behavior

- `systemctl status` is the first command to check services

- Logs give context before restarting anything