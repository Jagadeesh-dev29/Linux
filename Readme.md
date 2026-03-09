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

Permission Management means controlling who can access what in a system and what actions they can perform.

It is very important in Linux, DevOps, and servers to keep systems secure.

1. What is Permission Management?

Permission management defines:

Who can access a file

What they can do with that file

Example actions:

Read

Write

Execute

2. Types of Permissions in Linux
Permission	Symbol	Meaning
Read	r	View file content
Write	w	Modify or edit file
Execute	x	Run file as program

Example:

-rwxr-xr--

Meaning:

Owner → read, write, execute

Group → read, execute

Others → read only

3. Three Levels of Users
Level	Meaning
Owner	Person who created the file
Group	Team or group of users
Others	All remaining users

Example:

rwx   r-x   r--
Owner Group Others
4. Important Linux Commands
Check Permissions
ls -l

Example output:

-rw-r--r-- 1 user team file.txt
Change Permissions
chmod

Example:

chmod 755 file.sh

Meaning:

Number	Permission
7	rwx
5	r-x
4	r--
Change File Owner
chown user file.txt
Change Group
chgrp devteam file.txt
5. Example (Real DevOps Scenario)

Suppose you have a deployment script:

deploy.sh

You want:

DevOps team → run script

Others → no access

Command:

chmod 750 deploy.sh

Meaning:

Owner → rwx

Group → r-x

Others → no permission

This protects production servers.

6. Why Permission Management is Important

Security

Prevent unauthorized access.

Control

Only specific users modify files.

System Stability

Avoid accidental changes.

DevOps Usage

Manage server access

Secure deployment scripts

Control application logs

✅ Short definition (Interview Answer):

Permission management is a system that controls which users can access files and what actions they can perform, such as read, write, or execute. In Linux it is managed using owner, group, and others permissions with commands like chmod, chown, and chgrp.

If you want, I can also explain Permission Management in Linux in 30-second interview format (very useful for DevOps interviews).

give examples after they chnging

Here are simple examples of permission management before and after changing permissions.

1️⃣ Example: Changing File Permission
Before changing
ls -l file.txt

Output:

-rw-r--r-- 1 jagadeesh dev 0 Mar 9 file.txt

Meaning:

User	Permission	Explanation
Owner	rw-	Read, Write
Group	r--	Read only
Others	r--	Read only
Change Permission
chmod 777 file.txt
After changing
-rwxrwxrwx 1 jagadeesh dev 0 Mar 9 file.txt

Meaning:

Owner → read, write, execute

Group → read, write, execute

Others → read, write, execute

Everyone can access the file.

2️⃣ Example: Script Execution Permission
Before
-rw-r--r-- 1 jagadeesh dev deploy.sh

If you try to run:

./deploy.sh

Error:

Permission denied
Change Permission
chmod +x deploy.sh
After
-rwxr-xr-x 1 jagadeesh dev deploy.sh

Now it works:

./deploy.sh

Script executes successfully.

3️⃣ Example: Restricting Access
Before
-rwxrwxrwx 1 jagadeesh dev data.txt

Everyone can access.

Change Permission
chmod 700 data.txt
After
-rwx------ 1 jagadeesh dev data.txt

Meaning:

Owner → full access

Group → no access

Others → no access

More secure.

4️⃣ Example: Changing Owner
Before
-rw-r--r-- 1 jagadeesh dev file.txt
Command
chown ubuntu file.txt
After
-rw-r--r-- 1 ubuntu dev file.txt

Owner changed from jagadeesh → ubuntu.

✅ Simple interview line:

In Linux, permissions can be modified using chmod, ownership can be changed using chown, and group can be modified using chgrp. These commands help control access and secure system files.

If you want, I can also show real DevOps examples (logs, deployment files, application folders) — these are commonly asked in interviews.

gropu change

Changing Group in Linux means assigning a file or directory to a different group so that users in that group can access it.

This is done using the chgrp or chown command.

1️⃣ Example: Check Current Group
ls -l file.txt

Output:

-rw-r--r-- 1 jagadeesh dev file.txt

Meaning:

Owner → jagadeesh

Group → dev

2️⃣ Change Group using chgrp

Command:

chgrp testing file.txt
After Changing
ls -l file.txt

Output:

-rw-r--r-- 1 jagadeesh testing file.txt

Now the group changed from dev → testing.

Users in the testing group can access the file.

3️⃣ Change Group using chown

You can also change group like this:

chown jagadeesh:testing file.txt

Output:

-rw-r--r-- 1 jagadeesh testing file.txt
4️⃣ Real Example (DevOps)

Suppose a log file:

app.log

Before:

-rw-r--r-- 1 root root app.log

Change group for developers team:

chgrp developers app.log

After:

