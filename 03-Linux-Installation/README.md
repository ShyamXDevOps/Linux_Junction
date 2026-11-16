# Module 03: Linux Installation

## Learning Objectives

By completing this module, you will understand:

- Different methods of installing Linux.
- Hardware and software requirements.
- BIOS and UEFI firmware.
- Linux boot process.
- GRUB bootloader.
- Disk partitioning.
- Linux filesystem types.
- Swap space.
- Installation using virtual machines.
- Differences between WSL, virtual machines and physical Linux installations.

---

## 1. Linux Installation Methods

Linux can be installed in several ways depending on the environment and requirements.

### 1.1 Physical Machine (Bare Metal)

Linux is installed directly on the computer's physical hardware.

Use cases:
- Production servers.
- Dedicated Linux workstations.
- Enterprise infrastructure.

### 1.2 Virtual Machine

Linux runs inside virtualization software.

Examples:
- Oracle VirtualBox.
- VMware Workstation.
- Hyper-V.
- KVM.

Use cases:
- Learning Linux.
- Testing operating systems.
- Building development environments.
- Practising server administration.

### 1.3 Windows Subsystem for Linux (WSL)

WSL allows Linux distributions to run on Windows without requiring a traditional dual-boot installation.

Common use cases:
- Linux command-line learning.
- Bash scripting.
- Development environments.
- DevOps tools.

### 1.4 Cloud Installation

Linux virtual machines can be provisioned through cloud platforms.

Examples:
- Microsoft Azure.
- Amazon Web Services.
- Google Cloud Platform.

Use cases:
- Web servers.
- Application hosting.
- CI/CD agents.
- Container infrastructure.

---

## 2. Hardware Requirements

Linux hardware requirements depend on the distribution and workload.

Typical requirements for a basic Ubuntu Desktop virtual machine:

| Component | Suggested allocation |
|---|---|
| CPU | 2 virtual CPUs |
| RAM | 4 GB or more |
| Storage | 25 GB or more |
| Installation media | Ubuntu ISO |
| Network | Internet connection |

These are learning-lab suggestions, not universal minimum requirements.

---

## 3. BIOS vs UEFI

BIOS and UEFI are firmware interfaces that initialize hardware and help start the operating system.

### BIOS

BIOS stands for Basic Input/Output System.

Characteristics:
- Legacy firmware interface.
- Commonly uses MBR partitioning.
- Uses a boot sector to locate boot code.
- Has limitations compared with modern UEFI.

### UEFI

UEFI stands for Unified Extensible Firmware Interface.

Characteristics:
- Modern firmware interface.
- Supports GPT partitioning.
- Supports EFI System Partitions.
- Supports Secure Boot.
- Provides more flexible boot management.

| Feature | BIOS | UEFI |
|---|---|---|
| Boot mode | Legacy | Modern |
| Common partition scheme | MBR | GPT |
| EFI System Partition | Not required | Commonly required |
| Secure Boot | Not native | Supported |
| Boot management | Legacy boot code | EFI boot applications |

---

## 4. Linux Boot Process

A simplified Linux boot process:

1. Power-on.
2. BIOS or UEFI initializes hardware.
3. Firmware identifies the boot device.
4. Bootloader starts.
5. Bootloader loads the Linux kernel and initramfs.
6. Kernel initializes hardware and mounts the root filesystem.
7. Initial userspace process starts.
8. systemd starts services and targets.
9. Login environment becomes available.

---

## 5. Understanding GRUB

GRUB stands for GRand Unified Bootloader.

It is commonly used by Linux distributions to load the Linux kernel.

Main responsibilities:

- Display boot menu.
- Select operating systems.
- Load the Linux kernel.
- Pass kernel parameters.
- Support recovery and alternate boot entries.

Useful commands on a Linux system:

```bash
grub-install --version
update-grub
```

Note: Bootloader modification commands require special care. Do not execute `grub-install` or change bootloader configuration on your working system as part of this introductory exercise.

---

## 6. Disk Partitioning

Disk partitioning divides a storage device into logical sections.

Common Linux partitions:

| Partition | Purpose |
|---|---|
| `/` | Root filesystem |
| `/boot` | Boot-related files |
| `/boot/efi` | EFI System Partition mount point |
| `/home` | User data |
| `swap` | Virtual memory support |

A simple Linux installation can use a root filesystem and swap, while other installations may use additional partitions.

### MBR vs GPT

**MBR (Master Boot Record):**
- Legacy partitioning scheme.
- Supports up to four primary partitions.
- Has a practical disk-size limit of approximately 2 TiB with standard 512-byte sectors.

