# Linux Cheat Sheet

## ApexPlanet Internship – Task 1

I used Kali Linux for practicing the basic Linux commands required for this task.

---

## 1. pwd

`pwd` shows the current working directory.

```bash
pwd
```

Example output:

```text
/home/kali
```

---

## 2. ls

`ls` is used to list files and directories.

```bash
ls
```

Some useful options:

```bash
ls -l
ls -a
ls -la
```

- `-l` → detailed information
- `-a` → shows hidden files

---

## 3. cd

`cd` is used to change the current directory.

```bash
cd Documents
```

Go back one directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

---

## 4. chmod

`chmod` is used to change file or directory permissions.

Example:

```bash
chmod +x script.sh
```

This gives execute permission to the file.

Another example:

```bash
chmod 644 file.txt
```

---

## 5. chown

`chown` is used to change the owner of a file or directory.

Example:

```bash
sudo chown kali file.txt
```

To change owner and group:

```bash
sudo chown kali:kali file.txt
```

---

## 6. apt

`apt` is the package management command commonly used in Debian-based Linux distributions such as Kali Linux.

Update package information:

```bash
sudo apt update
```

Install a package:

```bash
sudo apt install <package-name>
```

Remove a package:

```bash
sudo apt remove <package-name>
```

---

## 7. dpkg

`dpkg` is another package management tool used with Debian packages.

To install a `.deb` package:

```bash
sudo dpkg -i package.deb
```

To check installed packages:

```bash
dpkg -l
```

---

## 8. ifconfig

`ifconfig` can be used to view network interface information.

```bash
ifconfig
```

It can show information such as:

- Network interface
- IP address
- MAC address
- Network status

On newer Linux systems, `ip` is commonly used instead:

```bash
ip addr
```

---

## 9. ping

`ping` is used to check network connectivity.

Example:

```bash
ping 8.8.8.8
```

To send only four packets:

```bash
ping -c 4 8.8.8.8
```

For testing the local system:

```bash
ping -c 4 127.0.0.1
```

---

## 10. netstat

`netstat` can be used to view network connections and listening ports.

Example:

```bash
netstat -tuln
```

The commonly used options are:

- `-t` → TCP
- `-u` → UDP
- `-l` → listening
- `-n` → show numerical addresses

A modern alternative is:

```bash
ss -tuln
```

---

## 11. traceroute

`traceroute` is used to show the path packets take to reach a destination.

Example:

```bash
traceroute google.com
```

If it is not installed:

```bash
sudo apt install traceroute
```

---

## Quick Reference

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `chmod` | Change permissions |
| `chown` | Change ownership |
| `apt` | Manage packages |
| `dpkg` | Manage Debian packages |
| `ifconfig` | Show network information |
| `ping` | Test connectivity |
| `netstat` | View network connections |
| `traceroute` | Show network path |

---

## Commands I Practiced

The basic sequence I used while practicing was:

```bash
pwd
ls
cd
ip addr
ping -c 4 127.0.0.1
```

I also practiced file permissions and package management commands.

---

## Note

These commands were practiced in my Kali Linux virtual machine as part of the ApexPlanet cybersecurity internship.
