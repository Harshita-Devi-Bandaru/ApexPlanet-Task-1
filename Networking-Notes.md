# Networking Notes

## ApexPlanet Internship – Task 1

This section contains the basic networking concepts I studied as part of Task 1.

The main topics are:

- OSI Model
- TCP/IP Model
- DNS
- HTTP and HTTPS
- IP Addressing
- Subnetting
- NAT

---

## 1. OSI Model

The OSI model has seven layers. It helps us understand how communication takes place between networked systems.

| Layer | Name | Basic Function |
|---|---|---|
| 7 | Application | Network services used by applications |
| 6 | Presentation | Data format, encryption and compression |
| 5 | Session | Establishes and manages sessions |
| 4 | Transport | End-to-end communication |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | Frames and MAC addresses |
| 1 | Physical | Transmission of bits |

### Easy way to remember

```text
7 - Application
6 - Presentation
5 - Session
4 - Transport
3 - Network
2 - Data Link
1 - Physical
```

---

## 2. TCP/IP Model

The TCP/IP model is commonly described using four layers.

| TCP/IP Layer | Examples |
|---|---|
| Application | HTTP, HTTPS, DNS |
| Transport | TCP, UDP |
| Internet | IP, ICMP |
| Network Access | Ethernet, Wi-Fi |

---

## 3. OSI and TCP/IP

The models can be roughly mapped like this:

```text
OSI                    TCP/IP

Application  ┐
Presentation ├──────→  Application
Session      ┘

Transport    ───────→  Transport

Network      ───────→  Internet

Data Link    ┐
Physical     ┘──────→  Network Access
```

---

## 4. DNS

DNS stands for **Domain Name System**.

It converts domain names into IP addresses so that systems can locate the required server.

For example:

```text
google.com
     ↓
DNS
     ↓
IP Address
```

Some common DNS record types are:

| Record | Purpose |
|---|---|
| A | Maps a domain to an IPv4 address |
| AAAA | Maps a domain to an IPv6 address |
| CNAME | Alias for another domain |
| MX | Mail server information |
| NS | Name server information |

### DNS command

```bash
nslookup google.com
```

Another command:

```bash
dig google.com
```

---

## 5. HTTP

HTTP stands for **Hypertext Transfer Protocol**.

It is used for communication between web browsers and web servers.

Example:

```text
Browser
   ↓
HTTP Request
   ↓
Web Server
   ↓
HTTP Response
   ↓
Browser
```

Some common HTTP methods are:

```text
GET
POST
PUT
DELETE
```

### Common HTTP status codes

| Code | Meaning |
|---|---|
| 200 | OK |
| 301 | Moved Permanently |
| 302 | Found / Redirect |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## 6. HTTPS

HTTPS means **HTTP Secure**.

HTTPS uses TLS to help protect communication between the client and server.

```text
HTTP
Client -------- Server

HTTPS
Client ======== Server
       TLS
```

TLS helps provide:

- Confidentiality
- Integrity
- Server authentication through certificates

---

## 7. IP Addressing

An IP address identifies a network interface on an IP network.

### IPv4

IPv4 addresses use 32 bits.

Example:

```text
192.168.1.10
```

IPv4 is normally written as four decimal numbers separated by dots.

### IPv6

IPv6 uses 128 bits.

Example:

```text
2001:db8::1
```

---

## 8. Private IPv4 Addresses

The commonly used private IPv4 ranges are:

| Range | CIDR |
|---|---|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

These addresses are commonly used inside private networks.

---

## 9. Subnetting

Subnetting means dividing a network into smaller networks.

A subnet mask is used to identify the network and host portions of an IP address.

Example:

```text
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
CIDR: /24
```

With a `/24` network:

```text
Network:   192.168.1.0
Host:      192.168.1.x
Broadcast: 192.168.1.255
```

Subnetting can help organize networks and manage IP addresses.

---

## 10. NAT

NAT stands for **Network Address Translation**.

It allows private IP addresses to communicate through a device that translates them to another address, commonly a public address when accessing the internet.

Simple example:

```text
Private Network
192.168.1.x
      |
      ↓
    NAT
      |
      ↓
   Internet
```

---

## 11. NAT vs Host-Only Network in VMware

### NAT

With NAT networking, a virtual machine can normally access external networks through the host's connection.

```text
VM
 ↓
VMware NAT
 ↓
Host
 ↓
Internet
```

### Host-Only

Host-Only networking creates a private network between the host and virtual machines.

```text
Kali
  |
  | Host-Only
  |
Metasploitable
```

This is useful for an isolated cybersecurity lab because the vulnerable target can communicate with the attacker VM without being directly exposed to the external network.

---

## 12. Useful Networking Commands

Check IP addresses:

```bash
ip addr
```

Check routing table:

```bash
ip route
```

Test the local system:

```bash
ping -c 4 127.0.0.1
```

Check listening TCP/UDP ports:

```bash
ss -tuln
```

Check DNS:

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

---

## 13. Simple Lab Practice

I used the following commands in Kali Linux:

```bash
ip addr
```

to check the network interfaces.

Then:

```bash
ip route
```

to check the routing information.

For connectivity:

```bash
ping -c 4 127.0.0.1
```

I also used:

```bash
ss -tuln
```

to view listening ports.

---

## Quick Reference

| Topic | Main Point |
|---|---|
| OSI | Seven-layer networking model |
| TCP/IP | Practical networking model |
| DNS | Converts domain names to IP addresses |
| HTTP | Web communication protocol |
| HTTPS | HTTP secured using TLS |
| IPv4 | 32-bit addressing |
| IPv6 | 128-bit addressing |
| Subnetting | Divides networks into smaller networks |
| NAT | Translates network addresses |
| Host-Only | Useful for isolated VM lab networks |

---

## What I Learned

From this section, I understood the basic structure of network communication and the purpose of the OSI and TCP/IP models.

I also practiced checking IP addresses, routes, connectivity, listening ports and DNS information in Kali Linux.

The Host-Only network was particularly useful for understanding how an isolated cybersecurity lab can be configured.
