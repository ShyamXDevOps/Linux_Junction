

# Module 05: Linux Filesystem and Storage

## Learning Objectives

By completing this module, you will understand:

- Linux filesystem hierarchy and directory structure.
- Purpose of important Linux directories.
- Absolute and relative paths.
- Files, directories and inodes.
- Hard links and symbolic links.
- Linux filesystem types.
- Disk partitions and storage devices.
- Mounting and unmounting filesystems.
- Disk space and storage monitoring.
- LVM (Logical Volume Management) fundamentals.
- Storage troubleshooting techniques used by DevOps engineers.

---

## 1. Understanding the Linux Filesystem

Linux uses a hierarchical filesystem structure.

All files and directories originate from a single root directory represented by `/`.

Unlike Windows, Linux does not use drive letters such as C: or D: as the root of its directory hierarchy.

Example:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

The Linux Filesystem Hierarchy Standard (FHS) defines the purpose and organization of many standard directories.

Reference: https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html

---

## 2. Important Linux Directories

| Directory | Purpose |
|---|---|
| `/` | Root of the filesystem |
| `/bin` | Essential user command binaries |
| `/boot` | Bootloader and kernel-related files |
| `/dev` | Device files |
| `/etc` | System-wide configuration files |
| `/home` | Regular users' home directories |
| `/lib` | Essential shared libraries |
| `/media` | Mount points for removable media |
| `/mnt` | Temporary mount points |
| `/opt` | Optional third-party application software |
| `/proc` | Virtual filesystem exposing process and kernel information |
| `/root` | Root user's home directory |
| `/run` | Runtime data since system startup |
| `/sbin` | System administration commands |
| `/srv` | Data served by system services |
| `/sys` | Virtual filesystem exposing kernel and device information |
| `/tmp` | Temporary files |
| `/usr` | User applications, libraries and shared resources |
| `/var` | Variable data such as logs, caches and spool files |

### Important directories for DevOps engineers

**`/etc`**

Stores system configuration files.

Examples:

```bash
ls /etc
cat /etc/os-release
cat /etc/hosts
```

**`/var`**

Stores frequently changing data.

Examples:

```bash
ls /var
ls /var/log
du -sh /var/log
```

**`/home`**

Contains regular user home directories.

```bash
ls /home
```

**`/tmp`**

Used for temporary files.

```bash
ls -lah /tmp
```

**`/opt`**

Often used for optional third-party applications.

```bash
ls /opt
```

---

## 3. Absolute Path vs Relative Path

### Absolute Path

An absolute path starts from the root directory `/`.

Example:

```bash
/etc/hosts
/home/user/documents/file.txt
/var/log/syslog
```

### Relative Path

A relative path starts from the current working directory.

Example:

```bash
documents/file.txt
../backup
./script.sh
```

### Special path symbols

| Symbol | Meaning |
|---|---|
| `/` | Root directory |
| `.` | Current directory |
| `..` | Parent directory |
| `~` | Current user's home directory |
| `-` | Previous working directory when used with `cd` |

Useful commands:

```bash
pwd
cd /
cd ..
cd ~
cd -
```

---

## 4. Understanding Files and Directories

Linux treats many system resources as files.

Common file categories include:

| Type | Description |
|---|---|
| Regular file | Text, scripts, binaries and data |
| Directory | Contains directory entries |
| Symbolic link | Reference to another path |
| Character device | Character-oriented device interface |
| Block device | Block-oriented storage device |
| FIFO | Named pipe |
| Socket | Inter-process communication endpoint |

Use `ls -l` to inspect file types and permissions.

```bash
ls -l /
```

The first character in the permissions field indicates the file type.

Examples:

```text
- regular file
d directory
l symbolic link
c character device
b block device
p named pipe
s socket
```

---

## 5. Understanding Inodes

An inode is a filesystem data structure that stores metadata about a file.

An inode typically contains:

- File type and permissions.
- Owner and group information.
- File size.
- Timestamps.
- Link count.
- Pointers or references to file data blocks.

