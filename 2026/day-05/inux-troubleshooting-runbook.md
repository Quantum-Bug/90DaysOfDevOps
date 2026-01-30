# Linux Troubleshooting Runbook
## Target Service
**Service:** ssh  
**Reason:** Critical access service, easy to validate health

---

## 1. Environment Basics

### Command 1
```bash
uname -a
```
Observation:

- Kernel version and architecture identified
- Confirms OS-level context before troubleshooting

### Command 2
```bash
cat /etc/os-release
```
Observation:

- Ubuntu-based system
- Useful for knowing log paths and service behavior

## 2. Filesystem Sanity Check

### Command 3

```bash
mkdir /tmp/runbook-demo
```
Observation:

- Directory creation successful
- Confirms filesystem is writable

### Command 4

```bash
cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
```
Observation:

- File copy succeeded
- No permission or disk errors

## 3. CPU & Memory Snapshot

### Command 5
```bash
top
```

Observation:

- SSH process using negligible CPU
- No abnormal load spikes observed

### Command 6
```bash
free -sh
```
Observation:

- Memory usage within normal range
- No swap pressure detected

## 4. Disk & IO Snapshot

### Command 7

```bash
df -h
```

Observation:

- Root filesystem below 70% usage
- No immediate disk space risk

### Command 8
```bash
du -sh /var/log
```

Observation:
- Logs consuming moderate space
- No runaway log growth

## 5. Network Snapshot
### Command 9
```bash
ss -tulpn | grep ssh
```

Observation:
- SSH listening on port 22
- Confirms service is bound to network

### Command 10
```bash
ping -c 3 8.8.8.8
```

Observation:
- Network connectivity healthy
- No packet loss observed

## 6. Logs Reviewed
### Command 11
```bash
journalctl -u ssh -n 50
```

Observation:

- No recent errors or warnings
- Normal authentication messages only

### Command 12
```bash
tail -n 50 /var/log/auth.log
```

Observation:

- Successful login attempts visible
- No repeated failures or suspicious activity

## 7. Quick Findings

- SSH service healthy and responsive
- System resources within normal limits
- No errors found in recent logs
- No immediate action required

## 8. If This Worsens (Next Steps)

1. Restart SSH safely:

```bash
systemctl restart ssh
```
2. Increase log verbosity for deeper inspection
3. Check for brute-force attempts and enable rate limiting