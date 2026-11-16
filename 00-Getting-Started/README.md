# Module 00: Getting Started with Linux

## Learning Objectives

By completing this module, you will understand:

- What Linux is and why it is widely used.
- The history and evolution of Linux.
- Linux distributions and their differences.
- Linux architecture and its major components.
- Linux vs Windows operating systems.
- The role of Linux in DevOps and cloud infrastructure.
- How to prepare a Linux learning environment using Ubuntu on WSL.

---

## 1. What is Linux?

Linux is an open-source, Unix-like operating system kernel originally created by Linus Torvalds in 1991.

An operating system manages computer hardware and software resources and provides an environment for applications to execute.

Linux is commonly used in:

- Servers and data centers
- Cloud infrastructure
- Containers and Kubernetes
- Embedded systems
- Networking devices
- Supercomputers
- Android-based devices

**Important:** Linux technically refers to the kernel. A complete Linux operating system distribution combines the Linux kernel with system utilities, libraries, package managers and applications.

## 2. Why Learn Linux?

Linux is a fundamental technology for infrastructure and DevOps engineering.

Key reasons:

1. Open source — source code is publicly available.
2. Stability — widely used for long-running server workloads.
3. Security — provides permissions, ownership and security controls.
4. Automation — supports shell scripting and command-line tools.
5. Cloud compatibility — widely supported by cloud platforms.
6. Container ecosystem — powers most container and Kubernetes environments.
7. Flexibility — supports different distributions and deployment models.

## 3. Linux vs Windows

| Feature | Linux | Windows |
|---|---|---|
| Source code | Mostly open source | Mostly proprietary |
| Interface | CLI and GUI | GUI and CLI |
| Customization | Highly customizable | More controlled |
| Common server usage | Very common | Common |
| Shells | Bash, Zsh, Fish | PowerShell, CMD |
| Package management | APT, DNF, Zypper | Winget, others |
| Filesystem hierarchy | Standardized directory hierarchy | Drive-letter based |

## 4. Linux Architecture

Linux systems can be understood through these major layers:

1. Hardware — CPU, RAM, storage and network devices.
2. Kernel — manages hardware, memory, processes and devices.
3. System libraries — provide interfaces for applications to use kernel functionality.
4. Shell — accepts commands and provides an interface to the operating system.
5. System utilities — tools used to administer and operate the system.
6. Applications — software running on the operating system.

## 5. Linux Distributions

A Linux distribution packages the Linux kernel with system utilities, libraries, package management and other software.

### Debian-based distributions
- Debian
- Ubuntu
- Linux Mint

Package manager: APT / DPKG

### Red Hat-based distributions
- Red Hat Enterprise Linux (RHEL)
- Fedora
- Rocky Linux
- AlmaLinux

Package managers: DNF / RPM

### SUSE-based distributions
- SUSE Linux Enterprise Server (SLES)
- openSUSE

Package managers: Zypper / RPM

## 6. Linux in DevOps

Linux is used throughout the DevOps lifecycle.

Examples:

- Source control: Git
- CI/CD: Jenkins, Azure DevOps agents
- Containers: Docker
- Orchestration: Kubernetes
- Configuration management: Ansible
- Infrastructure as Code: Terraform
- Monitoring: Prometheus and Grafana

## 7. Prepare Your Linux Lab

This learning repository uses Ubuntu on Windows Subsystem for Linux (WSL).

Verify your environment:

```bash
whoami
hostname
pwd
uname -a
cat /etc/os-release
```

Check system resources:

```bash
lscpu
free -h
df -h
```

## 8. First Linux Commands

| Command | Purpose |
|---|---|
| `whoami` | Display current username |
| `pwd` | Display current directory |
| `hostname` | Display system hostname |
| `uname -a` | Display kernel and system information |
| `date` | Display current date and time |
| `cal` | Display calendar, if installed |
| `clear` | Clear terminal screen |
| `history` | Display command history |
| `man ls` | Open manual for the ls command |
| `echo "Hello Linux"` | Print text in the terminal |

## 9. Hands-on Exercises

Try these commands yourself:

1. Display your Linux username.
2. Find your current working directory.
3. Display your Linux distribution details.
4. Display your kernel version.
5. Check available RAM.
6. Check available disk space.
7. Display your hostname.
8. Print `Welcome to Linux Junction` in the terminal.
9. Display the last 10 commands from your history.
10. Open the manual page for the `pwd` command.

## 10. Knowledge Check

1. What is Linux?
2. Who created the Linux kernel?
3. What is the difference between Linux and a Linux distribution?
4. What is the role of the Linux kernel?
5. What is a shell?
6. What is the difference between Ubuntu and Debian?
7. Which package manager is used by Ubuntu?
8. Why is Linux important for DevOps engineers?

---

## Additional Learning Resources

- [The Linux Kernel](https://www.kernel.org/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)
- [Linux Foundation](https://www.linuxfoundation.org/)
- [GNU Project](https://www.gnu.org/)

---

**Next Module:** Linux Fundamentals

**Repository:** Linux Junction — Independent Linux Learning Resource