The filename itself is stored in a directory entry that maps the filename to an inode number.

Useful commands:

```bash
ls -i file.txt
stat file.txt
df -i
```

### Important concept

A file's inode number identifies the file within a particular filesystem.

Different filesystems can have the same inode number.

---

## 6. Hard Links vs Symbolic Links

### Hard Link

A hard link creates another directory entry referencing the same inode.

Example:

```bash
echo "Linux Learning" > original.txt

ln original.txt hardlink.txt

ls -li original.txt hardlink.txt
```

Both filenames should display the same inode number.

### Symbolic Link

A symbolic link stores a path reference to another file or directory.

Example:

```bash
ln -s original.txt symlink.txt

ls -l symlink.txt
```

### Comparison

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Inode | Same inode | Different inode |
| References | Inode | Pathname |
| Cross-filesystem | Not supported | Supported |
| Directory links | Generally not allowed for users | Supported |
| Original file removed | Data remains while another hard link exists | Link may become broken |

### Practical exercise

```bash
mkdir link-lab
cd link-lab

echo "Testing Linux links" > original.txt

ln original.txt hardlink.txt

ln -s original.txt symlink.txt

ls -li
```

Inspect the links:

```bash
stat original.txt
stat hardlink.txt
stat symlink.txt
```

---

## 7. Linux Storage Devices

Linux represents storage devices through device files, commonly under `/dev`.

Examples:

| Device | Description |
|---|---|
| `/dev/sda` | Common SATA/SCSI disk naming |
| `/dev/sdb` | Another SATA/SCSI disk |
| `/dev/nvme0n1` | NVMe storage device |
| `/dev/sda1` | First partition of `/dev/sda` |
| `/dev/loop0` | Loop device |

Device names depend on the hardware and storage configuration.

Useful commands:

```bash
lsblk
lsblk -f
sudo fdisk -l
sudo blkid
```

---

## 8. Disk Partitions

Partitioning divides a physical storage device into logical sections.

Common partition table formats:

### MBR

Master Boot Record.

- Legacy partition table.
- Supports up to four primary partitions.
- Has a practical 2 TiB disk-size limit with standard 512-byte sectors.

### GPT

GUID Partition Table.

- Modern partition table.
- Supports large storage devices.
- Supports many partitions.
- Commonly used with UEFI systems.

Useful commands:

```bash
lsblk
sudo fdisk -l
```

Do not create, delete or format partitions on your working WSL system during this exercise.

---

## 9. Linux Filesystem Types

A filesystem defines how files and directories are stored and managed.

Common filesystem types:

| Filesystem | Description |
|---|---|
| ext4 | Widely used Linux journaling filesystem |
| XFS | High-performance journaling filesystem |
| Btrfs | Copy-on-write filesystem with advanced features |
| FAT32 | Common compatibility filesystem |
| NTFS | Common Windows filesystem |
| ZFS | Advanced storage and filesystem platform |

### Check filesystem types

```bash
df -Th
lsblk -f
findmnt
```

---

## 10. Mounting and Unmounting Filesystems

Mounting makes a filesystem accessible through a directory called a mount point.

Example:

```bash
findmnt
mount
```

### Mount command syntax

```bash
sudo mount DEVICE MOUNT_POINT
```

Example for a separate lab disk:

```bash
sudo mount /dev/sdb1 /mnt/data
```

This is an example only. Do not run it unless the device and filesystem have been verified.

### Unmount command

```bash
sudo umount /mnt/data
```

### Check mounted filesystems

```bash
findmnt
mount | column -t
df -h
```

---

## 11. Disk Space Monitoring

Disk monitoring is important for Linux server administration.

### df — Disk Filesystem Usage

Displays available and used filesystem space.

```bash
df -h
df -Th
df -i
```

Options:

- `-h`: Human-readable sizes.
- `-T`: Display filesystem type.
- `-i`: Display inode usage.

### du — Directory Usage

