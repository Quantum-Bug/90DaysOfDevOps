# Part 1: Launch Cloud Instance & SSH Access (15 minutes)

**Step 1: Create a Cloud Instance**
![image](/2026/day-08/images/demo-server.png)

**Step 2: Connect via SSH**
![image](/2026/day-08/images/ssh-connect.png)

---

# Part 2: Install Docker & Nginx (20 minutes)

**Step 1: Update System**
![image](/2026/day-08/images/update.png)

**Step 3: Install Nginx**
![image](/2026/day-08/images/nginx.png)

**Verify Nginx is running:**
![image](/2026/day-08/images/nginx-status.png)
---

# Part 3: Security Group Configuration (10 minutes)

**Test Web Access:**
Open browser and visit: `http://<your-instance-ip>`

You should see the **Nginx welcome page**!

![image](/2026/day-08/images/Welcome-to-nginx-.png)

---

# Part 4: Extract Nginx Logs (15 minutes)

**Step 1: View Nginx Logs**
![image](/2026/day-08/images/nginx-logs.png)

**Step 2: Save Logs to File**

**Step 3: Download Log File to Your Local Machine**
```bash
# On your local machine (new terminal window)
# For AWS:
scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-logs.txt .
```
![image](/2026/day-08/images/verify-accesslogs.png)
---
![image](/2026/day-08/images/backup-logs.png)

## Commands Used
`ssh`

`apt update`

`apt upgrade`

`apt install nginx`

`systemctl status nginx`

`cat`

`tail`

`scp`

## Challenges Faced
- Webpage not accessible initially

- Resolved by opening port 80 in the security group

- Verified Nginx service was running

## What I Learned
- How to launch and access a cloud server

- Installing and managing services remotely

- Importance of security group rules

- Where Nginx logs are stored

- How to extract and download logs from a server


## Why This Matters for DevOps

This exercise teaches you:
- **Cloud infrastructure provisioning** - launching and configuring servers
- **Remote server management** - SSH, security, access control
- **Service deployment** - installing and running applications
- **Log management** - accessing and analyzing logs
- **Security** - configuring firewalls and security groups

These are core skills for any DevOps engineer working in production.

---
