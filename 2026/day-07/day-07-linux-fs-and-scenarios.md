# Part 1: Linux File System Hierarchy

## / (Root Directory)
- The top-level directory; everything in Linux starts here.
- All filesystems and directories branch from `/`.

```bash
ls -l /
````

### Observed:

* Common directories like `bin`, `etc`, `home`, `var`, `usr`

### I would use this when:

* Understanding overall system structure or mount points

---

## /home

* Contains home directories for normal users.
* Each user stores personal files and configs here.

```bash
ls -l /home
```

### Observed:

* User-specific directories

### I would use this when:

* Checking user files, scripts, or permissions

---

## /root

* Home directory for the root (admin) user.
* Separate from `/home` for security reasons.

```bash
ls -l /root
```

### Observed:

* Root-only configuration files and scripts

### I would use this when:

* Logged in as root and managing system-level tasks

---

## /etc

* Stores system-wide configuration files.
* Most services read their config from here.

```bash
ls -l /etc | head
cat /etc/hostname
```

### Observed:

* Config files for networking, services, hostname

### I would use this when:

* Editing or inspecting service configuration

---

## /var/log

* Contains system and application log files.
* One of the most important directories for DevOps.

```bash
ls -l /var/log
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```

### Observed:

* Logs like `syslog`, `auth.log`, and service logs

### I would use this when:

* Debugging errors, crashes, or incidents

---

## /tmp

* Temporary files used by applications and users.
* Files here may be deleted after reboot.

```bash
ls -l /tmp
```

### Observed:

* Temporary files and folders

### I would use this when:

* Creating test files or short-lived data

---

## /bin

* Essential command binaries needed for system operation.
* Available even in rescue mode.

```bash
ls -l /bin | head
```

### Observed:

* Commands like `ls`, `cp`, `mv`

### I would use this when:

* Running basic commands during system recovery

---

## /usr/bin

* Contains most user-level command binaries.
* Larger set than `/bin`.

```bash
ls -l /usr/bin | head
```

### Observed:

* Common utilities and tools

### I would use this when:

* Understanding where commands are installed

---

## /opt

* Optional or third-party software installations.
* Often used by custom or vendor apps.

```bash
ls -l /opt
```

### Observed:

* Vendor or custom application directories

### I would use this when:

* Managing non-default applications

---

# Part 2: Scenario-Based Practice

## SOLVED EXAMPLE: Checking a Service

**Scenario:**
How do you check if the `nginx` service is running?

**Step 1:**

```bash
systemctl status nginx
```

**Why:**

* Shows whether the service is active, failed, or stopped

**Step 2:**

```bash
systemctl list-units --type=service
```

**Why:**

* Lists available services if nginx is not found

**Step 3:**

```bash
systemctl is-enabled nginx
```

**Why:**

* Checks if the service starts on boot

**What I learned:**

* Always check service status first before taking action.

---

## Scenario 1: Service Not Starting

**Problem:**
`myapp` failed to start after reboot.

**Step 1:**

```bash
systemctl status myapp
```

**Why:**

* Confirms whether the service failed or is inactive

**Step 2:**

```bash
journalctl -u myapp -n 50
```

**Why:**

* Reviews recent logs for error messages

**Step 3:**

```bash
systemctl is-enabled myapp
```

**Why:**

* Verifies if the service is enabled at boot

**Step 4:**

```bash
systemctl restart myapp
```

**Why:**

* Attempts a controlled restart after inspection

---

## Scenario 2: High CPU Usage

**Problem:**
Server feels slow.

**Step 1:**

```bash
top
```

**Why:**

* Live view of CPU usage and top processes

**Step 2:**

```bash
ps aux --sort=-%cpu | head -10
```

**Why:**

* Identifies highest CPU-consuming processes

**Step 3:**

```bash
ps -p <PID> -o pid,ppid,cmd,%cpu,%mem
```

**Why:**

* Gets details of the suspected process

---

## Scenario 3: Finding Service Logs

**Problem:**
Developer asks where Docker logs are.

**Step 1:**

```bash
systemctl status docker
```

**Why:**

* Confirms service name and status

**Step 2:**

```bash
journalctl -u docker -n 50
```

**Why:**

* Views recent service logs

**Step 3:**

```bash
journalctl -u docker -f
```

**Why:**

* Follows logs in real time

---

## Scenario 4: File Permission Issue

**Problem:**
Script `/home/user/backup.sh` shows “Permission denied”.

**Step 1:**

```bash
ls -l /home/user/backup.sh
```

**Why:**

* Checks current permissions

**Step 2:**

```bash
chmod +x /home/user/backup.sh
```

**Why:**

* Adds execute permission

**Step 3:**

```bash
ls -l /home/user/backup.sh
```

**Why:**

* Verifies execute bit is set

**Step 4:**

```bash
./backup.sh
```

**Why:**

* Confirms script runs successfully

---

## Key Takeaways

* Know where configs (`/etc`) and logs (`/var/log`) live
* Always inspect before restarting services
* High CPU issues usually start with `top`
* Permission issues are often due to missing execute (`x`) bit