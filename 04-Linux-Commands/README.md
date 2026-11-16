# Module 04: Linux Commands

## Learning Objectives

By completing this module, you will understand:

- Linux command syntax and structure.
- Navigation and directory management.
- File creation, copying, moving and deletion.
- File viewing and text processing.
- File searching.
- System information commands.
- Pipes and input/output redirection.
- Command chaining and operators.
- Practical commands used by DevOps engineers.

---

## 1. Understanding Linux Command Syntax

A Linux command generally follows this structure:

```bash
command [options] [arguments]
```

Example:

```bash
ls -l /home
```

Explanation:

- `ls` — command.
- `-l` — option.
- `/home` — argument.

Linux commands are case-sensitive.

For example:

```bash
ls
LS
```

These are not equivalent commands.

---

## 2. Navigation Commands

### pwd — Print Working Directory

Displays the current working directory.

```bash
pwd
```

### ls — List Directory Contents

```bash
ls
ls -l
ls -a
ls -lh
ls -ltr
ls -R
```

Options:

- `-l` — detailed listing.
- `-a` — include hidden files.
- `-h` — human-readable file sizes.
- `-t` — sort by modification time.
- `-r` — reverse sorting.
- `-R` — recursive listing.

### cd — Change Directory

```bash
cd /etc
cd /home
cd ..
cd ~
cd -
```

Important:

- `..` — parent directory.
- `.` — current directory.
- `~` — home directory.
- `-` — previous working directory.

---

## 3. File and Directory Management

### mkdir — Create Directory

```bash
mkdir projects
mkdir -p projects/devops/linux
```

### touch — Create Empty File

```bash
touch file.txt
touch app.log
```

### cp — Copy Files

```bash
cp file.txt backup.txt
cp -r projects projects_backup
```

### mv — Move or Rename Files

```bash
mv file.txt newfile.txt
mv newfile.txt /tmp/
```

### rm — Remove Files and Directories

```bash
rm file.txt
rm -r projects
```

Use `rm -rf` carefully. It can recursively delete files without prompting.

### rmdir — Remove Empty Directory

```bash
rmdir empty_directory
```

---

## 4. Viewing File Contents

### cat

Displays file contents.

```bash
cat file.txt
cat -n file.txt
```

### less

Displays long files page by page.

```bash
less /var/log/syslog
```

Useful shortcuts:

- `q` — quit.
- `Space` — next page.
- `b` — previous page.
- `/keyword` — search.

### head

Displays the beginning of a file.

```bash
head file.txt
head -n 20 file.txt
```

### tail

Displays the end of a file.

```bash
tail file.txt
tail -n 20 file.txt
tail -f app.log
```

`tail -f` is particularly useful for monitoring application logs.

---

## 5. Searching Files and Directories

### find

Searches for files and directories.

```bash
find /home -name "*.txt"
find /var/log -type f
find . -type d
find . -type f -name "*.log"
```

### locate

Searches an indexed file database, when the locate utility and its database are available.

```bash
locate filename.txt
```

### which

Displays the executable path resolved through PATH.

```bash
which python3
which docker
```

### whereis

Locates binary, source and manual files for a command.

```bash
whereis bash
whereis python3
```

---

## 6. Text Searching and Processing

### grep

Searches text using patterns.

```bash
grep "error" app.log
grep -i "error" app.log
grep -n "error" app.log
grep -r "password" ./config
grep -v "success" app.log
```

Options:

- `-i` — ignore case.
- `-n` — show line numbers.
- `-r` — search recursively.
- `-v` — invert match.

Avoid searching for or exposing real passwords and secrets in shared logs.

### sort

Sorts lines.

```bash
sort names.txt
sort -r names.txt
```

### uniq

Removes adjacent duplicate lines.

```bash
sort names.txt | uniq
sort names.txt | uniq -c
```

### wc

Counts lines, words and bytes.

