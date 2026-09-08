# Day 06 — Active Reconnaissance

## Overview

Continued my cybersecurity journey with TryHackMe and completed the **Active Reconnaissance** room.

The goal of this session was to understand how active reconnaissance differs from passive reconnaissance and how directly interacting with an authorized target can reveal useful information about hosts, network paths, ports, services, and running software.

In Day 05, I focused on passive reconnaissance, where information is collected from publicly available sources without directly interacting with the target system.

Day 06 introduced the next step by focusing on **active reconnaissance**, where direct communication with the target is used to gather technical information.

Rather than simply running reconnaissance commands, I focused on understanding what each technique does, what information it can reveal, and why that information can become useful during later stages of security testing.

I also practiced using browser Developer Tools, `ping`, `traceroute`, Telnet, and Netcat to investigate an authorized TryHackMe target.

## Platform

**TryHackMe**

**Room:** Active Reconnaissance

## Rooms Completed

- **Active Reconnaissance**

## What I Learned

### Browser Developer Tools

I used Chrome Developer Tools while investigating a website in the TryHackMe room.

Developer Tools can be opened using `F12` or `Ctrl + Shift + I`. I explored different areas including **Elements**, **Sources**, and **Console** to understand how the website was built and what information was available on the client side.

In the Sources section, I searched through the loaded JavaScript and discovered a `questions` variable containing information related to the site's question data.

This demonstrated that browser-side JavaScript and application data can sometimes reveal useful information during reconnaissance. Since this information is delivered to the browser, it may be possible to inspect it even when it is not immediately visible on the webpage.

I also encountered Chrome's self-XSS protection when attempting to paste JavaScript into the Console. This helped me understand that browsers include protections designed to prevent users from unknowingly executing malicious code copied from untrusted sources.

After enabling pasting, I tested `questions.length`, which returned `undefined`. This showed that the data was not being treated as a normal JavaScript array, so I investigated the structure further instead of assuming that the variable was an array.

This was a useful reminder that reconnaissance is not always about finding an immediate answer. Sometimes the important part is understanding how the application's data is structured.

### Ping

I used the `ping` command to test connectivity with the target.

The commands used included:

`ping -c 5 <TARGET_IP>`

and:

`ping -c 10 <TARGET_IP>`

Ping uses **ICMP Echo Requests** and **ICMP Echo Replies** to determine whether a host is reachable and to measure the time required for packets to travel to the destination and back.

During the exercise, I learned about packet transmission, packet reception, packet loss, and round-trip time.

I also learned that the ICMP packet contains a header and a data portion. The data portion can contain an ICMP payload whose size can be controlled when using the `ping` command.

### ICMP Header

I learned that an **ICMP Echo Request has an 8-byte ICMP header**.

The basic structure is:

- Type — 1 byte
- Code — 1 byte
- Checksum — 2 bytes
- Identifier — 2 bytes
- Sequence Number — 2 bytes

The total size of these fields is **8 bytes**.

Understanding the structure of ICMP helped me connect the practical `ping` command with what is actually being transmitted across the network.

Instead of treating `ping` as simply a command that says whether a host is online, I started understanding it as a network communication process involving ICMP packets.

### Ping Data Size

I learned that the `-s` option controls the size of the data carried by an ICMP Echo Request.

The basic syntax is:

`ping -s <size> <TARGET_IP>`

This helped me distinguish between the ICMP header and the data carried inside the packet.

The `-s` option therefore changes the payload/data size rather than changing the fixed ICMP header itself.

### Windows Firewall

I also learned that Windows Firewall commonly blocks ICMP ping requests by default.

This is important because a failed ping does not automatically mean that a host is offline.

A system can be reachable while still not responding to ICMP Echo Requests because of firewall rules or network configuration.

This helped me understand why reconnaissance results need to be interpreted carefully rather than treated as absolute proof.

### Traceroute

I used `traceroute` to investigate the network path between the AttackBox and the target.

Traceroute displays the intermediate network hops between the source and destination. Each hop generally represents a router or other network device encountered while the traffic travels toward the target.

This allowed me to investigate more than just whether the target was reachable. I could also observe the path that packets took through the network.

I practiced identifying the final responding IP address and counting the number of hops between the source and destination.

This showed me how network-path information can provide additional context during reconnaissance.

### Telnet

I used Telnet to connect directly to a web service running on TCP port 80:

`telnet <TARGET_IP> 80`

Instead of relying only on a browser, I used the TCP connection to manually interact with the HTTP service.

The service returned a server banner containing:

`Server: Apache/2.4.61 (Debian)`

