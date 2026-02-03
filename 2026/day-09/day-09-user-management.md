# Objective
Practice Linux user and group management by creating users, groups, assigning permissions, and setting up shared directories.


## Task 1: Create Users

### Users Created
- tokyo
- berlin
- professor

### Commands Used

```bash
sudo useradd -m tokyo
sudo passwd tokyo

sudo useradd -m berlin
sudo passwd berlin

sudo useradd -m professor
sudo passwd professor
```
**Verification** 
```bash
cat /etc/passwd | grep -E "tokyo|berlin|professor"
ls -l /home
```

**Result**

- All users created successfully

- Home directories exist under `/home`

## Task 2: Create Groups
### Groups Created
- developers
- admins

### Commands used 
```bash
sudo groupadd developers
sudo groupadd admins
```

**Verification**
```bash
cat /etc/group | grep -E "developers|admins"
```

## Task 3: Assign Users to Groups
### Group Assignments

- tokyo → developers

- berlin → developers, admins

- professor → admins

### Commands Used
```bash
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
```

**Verification**
```bash
groups tokyo
groups berlin
groups professor
```

**Result:**

- Users assigned to correct groups

## Task 4: Shared Directory for Developers
**Steps Performed**

```bash
sudo mkdir /opt/dev-project
sudo chgrp developers /opt/dev-project
sudo chmod 775 /opt/dev-project
```

**Verification**

```bash
ls -ld /opt/dev-project
```

**Expected output:**

```bash
drwxrwxr-x root developers /opt/dev-project
```

**Testing File Creation**

```bash
sudo -u tokyo touch /opt/dev-project/tokyo.txt
sudo -u berlin touch /opt/dev-project/berlin.txt
ls -l /opt/dev-project
```

**Result:**

- Both users successfully created files

- Group permissions working as expected

## Task 5: Team Workspace Setup
### Step 1: Create User and Group

```bash
sudo useradd -m nairobi
sudo passwd nairobi
sudo groupadd project-team
```

### Step 2: Add Users to Group

```bash
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

### Step 3: Create Shared Directory


```bash
sudo mkdir /opt/team-workspace
sudo chgrp project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
```

**Verification**

```bash
ls -ld /opt/team-workspace
groups nairobi
```

**Test Access**

```bash
sudo -u nairobi touch /opt/team-workspace/nairobi.txt
ls -l /opt/team-workspace
```

**Result:**

- Nairobi successfully created a file

- Group access configured correctly


## Summary

### Users & Groups Created

- **Users:** tokyo, berlin, professor, nairobi

- **Groups:** developers, admins, project-team

### Group Membership

- developers → tokyo, berlin

- admins → berlin, professor

- project-team → tokyo, nairobi

### Directories Created

- `/opt/dev-project` → developers (775)

- `/opt/team-workspace` → project-team (775)

## Commands Used

- `useradd`

- `passwd`

- `groupadd`

- `usermod`

- `groups`

- `mkdir`

- `chgrp`

- `chmod`

- `ls`

- `sudo -u`

## What I Learned

- How to manage users and groups in Linux

- How group permissions enable shared access

- How to safely test permissions using `sudo -u`

- Why correct ownership is critical for collaboration

