# Tool Familiarization

## ApexPlanet Internship – Task 1

For this task, I practiced some basic cybersecurity tools in my Kali Linux lab. The main tools I worked with were **Wireshark, Nmap, Burp Suite and Netcat**.

---

## 1. Wireshark

### What is Wireshark?

Wireshark is used to capture and analyze network packets. It helps us understand what type of traffic is moving through a network.

I used Wireshark to see packets generated during basic network activity.

### Starting Wireshark

I opened Wireshark from Kali Linux and selected the required network interface.

I also generated some traffic using:

```bash
ping -c 4 8.8.8.8
```

After starting the capture, I could see different packets in Wireshark.

### Some filters I tried

For ICMP traffic:

```text
icmp
```

For TCP traffic:

```text
tcp
```

For DNS traffic:

```text
dns
```

For HTTP traffic:

```text
http
```

### What I observed

The captured packets contain information such as:

- Source IP
- Destination IP
- Protocol
- Packet length
- Packet details

This helped me understand how network communication can be viewed at packet level.

---

## 2. Nmap

### What is Nmap?

Nmap is a network scanning tool. It can be used to find open ports and identify services running on a system.

I used Nmap only against my own lab machines.

### Basic scan

```bash
nmap <TARGET-IP>
```

For example:

```bash
nmap 192.168.56.101
```

The IP address depends on the IP assigned to my lab target.

### Service detection

```bash
nmap -sV <TARGET-IP>
```

The `-sV` option is used to identify the services and their versions.

### OS detection

```bash
sudo nmap -O <TARGET-IP>
```

The `-O` option attempts to identify the operating system.

### What I observed

The scan can show information such as:

- Open ports
- Port numbers
- Running services
- Service versions

I used this mainly to understand how network reconnaissance works.

---

## 3. Burp Suite

### What is Burp Suite?

Burp Suite is a web application security testing tool. It can be used to view and modify HTTP requests and responses.

I used it with a local/test web application rather than testing an external website.

### Proxy

The Proxy feature works between the browser and the web application.

```text
Browser
   ↓
Burp Suite
   ↓
Web Application
```

When interception is enabled, Burp can show the request sent by the browser.

For example:

```http
GET / HTTP/1.1
Host: example.local
```

I can inspect things like:

- HTTP method
- URL
- Headers
- Parameters
- Cookies
- Response

### Repeater

I also looked at the Repeater feature.

The basic process is:

1. Capture a request.
2. Send it to Repeater.
3. Change a parameter or header.
4. Send the request again.
5. Check the response.

This helped me understand how web requests are sent between a browser and a server.

---

## 4. Netcat

### What is Netcat?

Netcat, or `nc`, is a network utility that can be used to create TCP or UDP connections.

I used it to understand basic client-server communication.

### Start a listener

In one terminal:

```bash
nc -lvnp 4444
```

Here:

- `-l` → listen mode
- `-v` → verbose output
- `-n` → do not resolve DNS
- `-p` → specify the port

### Connect from another terminal

```bash
nc 127.0.0.1 4444
```

After connecting, I could type a message in one terminal and see it on the other terminal.

### What I understood

This simple exercise helped me understand how a client connects to a listening service over TCP.

---

## 5. Quick Comparison

| Tool | What I used it for |
|---|---|
| Wireshark | Capturing and checking network packets |
| Nmap | Scanning ports and identifying services |
| Burp Suite | Checking web requests and responses |
| Netcat | Testing a basic network connection |

---

## 6. Screenshots

I added screenshots from my own lab while working with these tools.

```text
Screenshots/
├── 07-Wireshark-Capture.png
├── 08-Nmap-Scan.png
├── 09-Burp-Suite.png
└── 10-Netcat.png
```

The screenshots show the actual commands, tool interfaces, and results from my lab environment.

---

## 7. What I Learned

During this part of Task 1, I got familiar with four basic cybersecurity tools.

- Wireshark helped me understand network packets.
- Nmap helped me understand port and service scanning.
- Burp Suite helped me understand HTTP requests and responses.
- Netcat helped me understand basic network connections.

These are basic exercises, but they helped me get more comfortable working with cybersecurity tools in Kali Linux.

---

## Note

All testing was performed in my own/authorized lab environment for learning purposes.
