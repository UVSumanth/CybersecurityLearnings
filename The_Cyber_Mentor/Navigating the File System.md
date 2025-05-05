## 📘 Introduction

Understanding how to navigate and manipulate the **Linux file system** is foundational for ethical hackers. Most penetration testing environments (Kali Linux, Parrot OS, CTF machines) use Linux-based systems.

Whether you're exploring directories, reviewing logs, or modifying config files after gaining shell access — mastering basic navigation commands is essential.

---

## 🧭 Key File Navigation Commands

### 🔹 `pwd` - Print Working Directory
Displays the full path of your **current directory**.
```bash
pwd
```

### 🔹 `cd` - Change Directory
Moves you between directories.

Examples:
```bash
cd /etc
cd .. # Move up one level
cd / # Go to root directory
cd ~ # Go to home directory
```

### 🔹 `ls` - List Directory Contents
Lists files and directories in your current folder.
```bash
ls # Basic listing
ls -la # Long listing including hidden files (files starting with '.')
```

> 🧑‍💻 Tip: Use `ls -lah` to get human-readable file sizes.

---

## 📂 Directory Management

### 🔹 `mkdir` - Make Directory
Creates a new directory.
```bash
mkdir test_dir
```

### 🔹 `rmdir` - Remove Directory
Deletes an **empty** directory.
```bash
rmdir test_dir
```

> ⚠️ Use `rm -r` to delete non-empty directories (but carefully!)

---

## 📝 File Handling & Viewing

### 🔹 `echo` - Output to Terminal or File
Displays a string or redirects it to a file.
```bash
echo "Hi" # Prints to screen
echo "Hi" > file.txt # Writes to a file (overwrites)
echo "Again" >> file.txt # Appends to the file
```

### 🔹 `cat` - Concatenate and Display File
Shows file contents in terminal.
```bash
cat file.txt
```

> 🔍 Useful for reading flags, credentials, logs, or script contents on compromised systems.

---

## 🔍 Finding Files

### 🔹 `locate <filename>`
Quickly finds where a file is stored.
```bash
locate sshd_config
```

> 🛠️ May require running `sudo updatedb` first.

---

## 🔐 Other Useful Commands

### 🔹 `passwd`
Change the password for the current or another user (if root).
```bash
passwd
```

### 🔹 `man <command>`
Shows the **manual page** for a command.
```bash
man ls
```

### 🔹 `<command> --help`
Quick help for commands.
```bash
ls --help
```

---

## 🌐 Online Helper

### [explainshell.com](https://explainshell.com/)
Paste a command like:
ls -la /etc

It breaks down and explains **each part of the command** — extremely helpful when learning.

---

## 🧠 More Concepts to review on commands on Linux file systems 

- Absolute vs Relative paths
- Wildcards (`*`, `?`) and file globbing
- Redirection (`>`, `>>`, `<`, `2>`, `|`)
- File permissions (`chmod`, `chown`)
- Navigating with `find`, `grep`, `less`, `more`
- Bash scripting basics for automation
- Environment variables (`$PATH`, `$HOME`, etc.)
- Shell escape sequences (used in privilege escalation)

---

> 🛠️ **Practice Tip**: In CTF or lab environments, use `ls -la`, `cat`, and `find` to locate passwords, SSH keys, or sensitive config files. Being quick and confident with Linux navigation speeds up post-exploitation tasks.
