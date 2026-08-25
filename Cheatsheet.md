# Cybersecurity Journey — Tools, Commands & Knowledge Cheatsheet

A beginner-friendly reference for the tools, commands, websites, concepts, ports, and techniques discovered throughout my cybersecurity / CTF journey.

The goal is **understanding, not memorization**.

This file will grow throughout the journey. New tools, commands, sites, concepts, and lessons should be added as they are encountered.

---

## 1. Cybersecurity Workflow

A simplified security-testing workflow:

```text
Target
  ↓
Reconnaissance
  ↓
Enumeration
  ↓
Vulnerability Discovery
  ↓
Validation / Testing
  ↓
Exploitation
  ↓
Post-Exploitation
  ↓
Reporting
```

### Reconnaissance

Gather information about a target.

- **Passive reconnaissance** — collect publicly available information without directly interacting with the target.
- **Active reconnaissance** — directly communicate with an authorized target to learn what it exposes.

### Enumeration

Systematically investigate discovered hosts, ports, services, applications, directories, and other resources.

### Vulnerability Discovery

Look for weaknesses in the discovered systems or applications.

### Exploitation

In an authorized environment, demonstrate whether a vulnerability can actually be exploited.

### Reporting

Document the finding, evidence, impact, reproduction steps, and recommended remediation.

---

## 2. Core Networking Vocabulary

### Host

A device or system connected to a network.

Examples:

- Computer
- Server
- Router
- Virtual machine
- Network device

### IP Address

An address used to identify a network interface.

Example:

```text
10.49.177.254
```

Think:

> **IP address = where the machine can be reached**

### Port

A numbered communication endpoint on a host.

Ports range from:

```text
0 - 65535
```

Think:

```text
IP address = building
Port        = door
Service     = what is behind the door
```

Example:

```text
10.49.177.254:80
```

### Service

Software that listens for and handles network connections.

Example:

```text
Port:    80
Service: HTTP
Software: Apache
Version:  2.4.61
```

### Protocol

A defined set of rules used for communication.

Examples:

- TCP
- UDP
- HTTP
- HTTPS
- DNS
- FTP
- SSH
- ICMP

### Packet

A unit of data transmitted across a network. Packets contain headers and data.

---

## 3. Common Ports

These are common associations, not absolute rules. A service can run on a different port.

| Port | Common Service | Purpose |
|---:|---|---|
| 20 | FTP Data | FTP data connection |
| 21 | FTP | File Transfer Protocol |
| 22 | SSH | Secure remote access |
| 23 | Telnet | Remote terminal |
| 25 | SMTP | Sending email |
| 53 | DNS | Domain name resolution |
| 80 | HTTP | Web traffic |
| 110 | POP3 | Receiving email |
| 139 | NetBIOS | Windows networking |
| 143 | IMAP | Email access |
| 443 | HTTPS | Encrypted web traffic |
| 445 | SMB | Windows file/printer sharing |
| 3389 | RDP | Windows Remote Desktop |
| 8080 | HTTP Alternative | Common alternative web port |

**Important:** Never assume a port proves what service is running. Verify it.

---

## 4. TCP and UDP

### TCP

TCP is connection-oriented and provides mechanisms for reliable, ordered communication.

Common TCP services:

- HTTP
- HTTPS
- SSH
- FTP
- Telnet

### UDP

UDP is connectionless and has less overhead than TCP.

Common examples:

- DNS
- DHCP
- Some real-time applications

### Easy Memory Trick

```text
TCP = connection-oriented
UDP = connectionless
```

---

## 5. Passive Reconnaissance

Passive reconnaissance gathers information without directly interacting with the target's systems.

Common sources:

- WHOIS
- RDAP
- DNS information
- Certificate Transparency
- DNSDumpster
- Shodan
- Search engines
- Public websites
- Public documentation

Think:

> **What can I learn from information that is already publicly available?**

---

## 6. WHOIS

WHOIS is traditionally used to retrieve domain registration information.

