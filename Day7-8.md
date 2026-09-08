# Day 07–08 — Nmap Live Host Discovery

## Overview

Continued my cybersecurity journey with TryHackMe and completed the Nmap Live Host Discovery room.

This room introduced Nmap and focused on using it to discover live hosts on a network before moving into deeper enumeration.

The main goal was to understand how different host discovery techniques work and how Nmap can identify systems using ICMP, TCP, and ARP-based methods.

## Platform

**TryHackMe**

[My TryHackMe Profile](https://tryhackme.com/p/L1QU1D)

## Room Completed

- Nmap Live Host Discovery

## What I Learned

### Nmap

Nmap stands for:

```text
Network Mapper
```

It is a network exploration and security auditing tool.

The focus of this room was **host discovery**.

The main question was:

```text
Which hosts are alive?
```

This is different from port scanning.

```text
Host Discovery
      ↓
Which systems are alive?

Port Scanning
      ↓
Which ports are open?
```

### Target Specification

Nmap can accept different types of targets.

A single IP address:

```bash
nmap TARGET_IP
```

An IP range:

```bash
nmap 10.10.12.15-20
```

A CIDR subnet:

```bash
nmap 10.10.12.13/29
```

A list of targets from a file:

```bash
nmap -iL list_of_hosts.txt
```

Targets can also be listed without actually scanning them:

```bash
nmap -sL TARGETS
```

### CIDR

CIDR notation can be used to specify a network range.

A `/29` network contains:

```text
8 IP addresses
```

Example:

```text
10.10.12.13/29
```

The network range is:

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

The range is:

```text
10.48.182.0 - 10.48.182.255
```

An important distinction is:

```text
Addresses scanned ≠ Live hosts discovered
```

For example:

```text
256 addresses scanned
7 hosts up
```

means Nmap checked 256 possible addresses and discovered 7 live hosts.

### Host Discovery Without Port Scanning

The `-sn` option performs host discovery without performing a port scan.

```bash
nmap -sn TARGET
```

Example:

```bash
nmap -sn 10.48.182.148/24
```

The purpose is:

```text
Find live hosts
```

rather than:

```text
Find open ports
```

### ICMP Host Discovery

Nmap supports several ICMP-based discovery methods.

#### ICMP Echo

```bash
nmap -PE TARGET
```

```text
-PE → ICMP Echo
```

#### ICMP Timestamp

```bash
nmap -PP TARGET
```

```text
-PP → ICMP Timestamp
```

#### ICMP Address Mask

```bash
nmap -PM TARGET
```

```text
-PM → ICMP Address Mask
```

Easy memory:

```text
-PE → Echo
-PP → Timestamp
-PM → Address Mask
```

### TCP Host Discovery

Nmap can also use TCP packets to discover live hosts.

#### TCP SYN Ping

```bash
nmap -PS TARGET
```

A specific port can be specified:

```bash
nmap -PS23 TARGET
```

Port 23 is commonly associated with Telnet.

```text
-PS → TCP SYN ping
```

#### TCP ACK Ping

```bash
nmap -PA TARGET
```

```text
-PA → TCP ACK ping
```

The room demonstrated an important difference:

```text
TCP SYN ping → does not require a privileged account
TCP ACK ping → requires a privileged account
```

### ARP Host Discovery

ARP stands for:

```text
Address Resolution Protocol
```

ARP is used on local networks to determine the MAC address associated with an IP address.

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

ARP discovery is particularly useful on local networks.

An important networking concept is:

```text
ARP broadcasts do not normally cross routers.
```

This means an ARP broadcast stays within the local network segment rather than being forwarded into another subnet.

### Reverse DNS

Nmap can perform reverse DNS lookups to resolve IP addresses into hostnames.

Conceptually:

```text
IP Address
    ↓
Reverse DNS
    ↓
Hostname
```

DNS resolution can be disabled with:

```bash
nmap -n TARGET
```

The `-n` option means:

```text
-n → disable DNS resolution
```

## Commands Learned

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

## Practical Experience

During the room, I practiced specifying Nmap targets using:

1. Single IP addresses
2. IP ranges
3. CIDR subnets
4. Target lists

I also practiced host discovery using:

```text
ICMP
TCP SYN
TCP ACK
ARP
```

The main workflow was:

```text
Specify Target
      ↓
Choose Discovery Method
      ↓
Send Discovery Probes
      ↓
Observe Responses
      ↓
Identify Live Hosts
```

I also practiced understanding how ARP behaves differently from routed network traffic and how Nmap can use different discovery techniques depending on the network environment.

All activity was performed inside the authorized TryHackMe learning environment.

## Key Takeaways

- Nmap stands for Network Mapper.
- Nmap can be used for network exploration and security auditing.
- Host discovery identifies live hosts before deeper enumeration.
- Host discovery is different from port scanning.
- Nmap can accept single IPs, IP ranges, CIDR networks, and target lists.
- `/29` contains 8 IP addresses.
- `/24` contains 256 IP addresses.
- The number of addresses scanned is not the same as the number of live hosts discovered.
- `-sn` performs host discovery without port scanning.
- `-PE` performs ICMP Echo discovery.
- `-PP` performs ICMP Timestamp discovery.
- `-PM` performs ICMP Address Mask discovery.
- `-PS` performs TCP SYN ping.
- `-PA` performs TCP ACK ping.
- TCP SYN ping does not require a privileged account.
- TCP ACK ping requires a privileged account.
- ARP can be used for local network host discovery.
- ARP broadcasts do not normally cross routers.
- `-n` disables DNS resolution.
- Different discovery methods can be useful in different network conditions.

## Learning Approach

For this journey, I will focus on understanding rather than memorizing.

My approach is:

1. Learn the basic concept
2. Investigate the challenge or room myself
3. Experiment safely
4. Use hints when necessary
5. Understand why the technique works
6. Document important lessons
7. Apply the concept again when possible

## Status

Completed

## Next Step

Continue learning Nmap and move from host discovery into port scanning and service enumeration.

---
