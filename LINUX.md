# LINUX

Here's a clear and practical syllabus for **Setting Up a Linux Server** — perfect for developers or sysadmins getting started with managing Linux servers.

---

# Linux Server Setup Syllabus

---

## 1. Introduction to Linux Servers

* Overview of Linux distributions for servers (Ubuntu, CentOS, Debian, etc.)
* Understanding server use cases: web hosting, databases, file servers, etc.
* Basics of command-line interface (CLI) and SSH

---

## 2. Installing and Accessing Linux Server

* How to install Linux server (physical machine, VM, or cloud instance)
* Accessing the server remotely via SSH (using `ssh` command, PuTTY)
* Basic SSH security tips (disabling root login, changing SSH port)

---

## 3. Linux Command Line Essentials

* Navigating the filesystem (`ls`, `cd`, `pwd`)
* File operations (`cp`, `mv`, `rm`, `touch`)
* Viewing and editing files (`cat`, `less`, `nano`, `vim`)
* Managing users and permissions (`adduser`, `chmod`, `chown`)

---

## 4. Package Management and Software Installation

* Using package managers (`apt` for Ubuntu/Debian, `yum` or `dnf` for CentOS)
* Installing, updating, and removing software packages
* Understanding repositories and PPAs

---

## 5. Network Configuration and Management

* Viewing network interfaces and IP addresses (`ifconfig`, `ip`)
* Configuring static IP vs DHCP
* Managing firewall rules with `ufw` or `firewalld`
* Testing network connectivity (`ping`, `netstat`, `ss`)

---

## 6. Setting Up Essential Services

* Installing and configuring SSH server (`openssh-server`)
* Setting up a basic web server (Apache or Nginx)
* Managing services with `systemctl` (start, stop, enable on boot)
* Understanding logs (`journalctl`, `/var/log/`)

---

## 7. Security Basics

* Configuring firewalls and SELinux/AppArmor basics
* Setting up fail2ban to prevent brute force attacks
* Using SSH keys for authentication
* Keeping system up to date and patched

---

## 8. Disk and Storage Management

* Viewing disk space usage (`df`, `du`)
* Partitioning disks with `fdisk` or `parted`
* Mounting and unmounting drives
* Managing swap space

---

## 9. Backup and Recovery

* Creating backups with `rsync` or tar archives
* Scheduling backups with `cron` jobs
* Restoring files and handling disaster recovery

---

## 10. Monitoring and Maintenance

* Monitoring system resources (`top`, `htop`, `vmstat`)
* Checking disk health (`smartctl`)
* Log monitoring and rotation (`logrotate`)
* Automating tasks with `cron`

---

## Recommended Resources

* [Ubuntu Server Guide](https://ubuntu.com/server/docs)
* [Linux Command Line Basics (Linux Foundation)](https://www.edx.org/course/introduction-to-linux)
* [DigitalOcean Community Tutorials](https://www.digitalocean.com/community/tutorials)
* [Linux Handbook](https://linuxhandbook.com/)

---
