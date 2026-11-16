# Module 02: Linux Distributions

## Learning Objectives

By completing this module, you will understand:

- What a Linux distribution is.
- The major Linux distribution families.
- Debian, Ubuntu and Linux Mint.
- RHEL, Fedora, Rocky Linux and AlmaLinux.
- SUSE Linux Enterprise and openSUSE.
- Package managers and package formats.
- LTS, stable and rolling-release models.
- How to manage packages using APT on Ubuntu.

---

## 1. What Is a Linux Distribution?

A Linux distribution (distro) is a complete operating system built around the Linux kernel.

A distribution generally includes:

- Linux kernel.
- System libraries.
- GNU utilities and other system tools.
- Package manager.
- Software repositories.
- System initialization and service management tools.
- Optional desktop environment.
- Applications and configuration tools.

Different distributions package and maintain these components differently.

### Why Do Different Distributions Exist?

Different distributions target different requirements:

- Desktop computing.
- Enterprise servers.
- Cloud infrastructure.
- Security testing.
- Container environments.
- Embedded systems.
- Software development.

---

## 2. Major Linux Distribution Families

Linux distributions are often grouped by their software packaging and historical relationships.

### 2.1 Debian Family

Examples:

- Debian
- Ubuntu
- Linux Mint
- Pop!_OS

Package management:

- APT — high-level package manager.
- DPKG — low-level Debian package management tool.
- Package format: `.deb`

Common commands:

```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx
```

### 2.2 Red Hat Family

Examples:

- Red Hat Enterprise Linux (RHEL)
- Fedora
- Rocky Linux
- AlmaLinux

Package management:

- DNF — high-level package manager.
- RPM — package format and low-level package management tool.
- Package format: `.rpm`

Common commands:

```bash
sudo dnf check-update
sudo dnf upgrade
sudo dnf install nginx
sudo dnf remove nginx
```

Note: Older Red Hat-based systems commonly used YUM. Modern RHEL-family releases generally use DNF.

### 2.3 SUSE Family

Examples:

- SUSE Linux Enterprise Server (SLES)
- openSUSE Leap
- openSUSE Tumbleweed

Package management:

- Zypper — package manager.
- RPM — package format.
- Package format: `.rpm`

Common commands:

```bash
sudo zypper refresh
sudo zypper update
sudo zypper install nginx
sudo zypper remove nginx
```

---

## 3. Important Linux Distributions

### Debian

- Community-developed distribution.
- Known for stability and extensive package repositories.
- Used as the foundation for Ubuntu.

Website: https://www.debian.org/

### Ubuntu

- Based on Debian.
- Developed by Canonical.
- Widely used for desktops, servers, cloud and development.
- Provides LTS releases.

Website: https://ubuntu.com/

### Red Hat Enterprise Linux (RHEL)

- Enterprise Linux distribution developed by Red Hat.
- Commercial support and subscription-based services.
- Common in enterprise infrastructure.

Website: https://www.redhat.com/en/
