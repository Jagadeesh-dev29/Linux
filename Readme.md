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