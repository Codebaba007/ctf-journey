# Cybersecurity Journey — Tools & Commands Cheatsheet

> Only tools, commands, and useful information actually learned during the journey.

---

# Day 01 — Cybersecurity Foundations

## TryHackMe

**Tool / Platform:** TryHackMe

Used to learn the basic difference between offensive and defensive security and the role of cybersecurity professionals.

## Offensive Security

Focuses on finding and demonstrating weaknesses in systems.

```text
Reconnaissance
      ↓
Enumeration
      ↓
Vulnerability Discovery
      ↓
Exploitation
```

## Defensive Security

Focuses on protecting systems, detecting attacks, and responding to incidents.

```text
Prevention
Detection
Monitoring
Incident Response
Recovery
```

## CTF

Capture The Flag environments provide controlled challenges for practicing cybersecurity skills.

```text
CTF → Practice in an authorized environment
```

---

# Day 02 — Linux Fundamentals

## Linux Terminal

The terminal provides a command-line interface for interacting with a Linux system.

## Commands Learned

### `pwd`

Shows the current working directory.

```bash
pwd
```

### `ls`

Lists files and directories.

```bash
ls
ls -l
ls -la
```

### `cd`

Changes the current directory.

```bash
cd directory
cd ..
cd ~
```

### `cat`

Displays file contents.

```bash
cat file.txt
```

### `less`

Reads a file page by page.

```bash
less file.txt
```

### `head`

Displays the beginning of a file.

```bash
head file.txt
```

### `tail`

Displays the end of a file.

```bash
tail file.txt
```

### `touch`

Creates an empty file.

```bash
touch file.txt
```

### `mkdir`

Creates a directory.

```bash
mkdir directory
```

### `cp`

Copies files or directories.

```bash
cp file.txt backup.txt
```

### `mv`

Moves or renames files.

```bash
mv old.txt new.txt
```

### `rm`

Removes files.

```bash
rm file.txt
```

### `rmdir`

Removes an empty directory.

```bash
rmdir directory
```

### `find`

Searches for files and directories.

```bash
find . -name "file.txt"
```

### `grep`

Searches text for a pattern.

```bash
grep "text" file.txt
```

### `echo`

Prints text.

```bash
echo "Hello"
```

Write text to a file:

```bash
echo "Hello" > file.txt
```

Append text:

```bash
echo "Another line" >> file.txt
```

## File Permissions

Linux permissions are commonly represented as:

```text
r → read
w → write
x → execute
```

Example:

```text
-rwxr-xr--
```

Permissions are associated with:

```text
Owner
Group
Others
```

---

# Day 03 — Networking Fundamentals

## Networking

A network allows systems to communicate with each other.

Basic model:

```text
Device
  ↓
Network
  ↓
Other Device
```

## IP Address

Identifies a network interface logically.

Example:

```text
192.168.1.10
```

## IPv4

IPv4 addresses contain four decimal octets.

Example:

```text
192.168.1.10
```

Each octet ranges from:

```text
0 - 255
```

## IPv6

IPv6 uses a much larger address space than IPv4.

Example:

```text
2001:db8::1
```

## MAC Address

Identifies a network interface at the local network/link layer.

```text
IP address  → logical network address
MAC address → local network interface
```

## Port

A numbered communication endpoint.

```text
0 - 65535
```

Think:

```text
IP address = building
Port        = door
Service     = what is behind the door
```

## TCP

Transmission Control Protocol.

```text
Connection-oriented
Reliable
Ordered
```

## UDP

User Datagram Protocol.

```text
Connectionless
Lower overhead
```

Memory:

```text
TCP → connection-oriented
UDP → connectionless
```

## DNS

Domain Name System.

Converts names such as:

```text
example.com
```

into network addresses such as:

```text
93.184.216.34
```

## Common Ports Learned

```text
21   → FTP
22   → SSH
23   → Telnet
25   → SMTP
53   → DNS
80   → HTTP
443  → HTTPS
445  → SMB
3389 → RDP
```

---

# Day 04 — Security / CTF Foundations

## Security Concepts

### Vulnerability

A weakness that can potentially be exploited.

### Exploit

A technique or code that takes advantage of a vulnerability.

### Payload

Data or instructions delivered as part of an attack/exploitation process.

### Threat

Something capable of causing harm to a system or organization.

### Risk

The potential impact of a threat exploiting a vulnerability.

Basic relationship:

```text
Threat
   ↓
Vulnerability
   ↓
Exploit
   ↓
Impact
```

## CTF Methodology

A basic approach:

```text
Understand target
      ↓
Gather information
      ↓
Enumerate
      ↓
Identify weakness
      ↓
Exploit when appropriate
      ↓
Capture flag
```

All practical exploitation should remain within authorized environments.

---