**GPT (GUID Partition Table):**
- Modern partitioning scheme.
- Supports many partitions.
- Supports large storage devices.
- Commonly used with UEFI systems.

---

## 7. Linux Filesystems

A filesystem organizes files and directories on a storage device.

Common Linux filesystem types:

| Filesystem | Description |
|---|---|
| ext4 | Widely used Linux filesystem |
| XFS | High-performance journaling filesystem |
| Btrfs | Copy-on-write filesystem with advanced features |
| FAT32 | Commonly used for compatibility and EFI partitions |
| NTFS | Common Windows filesystem |

Useful commands:

```bash
lsblk -f
df -Th
blkid
findmnt
```

---

## 8. Understanding Swap Space

Swap is storage space used by Linux to support virtual memory.

When physical RAM is under pressure, the kernel may move less frequently used memory pages to swap.

Swap can be configured as:

- Dedicated swap partition.
- Swap file.

Useful commands:

```bash
free -h
swapon --show
cat /proc/swaps
```

---

## 9. Virtual Machine Installation Lab

For learning purposes, use VirtualBox or another virtualization platform.

### Preparation

1. Install a supported virtualization platform.
2. Download an Ubuntu ISO from the official Ubuntu website.
3. Create a new virtual machine.
4. Allocate CPU, RAM and storage.
5. Attach the Ubuntu ISO.
6. Start the virtual machine.
7. Follow the Ubuntu installation wizard.
8. Create a user account.
9. Complete installation and reboot.

Official download:

https://ubuntu.com/download/desktop

VirtualBox:

https://www.virtualbox.org/wiki/Downloads

### Suggested VM configuration

| Setting | Suggested value |
|---|---|
| OS type | Linux |
| Distribution | Ubuntu 64-bit |
| CPU | 2 |
| RAM | 4 GB |
| Disk | 30 GB |
| Network | NAT |

Adjust resources according to your host computer's capacity.

---

## 10. Post-Installation Configuration

After installing Ubuntu, perform basic system checks.

### Update package metadata

```bash
sudo apt update
```

### Upgrade installed packages

```bash
sudo apt upgrade
```

### Check distribution

```bash
cat /etc/os-release
```

### Check kernel

```bash
uname -r
```

### Check storage

```bash
df -h
lsblk
```

### Check memory

```bash
free -h
```

### Check running services

```bash
systemctl --type=service
```

---

## 11. WSL vs Virtual Machine vs Bare Metal

| Feature | WSL2 | Virtual Machine | Bare Metal |
|---|---|---|---|
| Installation | Windows feature and distro | Virtualization software | Direct hardware installation |
| Hardware access | Integrated and limited | Virtualized hardware | Direct hardware access |
| Isolation | WSL environment | Separate virtual machine | Independent OS installation |
| Resource usage | Generally lightweight | Depends on allocation | Uses physical hardware |
| Best for | Linux development and CLI learning | OS installation and server labs | Dedicated production systems |

---

## 12. Hands-on Exercises

Complete these exercises in your current Ubuntu environment:

1. Identify the current kernel version.
2. Identify the filesystem type of mounted filesystems.
3. List block devices.
4. Check available disk space.
5. Check active swap devices.
6. Identify the init system.
7. Check whether GRUB utilities are installed.
8. Identify the Linux root filesystem mount.
9. Explain the BIOS vs UEFI difference.
10. Draw the Linux boot sequence.

Commands:

```bash
uname -r
lsblk -f
df -Th
swapon --show
ps -p 1 -o pid,comm,args
command -v grub-install
findmnt /
```

Note: WSL2 does not follow the same firmware and bootloader process as a traditional physical or virtual Linux installation. Some installation exercises must be performed inside a separate virtual machine.

---

## 13. Knowledge Check

1. What are the different methods of installing Linux?
2. What is bare-metal installation?
3. What is the difference between BIOS and UEFI?
4. What is GRUB?
5. What is the purpose of initramfs?
6. What is the difference between MBR and GPT?
7. What is a root partition?
8. What is an EFI System Partition?
9. What is swap space?
10. What is the difference between WSL2 and a virtual machine?

---

## Additional Learning Resources

- [Ubuntu Installation Guide](https://ubuntu.com/tutorials/install-ubuntu-desktop)
- [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/)
- [GRUB Manual](https://www.gnu.org/software/grub/manual/grub/)
- [Linux Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- [VirtualBox Documentation](https://www.virtualbox.org/manual/)

---

**Previous Module:** Linux Distributions

**Next Module:** Linux Commands

**Repository:** Linux Junction — Independent Linux Learning Resource
