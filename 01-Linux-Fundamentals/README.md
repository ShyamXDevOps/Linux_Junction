# Module 01: Linux Fundamentals

## Learning Objectives

By completing this module, you will understand:

- The history and evolution of Linux.
- The relationship between Unix, GNU and Linux.
- The Linux open-source philosophy.
- The difference between the Linux kernel and operating system.
- Linux architecture and its major components.
- How Linux handles system resources.
- Essential Linux terminology.
- How Linux boots and starts system services.

---

## 1. History of Unix and Linux

Understanding Linux history helps explain why Linux is designed the way it is.

### 1.1 Unix

Unix is an operating system originally developed at AT&T Bell Labs in the late 1960s and early 1970s.

Important characteristics:

- Multiuser operating system.
- Multitasking capabilities.
- Portable design.
- Hierarchical filesystem.
- Command-line tools and shell environments.

Unix influenced many operating systems, including Linux and BSD.

### 1.2 GNU Project

The GNU Project was started by Richard Stallman in 1983.

Its objective was to develop a completely free Unix-like operating system.

The GNU Project developed many important utilities, including:

- GCC — GNU Compiler Collection.
- GNU Bash — Command-line shell.
- GNU Coreutils — Essential command-line utilities.
- GNU Make — Build automation tool.
- GNU Debugger (GDB) — Debugging tool.

### 1.3 Linux Kernel

In 1991, Linus Torvalds released the first version of the Linux kernel.

The Linux kernel became the foundation for operating systems that combined it with GNU software and other components.

**Important distinction:**

- Linux is the kernel.
- GNU provides many essential system utilities.
- A Linux distribution combines the kernel with user-space software and other components.

---

## 2. Unix vs Linux

| Feature | Unix | Linux |
|---|---|---|
| Origin | Bell Labs | Created by Linus Torvalds |
| Initial development | Late 1960s | 1991 |
| Licensing | Varies by implementation | Open-source kernel |
| Source code | Depends on implementation | Publicly available |
| Distributions | Different Unix variants | Ubuntu, Debian, Fedora, etc. |
| Usage | Enterprise systems and servers | Servers, cloud, desktops and embedded systems |

Examples of Unix systems and Unix-like systems:

- AIX
- HP-UX
- Solaris
- FreeBSD
- Linux

Note: FreeBSD is a Unix-like operating system, while Linux is a Unix-like kernel. They are not the same implementation of Unix.

---

## 3. Open-Source Philosophy

Open-source software makes its source code available under a license that permits activities such as studying, modifying and redistributing the software, subject to that license.

### Key concepts

**Source Code:** Human-readable instructions used to build software.

**Open Source:** Software distributed under a license that provides defined rights to access and work with its source code.

**Free Software:** A philosophy emphasizing users' freedom to run, study, modify and share software.

**Community Development:** Contributors collaborate to improve software, fix bugs and develop new features.

### Benefits of Open Source

1. Transparency.
2. Collaboration.
3. Flexibility and customization.
4. Community support.
5. Reduced vendor lock-in.
6. Faster innovation through shared development.

### Common Open-Source Licenses

| License | Key characteristic |
|---|---|
| GPL | Copyleft license |
| MIT | Permissive license |
| Apache 2.0 | Permissive license with express patent provisions |
| BSD | Permissive license family |

---

## 4. Linux Kernel Architecture

The Linux kernel is the core component responsible for managing system resources and providing essential services to applications.

### Major kernel responsibilities

**4.1 Process Management**

- Creates and terminates processes.
- Schedules CPU time.
- Manages process states.
- Supports multitasking.

**4.2 Memory Management**

- Allocates and releases memory.
- Manages virtual memory.
- Handles memory protection.
- Supports paging and swapping.

**4.3 Device Management**

- Communicates with hardware through device drivers.
- Manages device access.
- Supports storage, networking and input/output devices.

**4.4 Filesystem Management**

- Provides filesystem interfaces.
- Manages files and directories.
- Supports multiple filesystem types.

**4.5 Networking**

- Implements networking protocols.
- Manages network interfaces.
- Handles packet transmission and reception.

---

## 5. Linux System Components

A Linux operating system environment includes several layers:

| Component | Responsibility |
|---|---|
| Hardware | CPU, RAM, disk and network devices |
| Kernel | Manages hardware and system resources |
| System Libraries | Provide APIs for programs |
| Shell | Provides a command-line interface |
| System Utilities | Provide administration tools |
| Applications | Perform user and business tasks |

### Important terminology

**Kernel:** Core of the operating system.

**Shell:** Command interpreter, such as Bash.

**Terminal:** Interface through which users interact with a shell.

**Process:** An instance of a running program.

**Daemon:** A background service process.

**Filesystem:** Method used to organize and store files.

**Root User:** Administrative user with UID 0.

**Root Directory:** Top-level directory represented by `/`.

**Repository:** A location from which software packages can be downloaded and installed.

---

## 6. Linux Kernel Space vs User Space

Linux separates privileged kernel operations from ordinary application execution.

### Kernel Space

- Executes kernel code.
- Has privileged access to system resources.
- Manages hardware and system operations.
- Handles system calls.

### User Space

- Runs applications and user processes.
- Provides restricted access to hardware.
- Uses system calls to request kernel services.

### Example

When an application reads a file:

1. The application requests file access.
2. A library or application invokes a system call.
3. The kernel handles the request.
4. The filesystem and storage subsystem access the required data.
5. The result is returned to the application.

---

## 7. Linux Boot Process

A simplified Linux boot sequence:

1. BIOS or UEFI initializes the system.
2. Bootloader loads the Linux kernel.
3. Kernel initializes memory and hardware.
4. Kernel starts the initial userspace process.
5. The init system starts services and targets.
6. The system becomes ready for user login.

On modern Ubuntu systems, systemd is commonly used as the init system.

### Useful commands

```bash
systemd-analyze
systemd-analyze blame
systemctl get-default
systemctl list-units --type=service
```

---

## 8. Explore Linux System Information

Execute the following commands in your Ubuntu terminal.

### Kernel information

```bash
uname -r
uname -a
cat /proc/version
```

### Distribution information

```bash
cat /etc/os-release
hostnamectl
```

### CPU and memory information

```bash
lscpu
free -h
```

### Kernel modules

```bash
lsmod
```

### System uptime

```bash
uptime
```

### System processes

```bash
ps aux
```

---

## 9. Hands-on Lab: Explore Your Linux Environment

### Lab 1: Identify the Linux kernel

```bash
uname -r
```

Expected result: Your installed Linux kernel version.

### Lab 2: Identify the distribution

```bash
cat /etc/os-release
```

Expected result: Distribution name and release details.

### Lab 3: Identify the current user

```bash
whoami
id
```

Expected result: Username, UID, GID and group memberships.

### Lab 4: Explore system memory

```bash
free -h
```

Expected result: Total, used and available memory.

### Lab 5: Explore running processes

```bash
ps aux | head -10
```

Expected result: A sample of currently running processes.

### Lab 6: Check system uptime

```bash
uptime
```

Expected result: How long the system has been running and load averages.

---

## 10. Knowledge Check

1. Who created the Linux kernel?
2. What was the original purpose of the GNU Project?
3. What is the difference between Unix and Linux?
4. What are the main responsibilities of the Linux kernel?
5. What is the difference between kernel space and user space?
6. What is a system call?
7. What is a daemon?
8. What is the role of a bootloader?
9. What is systemd?
10. What is the difference between a terminal and a shell?
11. What is the root user?
12. What is the difference between a kernel and a Linux distribution?

---

## 11. Practical Assignment

Complete these tasks and record your results:

- Identify your kernel version.
- Identify your Linux distribution.
- Find your current UID and GID.
- Check CPU architecture.
- Check memory availability.
- Identify the init system.
- Display the first 10 running processes.
- Check system uptime.

Document your findings in your own words.

---

## Additional Learning Resources

- [Linux Kernel Documentation](https://docs.kernel.org/)
- [The GNU Project](https://www.gnu.org/)
- [Linux Kernel Archives](https://www.kernel.org/)
- [The Linux man-pages Project](https://www.kernel.org/doc/man-pages/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)

---

**Previous Module:** Getting Started with Linux

**Next Module:** Linux Distributions

**Repository:** Linux Junction — Independent Linux Learning Resource
