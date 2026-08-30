# Day 12 — Brute It

## Overview

On Day 12, I continued my cybersecurity journey with the **Brute It** room on TryHackMe. This room introduced me to a complete attack chain, starting from reconnaissance and moving through web enumeration, credential attacks, SSH access, and privilege escalation. Although the room was more advanced than my current beginner level and I needed guidance through several steps, it gave me practical exposure to important concepts that I will learn more deeply as I progress.

## Platform

- TryHackMe

## Room Completed

- Brute It

## What I Learned

### Reconnaissance

Used Nmap with `-sC -sV` to identify open ports, running services, and service versions. I found SSH running on port 22 and HTTP running on port 80.

### Web Enumeration

Used Gobuster to discover hidden directories on the web server and found the `/admin/` directory. I also learned that HTTP status code `301` indicates a redirect.

### HTML Source Investigation

Used `curl` to inspect the admin login page instead of relying on the slow AttackBox browser. An HTML comment revealed the username `admin`, showing how source code and comments can sometimes expose useful information.

### Brute-Force Authentication

Used Hydra with the RockYou wordlist against the authorized TryHackMe login form and discovered the admin password. This introduced me to HTTP POST form parameters, wordlists, and automated password guessing.

### SSH and RSA Keys

The admin panel contained an encrypted RSA private key. I learned how `ssh2john` converts an SSH private key into a format that John the Ripper can process, and then used John with the RockYou wordlist to recover the key's passphrase.

### SSH Access

Used the recovered RSA key and passphrase to connect to the target as the user `john` through SSH.

### Privilege Escalation

Used `sudo -l` to inspect John's sudo permissions and discovered that he could run `/bin/cat` as root without a password. This demonstrated how an incorrectly configured sudo permission can allow privilege escalation and access to root-owned files.

## Practical Experience

During this room, I followed an attack chain involving Nmap reconnaissance, Gobuster directory enumeration, HTML source inspection, Hydra, RSA private-key cracking with `ssh2john` and John the Ripper, SSH authentication, and sudo-based privilege escalation. I also practiced using the AttackBox terminal and learned that command-line tools such as `curl` can be useful when the browser is slow.

## Key Takeaways

- Nmap can identify open ports, services, and versions.
- Gobuster can discover hidden web directories.
- HTML comments and source code can contain useful clues.
- Hydra can brute-force authentication forms in authorized environments.
- SSH private keys can be protected with passphrases.
- `ssh2john` can convert SSH keys into a format suitable for John the Ripper.
- `sudo -l` is an important command for checking privilege-escalation opportunities.
- Misconfigured sudo permissions can allow a low-privileged user to perform actions as root.
- Complex CTFs depend on multiple concepts working together, so I need to strengthen my fundamentals before attempting more advanced machines independently.

## Status

**Completed**

## Next Step

I will return to easier beginner-level rooms and build my cybersecurity fundamentals step by step, focusing on one new concept at a time before moving into more complex CTFs. My long-term direction remains Security Engineering with AI Security as a specialization.

---

> **Day 12 takeaway:** A complex attack is built from many smaller concepts, so understanding the fundamentals is more important than simply completing a difficult CTF.