It may provide:

- Registrar
- Registration dates
- Name servers
- Domain status
- Registration-related information

Availability and visibility of registration data vary because of privacy protections and registry policies.

---

## 7. RDAP

RDAP stands for **Registration Data Access Protocol**.

It is a modern, structured alternative to traditional WHOIS services.

Easy distinction:

```text
WHOIS = traditional registration lookup
RDAP  = modern structured registration lookup
```

---

## 8. DNS

DNS stands for **Domain Name System**.

It provides the naming system used to locate network services.

Conceptually:

```text
example.com
     ↓
DNS
     ↓
IP address
```

Think:

> **DNS = the Internet's naming system**

### Common DNS Record Types

| Record | Purpose |
|---|---|
| A | IPv4 address |
| AAAA | IPv6 address |
| CNAME | Alias for another hostname |
| MX | Mail servers |
| NS | Authoritative name servers |
| TXT | Public text/configuration information |

---

## 9. DNS Tools

### nslookup

Simple command-line DNS investigation.

```bash
nslookup example.com
```

Query a specific record:

```bash
nslookup -type=MX example.com
```

### dig

More detailed DNS query tool.

```bash
dig example.com
```

Specific record:

```bash
dig example.com MX
```

TXT records:

```bash
dig example.com TXT
```

Name servers:

```bash
dig example.com NS
```

Easy distinction:

```text
nslookup = simple DNS investigation
dig      = detailed DNS investigation
```

---

## 10. Subdomains

A subdomain exists beneath a main domain.

Example:

```text
example.com
├── www.example.com
├── mail.example.com
├── api.example.com
└── dev.example.com
```

Subdomains can reveal:

- Applications
- APIs
- Development environments
- Mail systems
- Administrative interfaces
- Other infrastructure

A discovered subdomain is information, not automatically a vulnerability.

---

## 11. Certificate Transparency

Certificate Transparency (CT) provides public records related to issued TLS certificates.

CT data can sometimes reveal:

- Domains
- Subdomains
- Related hostnames

This makes Certificate Transparency useful during passive reconnaissance.

---

## 12. DNSDumpster

DNSDumpster is a web-based reconnaissance service that can help discover:

- DNS information
- Subdomains
- Hostnames
- Related infrastructure

It is one source of reconnaissance information and should be combined with other sources.

---

## 13. Shodan

Shodan is a search engine focused on Internet-connected devices and services.

It can provide information such as:

- IP addresses
- Open ports
- Service information
- Software banners
- Device types

Important:

> Shodan provides information about publicly exposed services; it is not a replacement for authorized testing.

---

## 14. Active Reconnaissance

Active reconnaissance directly communicates with the authorized target.

Tools encountered:

- `ping`
- `traceroute`
- `telnet`
- `nc` / Netcat
- Nmap

Think:

> **What can I learn by communicating directly with the target?**

Active reconnaissance creates traffic, so it must only be performed against authorized targets.

---

## 15. Ping

`ping` is commonly used to test whether a host responds to ICMP Echo Requests.

Basic:

```bash
ping TARGET_IP
```

Send a fixed number of requests:

```bash
ping -c 5 TARGET_IP
```

### `-c`

Specifies the number of requests.

```bash
ping -c 5 TARGET_IP
```

means:

> Send 5 ICMP Echo Requests.

### `-s`

Controls the size of the data carried by the ICMP Echo Request.

```bash
ping -s 100 TARGET_IP
```

### Ping Output

Useful fields include:

- Packets transmitted
- Packets received
- Packet loss
- Round-trip time

Example:

```text
5 packets transmitted, 5 received, 0% packet loss
```

---

## 16. ICMP

ICMP stands for **Internet Control Message Protocol**.

It is used for network diagnostics and error reporting.

`ping` commonly uses:

```text
ICMP Echo Request
        ↓
ICMP Echo Reply
```

Conceptually:

```text
Your machine
     │
     │ Echo Request
     ↓
Target
     │
     │ Echo Reply
     ↓
Your machine
```

