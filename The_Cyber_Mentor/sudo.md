## 📘 Introduction

In Linux systems, the `sudo` command stands for **"Superuser Do"**, and it allows a permitted user to execute a command as the **root** user (or another user), with elevated privileges.

As an ethical hacker, understanding how privilege escalation works is critical. Gaining `sudo` access is often the end goal of post-exploitation, as it gives full control over the target machine.

---

## 🧠 What is `sudo`?

- `sudo` lets authorized users execute commands as another user (by default, the **root** user)
- Used for **administrative tasks** like installing software, modifying system files, restarting services, or changing user settings

### Syntax:
```bash
sudo [command]
Example -
sudo apt update
sudo rm -rf /var/log
```


> ⚠️ Caution: With great power comes great responsibility — misusing `sudo` can break a system or delete critical files.

---

## 🛡️ Ethical Hacking Relevance

### Why `sudo` Matters:
- **Privilege Escalation**: If you gain access to a low-privilege user, you may attempt to escalate to a user with `sudo` access
- **Persistence**: Attackers use `sudo` to install backdoors or create new users
- **Enumeration**: Discovering users with `sudo` access is a key part of post-exploitation

### Tools & Techniques:
- Use `sudo -l` to list what a user can run with `sudo`:
```bash
sudo -l
```

- Misconfigured sudo permissions can lead to exploitation (GTFOBins, script injection, etc.)
- Tools like **LinPEAS**, **sudoers misconfig checks**, and **GTFOBins** help find `sudo` abuse paths

---

## 🔎 Common Misconfigurations (Privilege Escalation Paths)

| Misconfiguration                       | Exploit Method                                      |
|----------------------------------------|-----------------------------------------------------|
| `sudo` without password (NOPASSWD)     | Allows command execution without authentication     |
| Sudo access to scripts or editors      | Abuse via `nano`, `vim`, `less`, `python`, `bash`   |
| Wildcard execution (`sudo /usr/bin/*`) | Use wildcard to execute unexpected binaries         |
| Unrestricted command execution         | Ex: `sudo python`, `sudo vi` allows shell access    |

---

## ✅ Best Practices (Defense Side)

- Limit `sudo` access only to required users and commands
- Use `NOPASSWD` sparingly (if at all)
- Regularly audit `/etc/sudoers` and use `sudo visudo` to edit safely
- Monitor logs: `/var/log/auth.log` to track sudo usage

---

## 🧠 Concepts related to sudo

- `/etc/sudoers` file and role-based command access
- GTFOBins (https://gtfobins.github.io/) - ways to abuse binaries with sudo
- Sudo privilege escalation (local root exploits, misconfigured commands)
- Linux privilege escalation techniques (manual and scripted)
- Logging and alerting for sudo abuse
- Alternatives like `su` vs `sudo`

---

> 🛠️ **Practice Tip**: Use `sudo -l` on CTF or lab boxes to identify privilege escalation vectors. Look for scripts or binaries you can modify or abuse.

