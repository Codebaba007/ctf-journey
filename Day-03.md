# Day 03 — Networking Fundamentals

## Overview

Continued my cybersecurity journey by learning the fundamentals of computer
networking.

The focus for Day 03 was understanding how computers communicate across
networks and becoming familiar with some basic networking tools used in
cybersecurity.

## Platform

**TryHackMe**

## Room Completed

- Introductory Networking

## What I Learned

### The OSI Model

Learned about the seven-layer OSI (Open Systems Interconnection) model and
how it provides a structured way to understand network communication.

The seven layers are:

1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

Each layer has a different responsibility in the process of transmitting and
receiving data.

### TCP/IP Model

Learned that the TCP/IP model is the practical networking model used as the
basis for modern networking.

The four-layer version covered in the room is:

1. Network Interface
2. Internet
3. Transport
4. Application

The TCP/IP model is more compact than the OSI model while covering similar
networking functionality.

### Encapsulation

Learned that data is processed through the networking layers before being
transmitted.

As data moves down the layers, additional information is added to it.

The data is referred to differently at different stages:

- Data
- Segment / Datagram
- Packet
- Frame
- Bits

When the receiving computer processes the transmission, the reverse process
takes place. This is called de-encapsulation.

### TCP and UDP

Learned the basic difference between TCP and UDP.

**TCP (Transmission Control Protocol)** is connection-based and focuses on
reliable delivery of data.

**UDP (User Datagram Protocol)** does not establish the same type of
connection and generally prioritizes speed over reliability.

TCP is useful when reliable delivery is important, while UDP can be useful
when speed is more important.

### TCP Three-Way Handshake

Learned how TCP establishes a connection using a three-way handshake:

1. SYN
2. SYN-ACK
3. ACK

This process establishes the connection before data is transmitted.

### IP Addresses

Learned that IP addresses are used for logical addressing on networks.

IPv4 addresses are commonly written in a format such as:

`192.168.1.1`

The Network layer of the OSI model is responsible for logical addressing and
routing.

### MAC Addresses

Learned that MAC (Media Access Control) addresses are used for physical
addressing at the Data Link layer.

A network interface has a MAC address that can be used to identify it on a
local network.

## Networking Tools

The room introduced several useful networking tools.

### Ping

`ping` can be used to test whether a remote host is reachable and can also
provide information about the IP address associated with a domain.

### Traceroute

`traceroute` can be used to examine the path that network traffic takes toward
a destination.

This is useful for understanding how traffic travels through different
network devices.

### WHOIS

`whois` can be used to query information about domain registration.

This introduced the idea of gathering information about domains during
reconnaissance.

### Dig

`dig` can be used to manually query DNS information.

This helped me understand how domain names are translated into IP addresses.

## DNS

Learned the basic purpose of DNS (Domain Name System).

DNS allows domain names such as:

`example.com`

to be translated into IP addresses that computers can use to communicate.

I also learned about the general DNS lookup process involving:

- Local hosts file
- DNS cache
- Recursive DNS servers
- Root name servers
- Top-Level Domain (TLD) servers
- Authoritative name servers

## Practical Experience

I was introduced to several command-line networking tools and how they can be
used for basic network investigation.

This was my first step toward understanding how cybersecurity tools can gather
information about systems and networks.

## Key Takeaways

- Networking allows computers and devices to communicate.
- The OSI model provides seven conceptual layers for understanding networking.
- The TCP/IP model is used as the practical foundation of modern networking.
- IP addresses provide logical addressing.
- MAC addresses provide physical addressing on local networks.
- TCP provides reliable, connection-based communication.
- UDP prioritizes speed and does not establish a TCP-style connection.
- TCP uses a three-way handshake to establish connections.
- DNS translates domain names into IP addresses.
- `ping`, `traceroute`, `whois`, and `dig` are useful networking tools.
- Networking knowledge is essential for understanding cybersecurity.

## Status

Completed

## Next Step

Continue building networking knowledge and begin applying it through practical
security challenges.

---

Understanding how computers communicate before learning how to attack or
secure them.