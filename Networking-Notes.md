# Networking Notes

## ApexPlanet Cybersecurity & Ethical Hacking Internship

### Task 1 — Foundation & Environment Setup

This document contains notes on basic networking concepts studied as part of ApexPlanet Internship Task 1.

---

# 1. OSI Model

## What is the OSI Model?

The **Open Systems Interconnection (OSI) model** is a conceptual framework used to understand how network communication works.

It divides network communication into **seven layers**.

| Layer | Name | Main Function | Examples |
|---|---|---|---|
| 7 | Application | Provides network services to applications | HTTP, DNS, FTP |
| 6 | Presentation | Handles data representation, encryption and compression | TLS, data formats |
| 5 | Session | Establishes and manages communication sessions | Session management |
| 4 | Transport | Provides end-to-end communication | TCP, UDP |
| 3 | Network | Handles logical addressing and routing | IP, ICMP |
| 2 | Data Link | Handles frames and MAC addressing | Ethernet |
| 1 | Physical | Transmits raw bits over physical media | Cables, radio signals |

## Layer 1 — Physical

The Physical layer deals with the transmission of raw bits over a physical medium.

Examples:

- Ethernet cables
- Fiber optic cables
- Radio signals

---

## Layer 2 — Data Link

The Data Link layer provides communication between devices on the same network segment.

It works with:

- MAC addresses
- Frames
- Ethernet

---

## Layer 3 — Network

The Network layer is responsible for logical addressing and routing.

A major protocol at this layer is:

- IP

Routers operate primarily at this layer.

---

## Layer 4 — Transport

The Transport layer provides communication between applications running on different systems.

Important protocols:

### TCP

TCP is connection-oriented and provides reliable, ordered delivery.

### UDP

UDP is connectionless and has lower protocol overhead than TCP, but it does not provide the same delivery guarantees as TCP.

---

## Layer 5 — Session

The Session layer is concerned with establishing, managing, and terminating communication sessions.

---

## Layer 6 — Presentation

The Presentation layer deals with how data is represented.

Functions can include:

- Data formatting
- Encryption
- Decryption
- Compression

---

## Layer 7 — Application

The Application layer provides network services used by applications.

Examples include:

- HTTP
- HTTPS
- DNS
- FTP
- SMTP

---

# 2. TCP/IP Protocol Suite

The TCP/IP model is a practical networking model used to describe Internet communication.

A commonly used four-layer representation is:

| TCP/IP Layer | Main Function | Examples |
|---|---|---|
| Application | Provides application-level network services | HTTP, HTTPS, DNS |
| Transport | Provides end-to-end communication | TCP, UDP |
| Internet | Provides addressing and routing | IP, ICMP |
| Network Access | Handles communication over the local network | Ethernet |

## Application Layer

This layer contains protocols used by applications to communicate over networks.

Examples:

- HTTP
- HTTPS
- DNS
- FTP
- SMTP

---

## Transport Layer

The Transport layer provides communication between applications.

### TCP

TCP provides:

- Connection-oriented communication
- Reliable delivery
- Ordered data delivery
- Error detection and retransmission

### UDP

UDP provides:

- Connectionless communication
- Lower overhead
- Faster transmission in many use cases
- No guarantee of delivery or ordering

---

## Internet Layer

The Internet layer handles logical addressing and routing.

Important protocols include:

- IPv4
- IPv6
- ICMP

---

## Network Access Layer

This layer handles communication over the local network.

Examples include:

- Ethernet
- Wireless networking

---

# 3. OSI and TCP/IP Relationship

The OSI model has seven layers, while the commonly used TCP/IP model has four layers.

A simplified relationship is:

| OSI | TCP/IP |
|---|---|
| Application | Application |
| Presentation | Application |
| Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link | Network Access |
| Physical | Network Access |

The models are useful for understanding different parts of network communication.

---

# 4. DNS

## What is DNS?