From this response, I identified:

- Server: Apache
- Version: 2.4.61
- Operating system information exposed in the banner: Debian

This introduced me to the concept of **banner grabbing**.

Banner grabbing involves connecting to a service and examining the information it returns. Services may expose details such as their software name, version, operating system, or other configuration information.

This type of information can become useful during later enumeration because knowing which software and version are running can help determine what should be investigated further.

### Netcat

I also used Netcat to connect directly to TCP port 21:

`nc <TARGET_IP> 21`

Port 21 is commonly associated with FTP services.

When I connected to the service, it returned a banner revealing information about the FTP server. The FTP server version discovered during the room was:

`0.17`

This demonstrated another practical use of Netcat.

Netcat can establish direct TCP connections, allowing security researchers to interact with network services and observe their responses.

Like Telnet, this can be useful for basic banner grabbing and service enumeration.

### Active Reconnaissance

The main concept of the room was understanding **active reconnaissance**.

Active reconnaissance differs from passive reconnaissance because it involves directly communicating with the target system.

Instead of only collecting information from public sources, active reconnaissance can involve sending network requests, connecting to ports, inspecting service responses, and interacting with applications.

Active reconnaissance can reveal information such as:

- Reachable hosts
- Network paths
- Open services
- Service banners
- Software names
- Software versions
- Information exposed by applications

The information discovered during active reconnaissance can help build a clearer picture of the target's attack surface.

However, active reconnaissance also creates traffic that can be observed by the target. Because of this, it must only be performed against systems where testing is explicitly authorized.

For this room, all reconnaissance activities were performed against the authorized TryHackMe environment.

## Practical Experience

During Day 06, I moved from passive reconnaissance into direct interaction with an authorized TryHackMe target.

My practical workflow involved first inspecting the website through Chrome Developer Tools. I explored the Elements, Sources, and Console areas and investigated the JavaScript loaded by the application.

While examining the source code, I discovered a `questions` variable containing application-related question data. I then investigated how the data was structured and learned that simply assuming it was a JavaScript array could lead to incorrect conclusions.

After the browser-based investigation, I moved into basic network reconnaissance.

I used `ping` to test connectivity with the target and learned how ICMP Echo Requests and Replies are used to measure reachability and round-trip time.

I then investigated the network path using `traceroute` and practiced identifying intermediate hops and the final responding IP address.

Next, I connected directly to a web service using Telnet on TCP port 80. The service returned an Apache banner:

`Apache/2.4.61 (Debian)`

This allowed me to identify the web server software and its version through banner grabbing.

Finally, I connected to TCP port 21 using Netcat and inspected the FTP service response. The service revealed the FTP server version **0.17**.

The overall workflow helped me understand how different reconnaissance techniques can reveal different pieces of information about the same target.

Most importantly, all of this testing was performed against the authorized TryHackMe environment, reinforcing that active reconnaissance should only be performed where permission has been given.

## Key Takeaways

\- Active reconnaissance directly interacts with the target system.

\- `ping` uses ICMP Echo Requests and Echo Replies to test connectivity.

\- An ICMP Echo Request has an **8-byte ICMP header**.

\- The `-s` option controls the ICMP data/payload size used by `ping`.

\- A failed ping does not always mean that a host is offline because firewalls can block ICMP traffic.

\- Traceroute can reveal the network hops between a source and destination.

\- Each traceroute hop can represent a router or network device along the path.

\- Telnet can be used to manually interact with TCP services.

\- Service banners can reveal software names and version information.

\- The web service exposed **Apache/2.4.61 (Debian)** through its banner.

\- Netcat can establish direct TCP connections to network services.

\- Port 21 commonly hosts FTP services.

\- The FTP service exposed version **0.17** during the exercise.

\- Banner grabbing is useful during service enumeration because it can reveal information about running services.

\- Browser Developer Tools can expose client-side JavaScript and application information.

\- Information delivered to the browser can sometimes provide useful reconnaissance data.

\- Active reconnaissance generates traffic and can therefore be detected by the target.

\- Active reconnaissance must only be performed against authorized targets.

\- Understanding what a service exposes is an important step before vulnerability discovery.

\- Reconnaissance is about building an accurate picture of the target before moving toward deeper security testing.

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

**Completed**

## Next Step

Continue through the cybersecurity journey while strengthening the foundations needed for enumeration, web security, vulnerability discovery, and eventually bug bounty hunting.

Do not rush directly into advanced exploitation. Keep the progression beginner-friendly and build the required networking, web, Linux, and security fundamentals properly.

---