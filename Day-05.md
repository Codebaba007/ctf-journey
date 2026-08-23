**# Day 05 — Passive Reconnaissance**

**## Overview**

Continued my cybersecurity journey with TryHackMe and completed the Passive

Reconnaissance room.

The goal of this session was to understand how information about a target can

be collected from publicly available sources without directly interacting with

the target system.

Rather than simply running reconnaissance tools, I focused on understanding

what information each source can provide and how different pieces of public

information can be combined during security research.

**## Platform**

**\*\*TryHackMe\*\***

[My TryHackMe Profile]\([https://tryhackme.com/p/L1QU1D](https://tryhackme.com/p/L1QU1D))

**## Rooms Completed**

\- Passive Reconnaissance

**## What I Learned**

**### Passive Reconnaissance**

Passive reconnaissance involves gathering information about a target from

publicly available sources without directly interacting with the target.

This allows security professionals to learn about a target while minimizing

direct interaction with its systems.

**### WHOIS**

WHOIS provides registration information associated with domain names.

It can provide useful details about a domain and help identify information

related to its registration.

**### RDAP**

RDAP is a modern protocol for retrieving domain registration information.

It provides structured registration data and can be used as an alternative to

traditional WHOIS lookups.

**### DNS Records**

DNS records provide information about how domain names are configured.

Different record types can reveal information about services and infrastructure

associated with a domain.

**### nslookup**

nslookup is a command-line tool that can be used to query DNS information.

I learned how it can be used to investigate domain names and retrieve DNS

records during reconnaissance.

**### dig**

dig is another DNS query tool that provides detailed information about DNS

responses.

It can be used to investigate specific DNS record types and understand how a

domain is configured.

**### TXT Records**

TXT records can contain publicly available text associated with a domain.

They may provide useful information during reconnaissance and can sometimes

reveal details about services or domain configuration.

**### Subdomains**

Subdomains are additional domains that exist under a main domain.

Discovering subdomains can reveal other services, applications, or areas of an

organization's infrastructure that may not be immediately visible.

**### Certificate Transparency**

Certificate Transparency provides publicly accessible records of SSL/TLS

certificates that have been issued for domains.

These records can help identify domain names and subdomains associated with an

organization.

**### DNSDumpster**

DNSDumpster is a web-based reconnaissance tool that can help discover DNS

information, subdomains, and related infrastructure.

It provides another source of publicly available information during passive

reconnaissance.

**### Shodan**

Shodan is a search engine for Internet-connected devices and services.

It can be used to discover publicly exposed systems and gather information

about services that are visible on the Internet.

**### Public Reconnaissance Sources**

The room showed how reconnaissance does not depend on a single tool.

WHOIS, RDAP, DNS information, Certificate Transparency, DNSDumpster, Shodan,

and other public sources can provide different pieces of information about a

target.

Combining these sources can create a broader picture of the target's public

presence.

**## Practical Experience**

During the Passive Reconnaissance room, I practiced gathering information from

public reconnaissance sources and investigating domain-related information.

I worked with DNS queries and explored information using tools and services

covered by the room.

I also encountered a practical limitation with the free TryHackMe AttackBox.

Some reconnaissance commands could not directly access the Internet from the

AttackBox environment.

When this happened, I used browser-based alternatives such as ICANN Lookup

where appropriate and used the web-based reconnaissance tools provided by

TryHackMe.

My practical workflow was:

1\. Identify the target

2\. Gather publicly available information

3\. Investigate domain registration information

4\. Query DNS records

5\. Look for subdomains

6\. Check Certificate Transparency information

7\. Use reconnaissance sources such as DNSDumpster and Shodan

8\. Combine the collected information to understand the target's public presence

All activity was performed inside the authorized TryHackMe learning

environment and through publicly available reconnaissance sources.

**## Key Takeaways**

\- Passive reconnaissance focuses on collecting publicly available information.

\- WHOIS and RDAP can provide domain registration information.

\- DNS records can reveal useful information about domain configuration.

\- nslookup and dig can be used to investigate DNS information.

\- TXT records may contain useful publicly available information.

\- Subdomain discovery can reveal additional parts of an organization's public infrastructure.

\- Certificate Transparency can help identify domains and subdomains.

\- DNSDumpster can assist with discovering DNS information and related infrastructure.

\- Shodan can reveal publicly exposed Internet-connected services and devices.

\- Multiple public reconnaissance sources can be combined to build a broader picture of a target.

\- Reconnaissance does not always require directly interacting with the target.

\- Practical security work also involves adapting when a tool or environment has limitations.

**## Learning Approach**

For this journey, I will focus on understanding rather than memorizing.

My approach is:

1\. Learn the basic concept

2\. Investigate the challenge or room myself

3\. Experiment safely

4\. Use hints when necessary

5\. Understand why the technique works

6\. Document important lessons

7\. Apply the concept again when possible

**## Status**

Completed

**## Next Step**

Continue through the TryHackMe Pre Security path and build stronger foundations

in computer systems, operating systems, Linux, networking, web technologies,

and cybersecurity.

---