### ICMP Echo Request Header

An ICMP Echo Request has an **8-byte ICMP header**.

| Field | Size |
|---|---:|
| Type | 1 byte |
| Code | 1 byte |
| Checksum | 2 bytes |
| Identifier | 2 bytes |
| Sequence Number | 2 bytes |
| **Total** | **8 bytes** |

Remember:

```text
ICMP Echo header = 8 bytes
```

---

## 17. Traceroute

`traceroute` helps discover the network path between your machine and a target.

```bash
traceroute TARGET_IP
```

Conceptually:

```text
Your machine
     ↓
Hop 1
     ↓
Hop 2
     ↓
Hop 3
     ↓
Target
```

Each numbered step is a **hop**.

Traceroute can help identify:

- Network paths
- Intermediate routers
- Latency
- Where responses stop

A missing response does not necessarily mean the router is broken. Some devices do not respond to traceroute probes.

---

## 18. Telnet

Telnet is an older protocol and client used for remote communication.

In reconnaissance, the Telnet client can be used to establish a TCP connection to a specific port.

Example:

```bash
telnet TARGET_IP 80
```

This means:

```text
TARGET_IP
    ↓
TCP port 80
```

If a service is listening, the connection may succeed.

---

## 19. Manual HTTP Interaction

HTTP can be manually tested over a TCP connection.

Example request:

```http
GET / HTTP/1.1
Host: TARGET_IP
```

A server may respond with:

```text
HTTP/1.1 200 OK
Server: Apache/2.4.61
```

This demonstrates that services can expose information through their responses.

---

## 20. Banner Grabbing

**Banner grabbing** means obtaining information exposed by a network service, often including software and version information.

Example:

```text
Server: Apache/2.4.61 (Debian)
```

This can reveal:

```text
Software = Apache
Version  = 2.4.61
OS hint  = Debian
```

A version number is a clue for further research. It does **not** by itself prove that the service is vulnerable.

---

## 21. Netcat

Netcat is commonly invoked as:

```bash
nc
```

It is a general-purpose networking utility.

Basic TCP connection:

```bash
nc TARGET_IP PORT
```

Example:

```bash
nc TARGET_IP 21
```

This attempts to connect to TCP port 21.

Netcat can be useful for:

- Testing TCP connections
- Connecting to services
- Reading service banners
- Sending basic data
- Troubleshooting network communication
- Learning how protocols behave

Think:

> **Netcat = simple tool for directly interacting with network services**

---

## 22. Browser Developer Tools

Modern browsers contain powerful inspection and debugging tools.

### Elements

Inspect HTML/DOM and page structure.

### Console

Interact with JavaScript and view messages/errors.

### Sources

Inspect loaded files such as:

- JavaScript
- HTML
- CSS
- Other resources

### Network

Inspect requests and responses between the browser and server.

The Network tab will become especially important when learning web security and Burp Suite.

---

## 23. JavaScript Reconnaissance

Web applications send client-side JavaScript to the browser.

Inspecting JavaScript can sometimes reveal:

- API endpoints
- Application logic
- Variables
- Configuration
- Client-side data
- Hidden functionality

This does not automatically mean the application is vulnerable.

Important lesson:

> **Information delivered to the browser can often be inspected by the user.**

---

## 24. Nmap

Nmap stands for **Network Mapper**.

It is a major tool for network reconnaissance and enumeration.

It can help discover:

- Live hosts
- Open ports
- Services
- Service versions
- Operating system information
- Other network details

Basic idea:

```text
Target
  ↓
Nmap
  ↓
Ports
  ↓
Services
  ↓
Versions
```

### Basic Scan

```bash
nmap TARGET_IP
```

### Service/Version Detection

```bash
nmap -sV TARGET_IP
```

`-sV` attempts to identify the services and their versions.

### Default Scripts

```bash
nmap -sC TARGET_IP
```

`-sC` runs Nmap's default NSE scripts.

