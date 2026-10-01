# Linux Cheat Sheet

## ApexPlanet Cybersecurity & Ethical Hacking Internship

### Task 1 — Foundation & Environment Setup

This cheat sheet documents basic Linux commands practiced during Task 1 using the Kali Linux environment.

---

# 1. File System Navigation

Linux uses a hierarchical file system. Commands such as `pwd`, `ls`, and `cd` are used to navigate through directories.

## 1.1 `pwd`

### Purpose

`pwd` displays the current working directory.

### Syntax

```bash
pwd
```

### Example

```bash
pwd
```

### Expected Output

```text
/home/kali
```

The exact path may be different depending on the current directory.

### Use

Useful for identifying the directory you are currently working in.

---

## 1.2 `ls`

### Purpose

`ls` lists files and directories in the current directory.

### Syntax

```bash
ls
```

### Example

```bash
ls
```

### Useful Options

```bash
ls -l
```

Displays files with detailed information such as permissions, ownership, size, and modification time.

```bash
ls -a
```

Displays hidden files and directories.

```bash
ls -la
```

Displays both hidden files and detailed information.

---

## 1.3 `cd`

### Purpose

`cd` is used to change the current working directory.

### Syntax

```bash
cd <directory>
```

### Example

```bash
cd Documents
```

Move into the `Documents` directory.

### Move to the parent directory

```bash
cd ..
```

### Move to the home directory

```bash
cd ~
```

### Example Workflow

```bash
pwd
ls
cd Documents
pwd
```

This allows you to verify that the current directory has changed.

---

# 2. File and Directory Permissions

Linux uses permissions to control who can read, modify, or execute files and directories.

The three basic permission types are:

| Permission | Symbol | Meaning |
|---|---|---|
| Read | `r` | View/read the file |
| Write | `w` | Modify the file |
| Execute | `x` | Execute the file |

Permissions can apply to:

| User | Meaning |
|---|---|
| Owner | User who owns the file |
| Group | Group associated with the file |
| Others | All other users |

---

## 2.1 `chmod`

### Purpose

`chmod` changes the permissions of a file or directory.

### Syntax

```bash
chmod <permissions> <file>
```

### Example

```bash
chmod 755 script.sh
```

This assigns:

- Owner: read, write, execute
- Group: read, execute
- Others: read, execute

### Symbolic Example

```bash
chmod +x script.sh
```

Adds execute permission to the file.

### Check Permissions

```bash
ls -l script.sh
```

---

## 2.2 `chown`

### Purpose

`chown` changes the owner of a file or directory.

### Syntax

```bash
chown <user> <file>
```

### Example

```bash
sudo chown kali file.txt
```

### Change Owner and Group

```bash
sudo chown kali:kali file.txt
```

### Check Ownership

```bash
ls -l file.txt
```

---

# 3. Package Management

Kali Linux is based on Debian, so package management commonly uses `apt` and `dpkg`.

---

## 3.1 `apt`

### Purpose

`apt` is used to install, update, remove, and manage software packages.

### Update Package Information

```bash
sudo apt update
```

### Upgrade Installed Packages

```bash
sudo apt upgrade
```

### Install a Package

```bash
sudo apt install <package-name>
```

### Remove a Package

```bash
sudo apt remove <package-name>
```

### Search for a Package

```bash
apt search <package-name>
```

### Example

```bash
sudo apt install traceroute
```

---

## 3.2 `dpkg`

### Purpose

`dpkg` is a lower-level Debian package management tool.

It can be used to install and inspect `.deb` packages.

### Install a `.deb` Package

```bash
sudo dpkg -i package.deb
```

### List Installed Packages

```bash
dpkg -l
```

### Search Installed Packages

```bash
dpkg -l | grep <package-name>
```

### Important Difference

`apt` provides higher-level package management and can handle package dependencies.

`dpkg` works directly with Debian package files and does not automatically resolve dependencies in the same way that `apt` does.

---

# 4. Networking Commands

Linux provides several commands for checking network interfaces, testing connectivity, viewing network connections, and tracing network paths.

---

## 4.1 `ifconfig`

### Purpose

`ifconfig` displays and configures network interfaces.

### Example

```bash
ifconfig
```

It can display information such as:

- Network interface name
- IP address
- MAC address
- Network statistics

### Note

On modern Linux systems, `ip` is commonly used instead of `ifconfig`.

Example:

```bash
ip addr
```

---

## 4.2 `ping`

### Purpose

`ping` is used to test network connectivity between systems.

### Syntax

```bash
ping <IP-address-or-hostname>
```

### Example

```bash
ping -c 4 127.0.0.1
```

The `-c 4` option sends four ICMP echo requests.

### What to Observe

A successful response normally contains:

```text
64 bytes from ...
```

The output also provides response time information.

---

## 4.3 `netstat`

### Purpose

`netstat` can display network connections, listening ports, routing information, and network statistics.

### Example

```bash
netstat -an
```

### Display Listening Ports

```bash
netstat -tuln
```

Common options:

| Option | Meaning |
|---|---|
| `-t` | TCP |
| `-u` | UDP |
| `-l` | Listening |
| `-n` | Show numerical addresses and ports |

### Note

On modern Linux systems, `ss` is commonly used as an alternative.

Example:

```bash
ss -tuln
```

---

## 4.4 `traceroute`

### Purpose

`traceroute` displays the network hops between the local system and a destination.

### Syntax

```bash
traceroute <destination>
```

### Example

```bash
traceroute example.com
```

### Use

Traceroute can help understand the path traffic takes through a network.

If the command is not available, it can be installed using:

```bash
sudo apt install traceroute
```

---

# 5. Basic Linux Command Practice

The following sequence can be used for basic practice in Kali Linux.

```bash
pwd
ls
ls -la
cd /tmp
pwd
cd ..
pwd
```

Check network information:

```bash
ip addr
```

Test the local network stack:

```bash
ping -c 4 127.0.0.1
```

View listening network services:

```bash
ss -tuln
```

Check installed packages:

```bash
dpkg -l
```

---

# 6. Command Summary

| Command | Purpose |
|---|---|
| `pwd` | Display current working directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `chmod` | Change file/directory permissions |
| `chown` | Change file/directory ownership |
| `apt` | Manage software packages |
| `dpkg` | Manage Debian packages |
| `ifconfig` | Display/configure network interfaces |
| `ping` | Test network connectivity |
| `netstat` | Display network connections and statistics |
| `traceroute` | Trace network path |
| `ip addr` | Display IP/interface information |
| `ss` | Display socket/network information |

---

# 7. Task 1 Practical Evidence

The following commands were practiced in the Kali Linux lab environment:

- `pwd`
- `ls`
- `cd`
- `chmod`
- `chown`
- `apt`
- `dpkg`
- `ifconfig`
- `ping`
- `netstat`
- `traceroute`

Screenshots of relevant command execution are included in the repository's `Screenshots` directory.

---

# 8. Learning Outcome

Through this exercise, I learned how to:

- Navigate the Linux file system.
- Identify files and directories.
- Understand basic Linux permissions.
- Change file permissions and ownership.
- Manage software packages.
- Check network interface information.
- Test network connectivity.
- View network connections and listening ports.
- Trace network paths.
- Use basic Linux commands in a cybersecurity lab environment.

---

## Lab Environment

**Operating System:** Kali Linux  
**Virtualization Platform:** VMware Workstation  
**Purpose:** Cybersecurity learning and controlled laboratory practice

All practical security activities were performed in an authorized and controlled lab environment for educational purposes.