```bash
wc file.txt
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

### cut

Extracts selected fields or characters.

```bash
cut -d: -f1 /etc/passwd
```

### awk

Processes structured text and columns.

```bash
awk '{print $1}' file.txt
awk -F: '{print $1}' /etc/passwd
```

### sed

Performs stream editing.

```bash
sed 's/old/new/g' file.txt
sed -n '1,10p' file.txt
```

---

## 7. System Information Commands

### uname

```bash
uname -a
uname -r
uname -m
```

### hostname

```bash
hostname
hostnamectl
```

### uptime

```bash
uptime
```

### free

```bash
free -h
```

### df

Displays filesystem disk usage.

```bash
df -h
df -Th
```

### du

Displays directory and file space usage.

```bash
du -sh /var/log
du -h --max-depth=1 .
```

### lscpu

```bash
lscpu
```

### lsblk

```bash
lsblk
lsblk -f
```

---

## 8. Input and Output Redirection

Linux uses three standard streams:

| Stream | File Descriptor | Purpose |
|---|---|---|
| stdin | 0 | Standard input |
| stdout | 1 | Standard output |
| stderr | 2 | Standard error |

### Output Redirection

```bash
echo "Linux Junction" > output.txt
```

Overwrites the file.

### Append Output

```bash
echo "DevOps Learning" >> output.txt
```

Appends to the file.

### Redirect Errors

```bash
ls /invalid-path 2> error.log
```

### Redirect Standard Output and Error

```bash
command > output.log 2>&1
```

### Discard Output

```bash
command > /dev/null 2>&1
```

---

## 9. Pipes

A pipe (`|`) sends the standard output of one command to the standard input of another.

Examples:

```bash
ls -l | less
ps aux | grep nginx
cat /etc/passwd | wc -l
```

### Practical Example

Find the number of running processes:

```bash
ps aux | wc -l
```

Find the largest directories in the current location:

```bash
du -sh ./* 2>/dev/null | sort -hr | head
```

---

## 10. Command Chaining

### Semicolon (;)

Runs commands sequentially regardless of previous command success.

```bash
pwd; date; whoami
```

### AND (&&)

Runs the next command only if the previous command succeeds.

```bash
mkdir test && cd test
```

### OR (||)

Runs the next command only if the previous command fails.

```bash
cd /invalid-directory || echo "Directory not found"
```

### Background Execution (&)

Runs a command in the background.

```bash
sleep 100 &
```

---

## 11. File Permissions and Ownership

### chmod

Changes file permissions.

```bash
chmod 755 script.sh
chmod +x script.sh
chmod 644 file.txt
```

### chown

Changes file ownership.

```bash
sudo chown user:user file.txt
```

### stat

Displays detailed file metadata.

```bash
stat file.txt
```

### file

Identifies file type.

```bash
file file.txt
```

---

## 12. Useful DevOps Linux Commands

| Command | DevOps application |
|---|---|
| `grep` | Search application errors in logs |
| `tail -f` | Monitor live logs |
| `find` | Locate configuration files |
| `ps aux` | Inspect running processes |
| `df -h` | Check disk utilization |
| `free -h` | Check memory availability |
| `du -sh` | Identify large directories |
| `curl` | Test HTTP endpoints and APIs |
| `ss -tulnp` | Inspect listening network sockets |
| `systemctl` | Manage Linux services |
| `journalctl` | Inspect system service logs |
| `chmod` | Set file permissions |
| `chown` | Change file ownership |
| `tar` | Archive and extract files |

---

## 13. Hands-on Practical Labs

### Lab 1: Create a directory structure

```bash
mkdir -p ~/linux-lab/{files,logs,scripts,backup}
```

### Lab 2: Create files

```bash
touch ~/linux-lab/files/app.txt
touch ~/linux-lab/logs/app.log
touch ~/linux-lab/scripts/backup.sh
```

### Lab 3: Write data into files

```bash
echo "Linux Learning" > ~/linux-lab/files/app.txt
echo "Application started" > ~/linux-lab/logs/app.log
```

### Lab 4: Copy and move files

```bash
cp ~/linux-lab/files/app.txt ~/linux-lab/backup/
mv ~/linux-lab/backup/app.txt ~/linux-lab/backup/app-backup.txt
```

### Lab 5: Search for files

```bash
find ~/linux-lab -type f
```

### Lab 6: Search for text

```bash
grep "Application" ~/linux-lab/logs/app.log
```

### Lab 7: Count lines and words

```bash
wc ~/linux-lab/files/app.txt
```

### Lab 8: Monitor logs

```bash
tail -f ~/linux-lab/logs/app.log
```

In another terminal, append a new line:

```bash
echo "Application health check successful" >> ~/linux-lab/logs/app.log
```

Stop monitoring with `Ctrl + C`.

### Lab 9: Practice redirection

```bash
ls -l ~/linux-lab > ~/linux-lab/files/directory-list.txt
```

### Lab 10: Inspect disk usage

```bash
du -sh ~/linux-lab
df -h
```

---

## 14. Knowledge Check

1. What is the difference between `pwd` and `ls`?
2. What is the purpose of `mkdir -p`?
3. What is the difference between `cp` and `mv`?
4. What is the difference between `head` and `tail`?
5. What does `grep -i` do?
6. What is the difference between `>` and `>>`?
7. What is a pipe?
8. What is the difference between `&&` and `||`?
9. What is the purpose of `find`?
10. What is the difference between `df` and `du`?
11. What is the purpose of file descriptor 2?
12. How can you monitor a log file continuously?

---

## Additional Learning Resources

- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [GNU Grep](https://www.gnu.org/software/grep/manual/grep.html)
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Linux man-pages](https://www.kernel.org/doc/man-pages/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)

---

**Previous Module:** Linux Installation

**Next Module:** Filesystem and Storage

**Repository:** Linux Junction — Independent Linux Learning Resource