NSE stands for **Nmap Scripting Engine**.

### Specific Port

```bash
nmap -p 80 TARGET_IP
```

### Multiple Ports

```bash
nmap -p 21,22,80,443 TARGET_IP
```

### Port Range

```bash
nmap -p 1-1000 TARGET_IP
```

Only use Nmap scans against systems you are authorized to test.

---

## 25. Nmap Port States

### Open

A service is listening and accepting connections.

### Closed

The host is reachable, but no service is listening on that port.

### Filtered

A firewall or filtering mechanism prevents Nmap from determining whether the port is open.

```text
Open     → something is listening
Closed   → reachable, but no service
Filtered → result is being blocked/obscured
```

---

## 26. Enumeration

A useful simplified progression:

```text
Host discovered
      ↓
Ports discovered
      ↓
Services discovered
      ↓
Versions discovered
      ↓
Service-specific enumeration
      ↓
Potential vulnerabilities
```

Example:

```text
10.49.177.254
      ↓
Port 80
      ↓
HTTP
      ↓
Apache 2.4.61
      ↓
Investigate the service
      ↓
Research potential weaknesses
```

---

## 27. Reconnaissance vs Enumeration

A useful beginner distinction:

### Reconnaissance

> Gather information about the target.

### Enumeration

> Systematically investigate discovered resources in more detail.

Example:

```text
Recon
↓
"Port 80 is open."

Enumeration
↓
"Port 80 is running Apache 2.4.61."
```

---

## 28. HTTP Basics

HTTP is a protocol used for communication between web clients and servers.

Common methods:

```text
GET
POST
PUT
DELETE
PATCH
```

Basic communication:

```text
Browser
   │
   │ HTTP Request
   ↓
Web Server
   │
   │ HTTP Response
   ↓
Browser
```

### HTTPS

HTTPS is HTTP protected using TLS.

Common port:

```text
443
```

---

## 29. HTTP Status Codes

| Code | Meaning |
|---:|---|
| 200 | OK |
| 201 | Created |
| 301 | Permanent Redirect |
| 302 | Temporary Redirect |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

Easy categories:

```text
2xx = Success
3xx = Redirect
4xx = Client-side request problem
5xx = Server-side problem
```

---

## 30. Web Security Concepts — Coming Later

These are concepts to learn progressively rather than memorize now:

- Cookies
- Sessions
- Authentication
- Authorization
- Headers
- Parameters
- Forms
- APIs
- JSON
- REST
- WebSockets
- CORS
- CSRF
- XSS
- SQL Injection
- IDOR
- SSRF
- File Upload
- Path Traversal
- Command Injection
- SSTI
- Business Logic vulnerabilities

---

## 31. Tool Map

| Question | Tool |
|---|---|
| Domain registration information? | WHOIS / RDAP |
| DNS information? | `dig` / `nslookup` |
| Public subdomains? | Certificate Transparency / DNSDumpster |
| Internet-exposed services? | Shodan |
| Does the host respond to ICMP? | `ping` |
| What path does traffic take? | `traceroute` |
| Connect to one TCP port? | `telnet` |
| Make a simple network connection? | `nc` |
| Inspect browser-side code? | Developer Tools |
| Discover open ports? | Nmap |
| Identify service versions? | `nmap -sV` |
| Run default Nmap scripts? | `nmap -sC` |

---

## 32. Command Quick Reference

### DNS

```bash
nslookup example.com
dig example.com
dig example.com MX
dig example.com TXT
```

### Connectivity

```bash
ping TARGET_IP
ping -c 5 TARGET_IP
ping -s 100 TARGET_IP
```

### Network Path

```bash
traceroute TARGET_IP
```

### Service Interaction

```bash
telnet TARGET_IP 80
nc TARGET_IP 21
```

### Nmap

```bash
nmap TARGET_IP
nmap -sV TARGET_IP
nmap -sC TARGET_IP
nmap -p 80 TARGET_IP
nmap -p 21,22,80,443 TARGET_IP
nmap -p 1-1000 TARGET_IP
```

