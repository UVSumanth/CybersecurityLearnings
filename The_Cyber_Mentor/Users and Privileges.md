# 🔐 Linux File Permissions - Ethical Hacking Essentials

## 📘 Introduction

Linux file permissions are crucial in ethical hacking. They define **who can read, write, or execute a file**, and often control whether you can access sensitive data or escalate privileges. Post-exploitation often involves reviewing or abusing misconfigured permissions.

---

## 📂 Understanding Permission Structure

Example from `ls -la`:
> -rwxr-xr-- 1 root root 1234 May 1 14:00 exploit.sh 

### Breakdown:
- `-` → Regular file (`d` for directory)
- `rwx` → Owner permissions (Read, Write, Execute)
- `r-x` → Group permissions
- `r--` → Other (everyone else)

---

## 🛠️ `chmod` - Change File Permissions

### Numeric Mode:
```bash
chmod 755 file.sh
```

| Value | Permission |
|-------|------------|
| 7     | Read, Write, Execute (rwx) |
| 6     | Read, Write (rw-) |
| 5     | Read, Execute (r-x) |
| 4     | Read (r--) |
| 0     | No permissions (---) |

> 🔍 `chmod 777` gives **full access to everyone** — common misconfiguration to look for.

### Symbolic Mode:
```bash
chmod u+x script.sh # Add execute for user
chmod go-w file.txt # Remove write for group and others
chmod a+r file.txt # Add read for all
```

---

## 👤 `chown` - Change File Ownership

Change owner and group of a file:
```bash
chown user:group file
```

Examples:
```bash
chown root:root file.txt
chown john:users report.pdf
```

Use `-R` for recursive ownership:
```bash
chown -R root:root /var/logs
```

---

## 🔓 Ethical Hacking Context

### Misconfigured Permissions to Look For:
| Type | Risk |
|------|------|
| `777` on sensitive files | Anyone can modify/replace the file |
| World-writable scripts   | Replace scripts for privilege escalation |
| Executable by others     | Check what's being run and by whom |
| Cron jobs owned by root but editable by users | Exploitable for root shell |

### Privilege Escalation Opportunities:
- Replace or edit world-writable files executed by root
- Abuse `SUID`/`SGID` files
- Scan with:
```bash
find / -perm -u=s -type f 2>/dev/null # Find SUID binaries
find / -writable -type f 2>/dev/null # Find writable files
```

---

## 🧠 Concepts to Study Later

- `umask` default permissions
- `SUID`, `SGID`, and Sticky Bit
- Directory vs file permissions
- `/etc/sudoers` and file permission risks
- `ACLs` (Access Control Lists) for advanced permission management

---

> 🛠️ **Practice Tip**: In CTFs or compromised systems, always run:
```bash
find / -type f -perm -04000 -ls 2>/dev/null # SUID
find / -type f -perm -02000 -ls 2>/dev/null # SGID
```
These can often be abused to escalate privileges.