# Day 05 — Passive Reconnaissance

## Passive Reconnaissance

Gathering information about a target without directly interacting with the target's systems.

```text
Public Information
        ↓
Reconnaissance
        ↓
Target Information
```

## WHOIS

Used to retrieve domain registration information.

May provide:

```text
Registrar
Registration dates
Name servers
Domain status
```

## RDAP

Registration Data Access Protocol.

Modern structured alternative to traditional WHOIS.

```text
WHOIS → traditional registration lookup
RDAP  → modern structured registration lookup
```

## DNS

Domain Name System.

```text
example.com
     ↓
DNS
     ↓
IP address
```

## DNS Records

### A

Maps a hostname to an IPv4 address.

```text
A → IPv4
```

### AAAA

Maps a hostname to an IPv6 address.

```text
AAAA → IPv6
```

### CNAME

Alias for another hostname.

```text
CNAME → Alias
```

### MX

Specifies mail servers.

```text
MX → Mail server
```

### NS

Specifies authoritative name servers.

```text
NS → Name server
```

### TXT

Contains publicly available text/configuration information.

```text
TXT → Public text/configuration
```

## nslookup

Basic DNS lookup:

```bash
nslookup example.com
```

Query a specific record:

```bash
nslookup -type=MX example.com
```

## dig

Basic DNS query:

```bash
dig example.com
```

MX:

```bash
dig example.com MX
```

TXT:

```bash
dig example.com TXT
```

NS:

```bash
dig example.com NS
```

Memory:

```text
nslookup → simple DNS investigation
dig      → detailed DNS investigation
```

## Subdomains

Additional hostnames under a domain.

Example:

```text
example.com
├── www.example.com
├── mail.example.com
├── api.example.com
└── dev.example.com
```

Subdomains can reveal additional applications and infrastructure.

## Certificate Transparency

Public records of issued TLS certificates.

Can help identify:

```text
Domains
Subdomains
Related hostnames
```

## DNSDumpster

Web-based reconnaissance tool for discovering:

```text
DNS information
Subdomains
Hostnames
Related infrastructure
```

## Shodan

Search engine for Internet-connected devices and services.

Can reveal:

```text
IP addresses
Open ports
Services
Software banners
Device information
```

---

# Day 06 — Active Reconnaissance

## Active Reconnaissance

Directly interacting with an authorized target.

```text
Passive Recon
     ↓
Public information

Active Recon
     ↓
Direct communication with target
```

Active reconnaissance can be detected by the target.

## ping

Used to test whether a host responds to ICMP Echo Requests.

```bash
ping TARGET_IP
```

Send a specific number of requests:

```bash
ping -c 5 TARGET_IP
```

Change ICMP data/payload size:

```bash
ping -s 100 TARGET_IP
```

### `ping` Flags

```text
-c → number of requests
-s → ICMP data/payload size
```

## ICMP

Internet Control Message Protocol.

Ping commonly uses:

```text
ICMP Echo Request
        ↓
      Target
        ↓
ICMP Echo Reply
```

ICMP Echo header:

```text
8 bytes
```

Important:

```text
No ping response ≠ Host is definitely offline
```

A firewall can filter ICMP traffic.

## traceroute

Investigates the network path between the source and target.

```bash
traceroute TARGET_IP
```

Conceptually:

```text
Source
  ↓
Hop 1
  ↓
Hop 2
  ↓
Hop 3
  ↓
Target
```

A hop can represent an intermediate router or network device.

## Telnet

Can establish a TCP connection to a specific port.

```bash
telnet TARGET_IP 80
```

Can be used to interact manually with a service.

## HTTP Through Telnet

A basic HTTP request can be sent after connecting to a web server.

```http
GET / HTTP/1.1
```

An HTTP response may expose:

```text
HTTP version
Server software
Server version
Possible OS information
```

## Banner Grabbing

Obtaining information exposed by a network service.

Example:

```text
Server: Apache/2.4.61 (Debian)
```

Can reveal:

```text
Software → Apache
Version  → 2.4.61
OS hint  → Debian
```

## Netcat

Command:

```bash
nc
```

Basic connection:

```bash
nc TARGET_IP PORT
```

Example:

```bash
nc TARGET_IP 21
```

Netcat can:

```text
Test TCP connections
Connect to services
Read service banners
Send basic data
Interact with network services
```

## FTP

Port 21 is commonly associated with FTP.

Netcat can be used to connect to the FTP service and observe its banner:

```bash
nc TARGET_IP 21
```

## TCP vs UDP

```text
TCP → connection-oriented
UDP → connectionless
```

## HTTPS

HTTPS uses TLS encryption.

Common port:

```text
443
```

Telnet itself does not provide TLS encryption.

---

# Day 07–08 — Nmap Live Host Discovery

## Nmap