---

## 33. Command Flag Memory

| Command | Flag | Meaning |
|---|---|---|
| `ping` | `-c` | Number of requests |
| `ping` | `-s` | ICMP data/payload size |
| `nmap` | `-p` | Specify ports |
| `nmap` | `-sV` | Service/version detection |
| `nmap` | `-sC` | Default NSE scripts |

---

## 34. Sites & Resources

| Resource | Purpose |
|---|---|
| TryHackMe | Guided cybersecurity labs |
| WHOIS services | Domain registration research |
| RDAP | Structured registration data |
| DNSDumpster | DNS/subdomain reconnaissance |
| Shodan | Internet-exposed service/device discovery |
| Certificate Transparency | Certificate/domain discovery |
| Browser Developer Tools | Web application inspection |

This section will grow as new resources are discovered.

---

## 35. Useful Recon Questions

### Target

- What is the target?
- What is its IP?
- What domains are associated with it?

### Network

- Is the host reachable?
- What ports are open?
- What services are running?

### Services

- What software is running?
- What version?
- Does it expose a banner?

### Web Application

- Is HTTP/HTTPS available?
- What technology is being used?
- What pages exist?
- What endpoints exist?
- What does the browser receive?

### Security

- What information is exposed?
- What should I investigate further?
- Is there a potential vulnerability?
- Can it be safely validated within the authorized scope?

---

## 36. Safety Rule

All active security testing must be performed against systems where I have explicit authorization.

Examples:

- TryHackMe machines
- CTF environments
- My own systems
- Authorized bug bounty programs within their defined scope

Before running an active scan, ask:

> **Am I authorized to test this target?**

If the answer is unclear, stop and verify the scope.

---

## 37. Mental Model

Do not memorize tools as isolated commands.

Think in questions:

```text
"What is this domain?"
        ↓
WHOIS / RDAP / DNS

"Are there other domains?"
        ↓
Certificate Transparency / DNSDumpster

"Is this host reachable?"
        ↓
ping

"How does traffic reach it?"
        ↓
traceroute

"What ports are available?"
        ↓
Nmap

"What services are running?"
        ↓
Nmap / service interaction

"What software/version is running?"
        ↓
Nmap -sV / banner grabbing

"What does the web application expose?"
        ↓
Browser Developer Tools

"Is there a weakness?"
        ↓
Vulnerability research + authorized testing
```

The tools are ways of answering questions.

---

## 38. Personal Learning Notes

As the journey continues, add:

- New tools
- Important commands
- Useful flags
- Common ports
- Protocols
- Websites
- Security concepts
- Interesting findings
- Mistakes and lessons learned
- Techniques practiced

For every important tool, I should eventually be able to answer:

> **What does it do?**

> **Why would I use it?**

> **What does its output mean?**

> **When should I use something else instead?**

---

## 39. Current Journey Progress

### Completed

```text
Day 01 → Cybersecurity Foundations
Day 02 → Linux / System Fundamentals
Day 03 → Networking Fundamentals
Day 04 → Security / CTF Foundations
Day 05 → Passive Reconnaissance
Day 06 → Active Reconnaissance
```

### Current Direction

```text
Foundations
    ↓
Passive Recon
    ↓
Active Recon
    ↓
Nmap / Host Discovery
    ↓
Port Scanning
    ↓
Service Enumeration
    ↓
Web Enumeration
    ↓
Web Security
    ↓
Vulnerability Discovery
    ↓
Bug Bounty Practice
```

---

## 40. Final Reminder

I do not need to remember every tool.

I need to understand the relationship between them.

```text
Target
  ↓
What do I know?
  ↓
What don't I know?
  ↓
Which question should I ask?
  ↓
Which tool can answer it?
  ↓
What does the output mean?
  ↓
What should I investigate next?
```

The goal is not to memorize a hundred commands.

**Learn the question first. Learn the tool second. Learn the command third. Understand the output last.**
