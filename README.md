*This project has been created as part of the 42 curriculum by hahabib.*
# Born2BeRoot

## Description

Born2BeRoot is a system administration project that consists of setting up a secure Linux server inside a virtual machine. The goal is to gain a solid understanding of system administration concepts such as virtualization, disk partitioning, encryption, user management, networking, and system security.

The project requires configuring the system manually, enforcing strict security rules, and ensuring the server is stable and properly managed.

---

## Project Description

### OS Choice

For this project, I chose **Debian** as the operating system.

#### Advantages

* Highly stable and reliable, making it ideal for servers
* Large community and extensive documentation
* Simple and efficient package management using APT
* Lightweight and easy to configure

#### Disadvantages

* Older package versions due to stability focus
* Slower release cycle
* Less enterprise-oriented compared to RHEL-based systems

---

### Main Design Choices

#### Partitioning

* Implemented **LVM (Logical Volume Manager)** for flexible disk management
* Used multiple logical volumes to separate system components
* Enabled disk encryption to protect sensitive data
* use lsblk command to see the partition

#### Security Policies

* Enforced strong password policies (expiration, complexity, history)
* Configured sudo privileges with restrictions
* Disabled root login via SSH
* Changed SSH port to `4242`
* Limited authentication attempts

#### User Management

* Created users manually using terminal commands
* Managed groups and permissions carefully
* Applied the principle of least privilege

#### Services Installed

* **SSH** for remote access
* **UFW** as a firewall
* **cron** for task automation

---

### Comparisons

#### Debian vs Rocky Linux

**Debian**

* Stable and well-tested
* Large community support
* Uses APT

**Rocky Linux**

* Enterprise-focused (RHEL-based)
* Uses DNF/YUM
* More strict configuration

---

#### AppArmor vs SELinux

**AppArmor**

* Path-based security
* Easier to configure

**SELinux**

* Label-based security
* More granular but more complex

---

#### UFW vs firewalld

**UFW**

* Simple and beginner-friendly
* Easy rule-based configuration

**firewalld**

* Zone-based system
* More flexible but more complex

---

#### VirtualBox vs UTM

**VirtualBox**

* Easy to use and cross-platform
* Ideal for x86 virtualization

**UTM**

* Designed for macOS (especially Apple Silicon)
* Uses QEMU
* Better ARM support

---

## Instructions

### Connect to the Virtual Machine (SSH)

```bash
ssh <username>@<ip_address> -p 2424
```

Example:

```bash
ssh hahabib@localhost -p 2424
```

---

### User Management

```bash
# Create a new user
sudo adduser <username>

# Add user to a group
sudo adduser <username> <groupname>

For example, sudo adduser hahabib adm
sudo adduser hahabib systemd-journal

# Add user to sudo group
sudo adduser <username> sudo

# Remove user from a group
sudo deluser <username> <groupname>

# Delete a user
sudo deluser <username>

# Delete user and home directory
sudo deluser --remove-home <username>
```

---

### System Configuration (using nano)

```bash
sudo nano /etc/ssh/sshd_config
sudo nano /etc/ssh/ssh_config
sudo nano /etc/hostname
sudo nano /etc/hosts
sudo nano /etc/login.defs
sudo nano /etc/pam.d/common-password
sudo nano /etc/sudoers.d/sudo_config
sudo cat /var/log/sudo/sudo.log
```

---

### Firewall (UFW)

```bash
sudo ufw enable
sudo ufw allow 4242/tcp
sudo ufw status verbose
sudo ufw status numbered
sudo ufw delete (number)
```

---

### SSH Service

```bash
sudo service ssh status
sudo systemctl restart ssh
ss -tulnp
```

---

### Cron Jobs

```bash
crontab -u root -e
sudo /etc/profile.d/monitoring.sh
crontab -l
sudo systemctl status cron
```

---

## Resources

* Debian official documentation
* Linux manual pages (`man <command>`)
* Online tutorials and system administration guides

### AI Usage

AI was used to:

* Explain Linux and system administration concepts
* Help troubleshoot configuration issues
* Improve documentation structure and clarity

---

## Summary

This project demonstrates:

* Secure Linux server setup
* Virtualization concepts
* LVM and disk encryption
* SSH configuration and remote access
* Firewall management with UFW
* Task automation using cron
* User and permission management

It provides a strong foundation in Linux system administration and security.