Displays file and directory space usage.

```bash
du -sh /var/log
du -sh /home
du -h --max-depth=1 /var
```

### lsblk — Block Devices

Displays block devices and partitions.

```bash
lsblk
lsblk -f
```

### ncdu — Interactive Disk Usage

If installed, `ncdu` provides an interactive way to explore disk usage.

```bash
ncdu /
```

---

## 12. LVM Fundamentals

LVM stands for Logical Volume Management.

It provides flexible storage management in Linux.

LVM components:

1. Physical Volume (PV)
2. Volume Group (VG)
3. Logical Volume (LV)

### LVM architecture

```text
Physical Disks
      |
      v
Physical Volumes (PV)
      |
      v
Volume Group (VG)
      |
      v
Logical Volumes (LV)
      |
      v
Filesystem
      |
      v
Mount Point
```

### Common LVM commands

```bash
pvs
vgs
lvs
pvdisplay
vgdisplay
lvdisplay
```

These commands inspect LVM configuration.

LVM is commonly used in enterprise Linux environments to manage storage flexibly.

Do not run commands that initialize or modify physical volumes or logical volumes on your existing system as part of this introductory lab.

---

## 13. Swap Space

Swap is storage used to support virtual memory.

It can be configured using:

- Dedicated swap partition.
- Swap file.

Useful commands:

```bash
free -h
swapon --show
cat /proc/swaps
```

---

## 14. Storage Troubleshooting for DevOps

Common storage problems:

### Problem 1: Disk is full

Check:

```bash
df -h
```

Find large directories:

```bash
sudo du -h --max-depth=1 /var | sort -hr
```

### Problem 2: Inodes exhausted

Check:

```bash
df -i
```

### Problem 3: Large log files

Check:

```bash
sudo du -sh /var/log/*
```

### Problem 4: Find large files

```bash
sudo find /var -type f -size +100M -ls
```

### Problem 5: Identify mounted storage

```bash
findmnt
lsblk -f
```

Never delete production logs, application data or system files without understanding their purpose and retention requirements.

---

## 15. Hands-on Practical Labs

### Lab 1: Explore root directories

```bash
ls /
ls -lah /etc
ls -lah /var
ls -lah /home
ls -lah /tmp
```

### Lab 2: Understand paths

```bash
pwd
cd /
cd /var/log
pwd
cd ~
```

### Lab 3: Create files and directories

```bash
mkdir -p ~/storage-lab/files
touch ~/storage-lab/files/test.txt
echo "Storage practice" > ~/storage-lab/files/test.txt
```

### Lab 4: Inspect inode information

```bash
ls -i ~/storage-lab/files/test.txt
stat ~/storage-lab/files/test.txt
```

### Lab 5: Create hard and symbolic links

```bash
cd ~/storage-lab/files

ln test.txt hardlink.txt
ln -s test.txt symlink.txt

ls -li
```

### Lab 6: Inspect filesystem usage

```bash
df -Th
df -i
du -sh ~/storage-lab
lsblk -f
findmnt
```

### Lab 7: Inspect swap

```bash
free -h
swapon --show
```

---

## 16. Knowledge Check

1. What is the Linux root directory?
2. What is the purpose of `/etc`?
3. What kind of data is stored in `/var`?
4. What is the difference between absolute and relative paths?
5. What is an inode?
6. What is the difference between a hard link and a symbolic link?
7. What is a mount point?
8. What is the difference between MBR and GPT?
9. What is the difference between `df` and `du`?
10. What does `lsblk` display?
11. What are the three major components of LVM?
12. What is swap space?
13. What is inode exhaustion?
14. How would you troubleshoot a Linux server with 100% disk utilization?

---

## Additional Learning Resources

- [Linux Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- [Linux man-pages](https://www.kernel.org/doc/man-pages/)
- [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/)
- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html)

---

**Previous Module:** Linux Commands

**Next Module:** Users, Groups and Permissions

**Repository:** Linux Junction — Independent Linux Learning Resource