-rw-rr--r-- 1 root developers app.log

Now developers group can access the logs.

✅ Simple definition:

Group change in Linux means assigning a file or directory to a different group using chgrp or chown, so that users in that group can access it.

If you want, I can also explain User + Group + Permission management together with one real example (very easy concept used in DevOps and interviews).

give full notes on this topis

Here are clear and simple full notes on Permission Management in Linux (good for DevOps basics and interviews).

Permission Management in Linux – Full Notes
1. What is Permission Management?

Permission management means controlling who can access files and what actions they can perform in a Linux system.

It helps to:

Protect system files

Prevent unauthorized access

Manage user access in servers

Example:
A developer should read logs, but should not delete them.

2. Types of Permissions

Linux has 3 basic permissions.

Permission	Symbol	Meaning
Read	r	View file contents
Write	w	Modify or edit file
Execute	x	Run file as program

Example:

rwx

Meaning:

Read

Write

Execute

3. Types of Users

Linux permissions are divided into three user categories.

Category	Meaning
Owner	Person who created the file
Group	Team or group of users
Others	All remaining users

Example permission:

rwx r-x r--
Section	Meaning
rwx	Owner permissions
r-x	Group permissions
r--	Others permissions
4. Viewing File Permissions

Command:

ls -l

Example output:

-rw-r--r-- 1 jagadeesh dev file.txt

Explanation:

Part	Meaning

| File type |
rw- | Owner permission |
r-- | Group permission |
r-- | Others permission |
jagadeesh | Owner |
dev | Group |
file.txt | File name |

5. Changing Permissions

Command used:

chmod

There are two methods.

Method 1: Symbolic Method

Example:

chmod +x file.sh

Meaning:
Add execute permission.

Example:

chmod u+x file.sh
Symbol	Meaning
u	User
g	Group
o	Others
a	All

Examples:

chmod g+w file.txt
chmod o-r file.txt
chmod u+x script.sh
Method 2: Numeric Method

Each permission has a number.

Permission	Value
Read	4
Write	2
Execute	1

Add numbers together.

Value	Meaning
7	rwx
6	rw-
5	r-x
4	r--

Example:

chmod 755 file.sh

Meaning:

User	Permission
Owner	rwx
Group	r-x
Others	r-x
6. Changing File Owner

Command:

chown

Example:

chown ubuntu file.txt

Before:

-rw-r--r-- 1 jagadeesh dev file.txt

After:

-rw-r--r-- 1 ubuntu dev file.txt

Owner changed from jagadeesh → ubuntu.

7. Changing Group

Command:

chgrp

Example:

chgrp developers file.txt

Before:

-rw-r--r-- 1 jagadeesh dev file.txt

After:

-rw-r--r-- 1 jagadeesh developers file.txt

Group changed.

8. Important Permission Numbers
Number	Meaning
777	Everyone full access
755	Owner full, others read & execute
700	Only owner access
644	Owner read/write, others read

Example:

chmod 644 file.txt
9. Directory Permissions

Permissions work slightly differently for directories.

Permission	Meaning
Read	List files
Write	Add or delete files
Execute	Enter directory

Example:

chmod 755 project/
10. Real DevOps Example

Application directory:

/var/www/app

Owner:

deploy

Group:

developers

Command:

chown deploy:developers /var/www/app
chmod 755 /var/www/app

Meaning:

deploy → full access

developers → read & execute

others → read only

This protects application files.

11. Why Permission Management is Important

Security

Prevent unauthorized changes

Protect system files

Manage team access

Secure production servers

12. Simple Interview Answer

What is Permission Management in Linux?

Permission management is a mechanism in Linux that controls who can access files and what actions they can perform, such as read, write, or execute. It is managed using owner, group, and others permissions with commands like chmod, chown, and chgrp.

Service Management (Linux)
1. What is a Service?

A service is a program that runs in the background and helps the system or applications work.

Examples:

SSH → remote login

Nginx → web server

Docker → container service

2. What is Service Management?

Service management means starting, stopping, restarting, and checking services in Linux.

It helps keep applications running properly.

3. Command Used

Linux uses:

systemctl

This command manages services.

4. Important Commands
Start Service
systemctl start nginx

Starts the service.

Stop Service
systemctl stop nginx

Stops the service.

Restart Service
systemctl restart nginx

Restarts the service.

Check Service Status
systemctl status nginx

Shows if service is running or stopped.

5. Enable Service at Boot
systemctl enable nginx

Service starts automatically when system boots.

6. Disable Service
systemctl disable nginx

Service will not start at boot.

7. Example

Check SSH service:

systemctl status ssh

Restart SSH service:

systemctl restart ssh

✅ Short Interview Answer

Service management in Linux means controlling background services using commands like systemctl to start, stop, restart, enable, or check services.