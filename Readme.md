# 🐧 Linux Commands Guide

This repository contains basic and important Linux commands with explanations.  
Helpful for beginners and DevOps interview preparation.

---

## 📌 System Information

### uname
Get system information.

Example:
uname -a

---

## 📖 Help Commands

### --help
Displays short usage information directly in the terminal.

### man
Opens the full documentation page with detailed explanation.

### Difference Between --help and man

- `--help` → Quick and short information (used for fast checks).
- `man` → Complete documentation with detailed explanation.

---

## 📂 Current Directory

### pwd
Print Working Directory.  
Shows the current location in the system.

---

## 👤 User Symbols

- `$` → Normal user  
- `#` → Root user  

---

## 🔐 Switch to Root

sudo su -

- `sudo` → Run as superuser  
- `su` → Switch user  
- `-` → Load root login environment  

---

# 📁 List Commands (ls)

- `ls` → List directory contents  
- `ls -l` → Long listing format  
- `ls -lt` → Latest modified files  
- `ls -ltr` → Older files  
- `ls -la` → Show hidden files  
- `ls -h` → Human-readable format  

---

# 📄 Touch Command

### touch

- Create empty file  
- Update timestamp  

---

# 📁 Create Directory

- `mkdir foldername` → Create directory  
- `mkdir f1 f2 f3` → Create multiple directories  

### Create Nested Directory

mkdir -p devops/devops1/devops2

`-p` creates parent directories automatically.

---

# 📑 cat Command (Concatenate)

- `cat file.txt` → Display file  
- `cat > file.txt` → Overwrite file content  
- `cat >> file.txt` → Append content  
- `cat file1 file2 > merge.txt` → Merge files  

---

# ⚠️ rm Command (Dangerous)

- `rm file.txt` → Delete file  
- `rm -d folder` → Delete empty folder  
- `rm -r folder` → Delete folder  
- `rm -rf folder` → Force delete folder  
- `rm -ri folder` → Interactive delete (safer)  
- `rm -rf /` → ❌ Very dangerous  

---

# 📋 Copy Command (cp)

- `cp source destination` → Copy file  
- `cp -rp source destination` → Copy directory with permissions  

---

# 🔄 Move / Rename Command (mv)

- `mv source destination` → Move file/folder  
- `mv oldname newname` → Rename file/folder  

---

# 🔍 grep Command

- `grep "word" file.txt` → Search word  
- `grep -i "error" app.log` → Case insensitive  
- `grep -n "error" app.log` → Show line number  
- `grep -c "error" app.log` → Count occurrences  
- `grep -v "info" app.log` → Exclude word  
- `grep -rin "error" .` → Recursive + Ignore case + Line number  
- `grep -w "rm" file.txt` → Match whole word  

---

# 📖 head Command

- `head file.txt` → First 10 lines  
- `head -n 5 file.txt` → First 5 lines  

---

# 📖 tail Command

- `tail file.txt` → Last 10 lines  
- `tail -f app.log` → Live log monitoring  


# VIM Editor

vim editor -> visually improved

vim <file-name> -> open the file
create and open the file

colon mode
===========
:q -> quit
:wq -> save the file
:q! -> dont save any changes, force quit
:set nu -> display numbers
:<line-number> -> cursor goes particular line number
:/<word-to-search> -> top to bottom
:?<word-to-search> -> bottom to top
:<line-number>d -> deletes that line
:%d -> delete everything
:noh -> dont highlight
:<line-number>s/<word-to-find>/replace-word -> replaces first occurence
:<line-number>s/<word-to-find>/replace-word/g -> all occurences
:%s/<word-to-find>/replace-word/g -> all occurences in all lines

Esc Mode
=========
gg -> takes to top of the file
shift+g -> takes us to bottom of the file
u -> undo
ctrl+r -> redo
dd -> deletes the line
yy -> copy the line
p -> paste below that line
shift+p -> paste above that line

# 🔥 USER MANAGEMENT (DevOps Notes – Clean Version)
👤 Basic Concepts
Term	Meaning
User	Individual login account (human/service)
Group	Collection of users (team)
Roles	Position (Admin, Dev, QA etc.)
Permissions	Access rights (Read, Write, Execute)
🔁 CRUD Operations (User Lifecycle)
✅ Create

Create user

Create group

Assign user to group

✅ Update / Modify

Change group

Add/remove secondary groups

Change password

✅ Delete

Remove from groups

Lock account

Delete user

🟢 USER CREATION
useradd <username>

Example:

useradd ramesh

Check user:

id ramesh

View all users:

cat /etc/passwd

View all groups:

cat /etc/group
🟢 IMPORTANT CONCEPT

✔ A Linux user has:

One primary group

Zero or more secondary groups

✔ When you create a user:

A group with same name is created automatically

That becomes primary group

🟢 GROUP MANAGEMENT

Create group:

groupadd devops

Change primary group:

usermod -g devops ramesh

Add secondary group:

usermod -aG testing ramesh

Remove user from group:

gpasswd -d ramesh testing
🟢 PASSWORD MANAGEMENT

Set password:

passwd ramesh
🟢 SSH CONFIGURATION

SSH config file:

/etc/ssh/sshd_config

Check syntax:

sshd -t

By default in EC2:
✔ Key-based authentication enabled
❌ Password login disabled

🟢 SUDO ACCESS

File:

/etc/sudoers

Always edit using:

visudo

Add user to wheel group (RHEL):

usermod -aG wheel ramesh

Remove from group:

gpasswd -d ramesh wheel
🟢 FILE ARCHIVING

Windows zip format:

zip -r file.zip folder

Linux tar format:

Create archive:

tar -cf file.tar.gz folder

Extract:

tar -xf file.tar.gz
🔥 EMPLOYEE EXIT PROCESS (Real DevOps Practice)

When employee leaves:

1️⃣ Lock account immediately
usermod -L ramesh
2️⃣ Remove from all groups
gpasswd -d ramesh devops
3️⃣ Take backup
tar -cf ramesh_backup.tar.gz /home/ramesh
4️⃣ Delete user completely
userdel -r ramesh