Nmap stands for:

```text
Network Mapper
```

Nmap is used for network exploration and security auditing.

The focus so far is:

```text
Host Discovery
```

Main question:

```text
Which hosts are alive?
```

## Target Specification

Single IP:

```bash
nmap TARGET_IP
```

IP range:

```bash
nmap 10.10.12.15-20
```

CIDR subnet:

```bash
nmap 10.10.12.13/29
```

Read targets from a file:

```bash
nmap -iL list_of_hosts.txt
```

List targets without scanning:

```bash
nmap -sL TARGETS
```

## CIDR

A `/29` network contains:

```text
8 IP addresses
```

Example:

```text
10.10.12.13/29
```

Network range:

```text
10.10.12.8 - 10.10.12.15
```

A `/24` network contains:

```text
256 IP addresses
```

Example:

```text
10.48.182.148/24
```

Range:

```text
10.48.182.0 - 10.48.182.255
```

Important:

```text
Addresses scanned ≠ Live hosts discovered
```

Example:

```text
256 addresses scanned
7 hosts up
```

means Nmap checked 256 possible addresses and found 7 live hosts.

## Host Discovery Without Port Scanning

The `-sn` option performs host discovery without performing a port scan.

```bash
nmap -sn TARGET
```

Example:

```bash
nmap -sn 10.48.182.148/24
```

Purpose:

```text
Find live hosts
```

Not:

```text
Find open ports
```

## ICMP Host Discovery

### ICMP Echo

```bash
nmap -PE TARGET
```

```text
-PE → ICMP Echo
```

### ICMP Timestamp

```bash
nmap -PP TARGET
```

```text
-PP → ICMP Timestamp
```

### ICMP Address Mask

```bash
nmap -PM TARGET
```

```text
-PM → ICMP Address Mask
```

Memory:

```text
-PE → Echo
-PP → Timestamp
-PM → Address Mask
```

## TCP Host Discovery

### TCP SYN Ping

```bash
nmap -PS TARGET
```

Specific port:

```bash
nmap -PS23 TARGET
```

Port 23 is commonly associated with Telnet.

```text
-PS → TCP SYN ping
```

### TCP ACK Ping

```bash
nmap -PA TARGET
```

```text
-PA → TCP ACK ping
```

Privilege difference:

```text
TCP SYN ping → does not require a privileged account
TCP ACK ping → requires a privileged account
```

## ARP Host Discovery

ARP stands for:

```text
Address Resolution Protocol
```

Used on local networks to determine the MAC address associated with an IP address.

Conceptually:

```text
Host A
  ↓
ARP Request
"Who has this IP?"
  ↓
Local Network
  ↓
Target Host
  ↓
ARP Reply
```

Important:

```text
ARP broadcasts do not normally cross routers.
```

## Reverse DNS

Nmap can perform reverse DNS lookups to resolve IP addresses into hostnames.

Conceptually:

```text
IP Address
    ↓
Reverse DNS
    ↓
Hostname
```

Disable DNS resolution:

```bash
nmap -n TARGET
```

```text
-n → disable DNS resolution
```

## Nmap Flags Learned

```text
-sn → host discovery without port scanning
-sL → list targets without scanning
-iL → read targets from a file
-n  → disable DNS resolution

-PE → ICMP Echo discovery
-PP → ICMP Timestamp discovery
-PM → ICMP Address Mask discovery

-PS → TCP SYN ping
-PA → TCP ACK ping
```

---

# Quick Command Reference

## Linux

```bash
pwd
ls
ls -l
ls -la
cd directory
cd ..
cd ~
cat file.txt
less file.txt
head file.txt
tail file.txt
touch file.txt
mkdir directory
cp file.txt backup.txt
mv old.txt new.txt
rm file.txt
rmdir directory
find . -name "file.txt"
grep "text" file.txt
echo "Hello"
echo "Hello" > file.txt
echo "Another line" >> file.txt
```

## DNS

```bash
nslookup example.com
nslookup -type=MX example.com

dig example.com
dig example.com MX
dig example.com TXT
dig example.com NS
```

## Network

```bash
ping TARGET_IP
ping -c 5 TARGET_IP
ping -s 100 TARGET_IP
traceroute TARGET_IP
```

## Service Interaction

```bash
telnet TARGET_IP 80
nc TARGET_IP PORT
nc TARGET_IP 21
```

## Nmap

```bash
nmap TARGET_IP
nmap 10.10.12.15-20
nmap 10.10.12.13/29
nmap -iL list_of_hosts.txt
nmap -sL TARGETS

nmap -sn TARGET
nmap -PE TARGET
nmap -PP TARGET
nmap -PM TARGET

nmap -PS TARGET
nmap -PS23 TARGET
nmap -PA TARGET

nmap -n TARGET
```