**DNS (Domain Name System)** translates human-readable domain names into IP addresses.

For example:

```text
example.com
     ↓
IP address
```

Instead of remembering an IP address, users can access a service using a domain name.

## Why DNS is Important

DNS allows applications and users to locate network services using domain names.

## Basic DNS Process

A simplified DNS lookup can be represented as:

```text
User/Application
       ↓
DNS Resolver
       ↓
DNS Server
       ↓
IP Address
       ↓
Application connects to destination
```

## Common DNS Record Types

| Record | Purpose |
|---|---|
| A | Maps a domain name to an IPv4 address |
| AAAA | Maps a domain name to an IPv6 address |
| CNAME | Creates an alias for another domain name |
| MX | Identifies mail servers |
| NS | Identifies authoritative name servers |
| TXT | Stores text information associated with a domain |

---

# 5. HTTP

## What is HTTP?

**HTTP (Hypertext Transfer Protocol)** is an application-layer protocol used for communication between clients and web servers.

A simplified communication flow is:

```text
Client
   ↓
HTTP Request
   ↓
Web Server
   ↓
HTTP Response
   ↓
Client
```

## HTTP Request

An HTTP request can contain:

- HTTP method
- URL/path
- Headers
- Optional request body

Common HTTP methods include:

| Method | Common Purpose |
|---|---|
| GET | Retrieve information |
| POST | Submit data |
| PUT | Update/replace a resource |
| DELETE | Delete a resource |
| PATCH | Partially modify a resource |

---

# 6. HTTP Response

A server sends an HTTP response to a client.

A response contains:

- Status code
- Headers
- Optional response body

## Common HTTP Status Codes

| Code | Meaning |
|---|---|
| 200 | OK |
| 201 | Created |
| 301 | Moved Permanently |
| 302 | Found / Redirect |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

# 7. HTTPS

## What is HTTPS?

**HTTPS (HTTP Secure)** is HTTP communication protected using **TLS (Transport Layer Security)**.

HTTPS helps provide:

- Confidentiality
- Integrity
- Server authentication

A simplified connection is:

```text
Client
   ↓
TLS-secured connection
   ↓
Web Server
```

## HTTP vs HTTPS

| Feature | HTTP | HTTPS |
|---|---|---|
| Encryption | Not provided by HTTP itself | Uses TLS |
| Confidentiality | Not provided by HTTP itself | Provided through TLS |
| Integrity protection | Not provided by HTTP itself | Provided through TLS |
| Server authentication | Not provided by HTTP itself | Supported through TLS certificates |

---

# 8. IP Addressing

## What is an IP Address?

An IP address is a logical address used to identify a network interface for communication.

Two commonly used versions are:

- IPv4
- IPv6

---

## IPv4

IPv4 uses **32-bit addresses**.

Example:

```text
192.168.1.10
```

IPv4 addresses are commonly written as four decimal numbers separated by periods.

Each number can range from:

```text
0 - 255
```

---

## IPv6

IPv6 uses **128-bit addresses**.

Example:

```text
2001:db8::1
```

IPv6 provides a much larger address space than IPv4.

---

# 9. Private IP Addresses

Private IPv4 addresses are used within private networks.

Common private IPv4 ranges include:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

These addresses are commonly used inside local networks.

---

# 10. Subnetting

## What is Subnetting?

Subnetting divides a larger IP network into smaller logical networks called **subnets**.

Subnetting can help with:

- Network organization
- Address management
- Traffic separation
- Network design

---

## Subnet Mask

A subnet mask determines which part of an IPv4 address represents the network and which part represents hosts.

Example:

```text
IP Address:   192.168.1.10
Subnet Mask:  255.255.255.0
CIDR:         /24
```

A `/24` network commonly provides:

```text
Network:      192.168.1.0
Usable hosts: 192.168.1.1 - 192.168.1.254
Broadcast:    192.168.1.255
```

---

# 11. CIDR Notation

