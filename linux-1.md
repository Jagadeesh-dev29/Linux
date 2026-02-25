Linux Commands

uname – It is a Linux command used to get system information.
Example: uname -a

--help – Printed directly in the terminal. Shows short usage information.
man – Opens the full documentation page with a detailed explanation.

Question: Difference between --help and man

The --help command prints information directly in the terminal. It is quick and simple for debugging. I use --help for quick checks.

The man command provides full documentation of the command with description and author name. I use the man command when I am unsure about a command and need to check its behavior.

pwd – Present Working Directory. It is used to check where we are in the system.

$ – Normal user
# – Root user

sudo su -

sudo – Run as superuser

su – Switch user

- – Load root's login environment

List Commands

ls – List directory contents
ls -l – Long listing
ls -lt – Latest files
ls -ltr – Older files
ls -la – Get hidden (.) files
ls -h – Human-readable format

Touch Command

touch –

Create an empty file

Update timestamp

Make Directory

mkdir <foldername> – Create directory
mkdir <f1> <f2> ... – Create multiple directories

To create a directory inside another directory:
mkdir -p devops/devops1/devops2 – -p automatically creates parent directories

cat (concatenate)

cat devops.txt – Open the file
cat > devops.txt – Add data to the file (overwrites)
cat >> devops.txt – Add data (does not overwrite)
cat file1 file2 file3 > merge.txt – Merge 3 files into merge.txt

rm (dangerous command ⚠️)

rm <filename> – Delete file

rm -d <foldername> – Remove empty folder

rm -r <foldername> – Remove folder

rm -rf <foldername> – Remove folder forcefully

rm -rf / – Very dangerous command

rm -ri <foldername> – Safest way to delete directories; it asks before deleting