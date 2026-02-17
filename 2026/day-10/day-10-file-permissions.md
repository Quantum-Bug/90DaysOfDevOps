#  Tsk 1 – Create Files

## 1️⃣ Create `devops.txt`

```bash
touch devops.txt
```

---

## 2️⃣ Create `notes.txt` with content

```bash
echo "Linux permissions are powerful" > notes.txt
```

## 3️⃣ Create `script.sh` using vim

```bash
vim script.sh
```

Press `i` → insert mode
Add:

```bash
echo "Hello DevOps"
```

Press `ESC`
Type `:wq` → Enter

---

## 4️⃣ Verify permissions

```bash
ls -l
```

Example output:

```bash
-rw-r--r-- 1 user user    0 devops.txt
-rw-r--r-- 1 user user   28 notes.txt
-rw-r--r-- 1 user user   20 script.sh
```
![image](/2026/day-10/images/verify_permissions.png)

---

# Task 2 – Read Files

## 1️⃣ Read notes.txt

```bash
cat notes.txt
```

---

## 2️⃣ Open script.sh read-only

```bash
vim -R script.sh
```

Exit with:

```
:q
```

---

## 3️⃣ First 5 lines of /etc/passwd

```bash
head -n 5 /etc/passwd
```
---

## 4️⃣ Last 5 lines

```bash
tail -n 5 /etc/passwd
```

![image](/2026/day-10/images/first5.png)

---

# Task 3 – Understand Permissions

Run:

```bash
ls -l devops.txt notes.txt script.sh
```

Example:

```bash
-rw-r--r-- 1 user user  0 devops.txt
-rw-r--r-- 1 user user 28 notes.txt
-rw-r--r-- 1 user user 20 script.sh
```

### Breakdown: `-rw-r--r--`

```
-         → file
rw-       → owner (read, write)
r--       → group (read)
r--       → others (read)
```

### Who can do what?

| File       | Owner       | Group | Others |
| ---------- | ----------- | ----- | ------ |
| devops.txt | Read, Write | Read  | Read   |
| notes.txt  | Read, Write | Read  | Read   |
| script.sh  | Read, Write | Read  | Read   |

⚠ Notice: No execute (`x`) permission yet.

---

# 🔹 Task 4 – Modify Permissions

## 1️⃣ Make script executable

```bash
chmod +x script.sh
```

Verify:

```bash
ls -l script.sh
```

Now should show:

```bash
-rwxr-xr-x
```

Run it:

```bash
./script.sh
```

Output:

```
Hello DevOps
```

![image](/2026/day-10/images/script.png)

---

## 2️⃣ Make devops.txt read-only

Remove write for all:

```bash
chmod a-w devops.txt
```

Check:

```bash
ls -l devops.txt
```

Should show:

```bash
-r--r--r--
```

---

## 3️⃣ Set notes.txt to 640

```bash
chmod 640 notes.txt
```

Meaning:

```
6 = rw-
4 = r--
0 = ---
```

Verify:

```bash
ls -l notes.txt
```

Should show:

```bash
-rw-r-----
```

---

## 4️⃣ Create project directory with 755

```bash
mkdir project
chmod 755 project
```

Check:

```bash
ls -ld project
```

Should show:

```bash
drwxr-xr-x
```

![image](/2026/day-10/images/project.png)

---

# 🔹 Task 5 – Test Permissions

## 1️⃣ Try writing to read-only file

```bash
echo "test" >> devops.txt
```

Expected:

```bash
Permission denied
```

---

## 2️⃣ Remove execute and try running

```bash
chmod -x script.sh
./script.sh
```

Expected:

```bash
Permission denied
```

![image](/2026/day-10/images/error.png)