CIDR stands for **Classless Inter-Domain Routing**.

Example:

```text
192.168.1.0/24
```

The `/24` indicates that the first 24 bits are used for the network portion.

Some common examples:

| CIDR | Subnet Mask |
|---|---|
| /8 | 255.0.0.0 |
| /16 | 255.255.0.0 |
| /24 | 255.255.255.0 |

---

# 12. Network Address

The network address identifies the network itself.

Example:

```text
Network:
192.168.1.0/24
```

The address:

```text
192.168.1.0
```

represents the network rather than an individual host.

---

# 13. Broadcast Address

A broadcast address is used to communicate with all hosts on a particular IPv4 subnet.

For:

```text
192.168.1.0/24
```

the broadcast address is:

```text
192.168.1.255
```

---

# 14. NAT

## What is NAT?

**NAT (Network Address Translation)** translates IP addresses between network contexts.

It is commonly used to allow devices using private IP addresses to communicate with external networks through a public IP address.

Simplified example:

```text
Private Network
192.168.1.10
      ↓
    Router
      ↓
Public IP
      ↓
Internet
```

## Why NAT is Used

NAT can help:

- Allow private addresses to access external networks
- Conserve public IPv4 addresses
- Hide internal addressing from external networks

---

# 15. NAT in a Virtual Lab

In a virtualization environment, different virtual network modes can be used.

### NAT

The virtual machine can use the host's network connection to access external networks.

### Host-Only

The virtual machines communicate with the host and other machines on the host-only network, without requiring direct Internet access through that network.

For a vulnerable target such as Metasploitable, a private/host-only network is useful for keeping security testing isolated from external networks.

---

# 16. Basic Networking Commands

The following commands can be used in Kali Linux to inspect network configuration and connectivity.

## Display IP Information

```bash
ip addr
```

## Test Connectivity

```bash
ping -c 4 127.0.0.1
```

## Display Routing Information

```bash
ip route
```

## Display Listening Ports

```bash
ss -tuln
```

## DNS Lookup

```bash
nslookup example.com
```

or:

```bash
dig example.com
```

---

# 17. Networking Practical Exercise

The following commands can be practiced in the Kali Linux lab:

```bash
ip addr
```

Observe:

- Network interfaces
- IPv4 address
- IPv6 address
- Interface state

Then:

```bash
ip route
```

Observe the routing table.

Test the local network stack:

```bash
ping -c 4 127.0.0.1
```

Check listening ports:

```bash
ss -tuln
```

Perform a DNS lookup:

```bash
nslookup example.com
```

---

# 18. Networking Concepts Summary

| Topic | Key Point |
|---|---|
| OSI Model | Seven-layer conceptual networking model |
| TCP/IP | Practical model used for network communication |
| DNS | Resolves domain names to IP addresses |
| HTTP | Application-layer web communication protocol |
| HTTPS | HTTP protected using TLS |
| IPv4 | 32-bit addressing system |
| IPv6 | 128-bit addressing system |
| Subnetting | Divides networks into smaller logical networks |
| CIDR | Represents network prefixes such as `/24` |
| NAT | Translates addresses between network contexts |
| TCP | Reliable, connection-oriented transport |
| UDP | Connectionless transport with lower overhead |

---

# 19. Learning Outcome

After completing this section, I understand the basic structure of network communication and the role of:

- OSI model layers
- TCP/IP protocols
- DNS
- HTTP and HTTPS
- IP addressing
- Subnetting
- NAT
- TCP and UDP
- Basic network diagnostic commands

These concepts form the networking foundation required for further cybersecurity activities in the ApexPlanet internship.

---

## Lab Environment

**Operating System:** Kali Linux  
**Virtualization Platform:** VMware Workstation  
**Network:** Private/Host-Only Lab Network  
**Purpose:** Cybersecurity learning and controlled laboratory practice

All practical activities are performed within an authorized and controlled lab environment for educational purposes.
