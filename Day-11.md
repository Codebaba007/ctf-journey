# Day 11 — Linux Strength Training

## Overview

Day 11 focused on strengthening my Linux command-line fundamentals through practical cybersecurity tasks.

Instead of only learning commands theoretically, I used Linux commands to search for files, inspect file contents, manipulate files and directories, transfer files, identify and crack hashes, decode Base64 data, encrypt and decrypt files with GPG, read SQL databases, and work through a final multi-step Linux challenge.

This room was especially useful because many of the techniques are directly applicable to reconnaissance, enumeration, privilege escalation, CTFs, and general Linux-based security work.

---

## Platform

**TryHackMe**

## Room Completed

**Linux Strength Training**

---

## What I Learned

### 1. Finding Files with `find`

I learned how to search Linux filesystems using different conditions.

Important filters include:

- File name
- File type
- File size
- File owner
- File group

Examples:

```bash
find / -type f -name "filename"
find /home -type f -name "filename"
find /home/francis -type f -user francis -size 52k
find / -type f -name "hashA.txt" 2>/dev/null
```

I also learned that:

```bash
2>/dev/null
```

can suppress permission-denied errors when searching large parts of the filesystem.

---

### 2. Searching File Contents with `grep`

I learned how `grep` can be used to search inside files rather than only searching for filenames.

Useful options:

```bash
grep -iRl "keyword" /path
```

Where:

- `-i` = case-insensitive
- `-R` = recursive search
- `-l` = show filenames containing the match

This is useful when the location of information is unknown but I know a keyword that should appear inside a file.

---

### 3. Working with Files

I reinforced the basic Linux file-management commands.

Copy:

```bash
cp file.txt /destination/
```

Move:

```bash
mv file.txt /destination/
```

Rename:

```bash
mv oldname.txt newname.txt
```

Create a file:

```bash
touch file.txt
```

Create a directory:

```bash
mkdir directory
```

Read a file:

```bash
cat file.txt
```

Edit a file:

```bash
nano file.txt
```

I also learned that filenames beginning with `-` can be interpreted as command-line options.

For these files, `--` can be used to indicate that the following argument is a filename:

```bash
mv -- -logs -newlogs
```

---

### 4. Moving Multiple Files

I learned how to move multiple files at once.

```bash
mv file1 file2 file3 -t /destination/
```

I also learned that:

```bash
mv * /destination/
```

can move all matching items from the current directory into another directory.

---

### 5. Secure File Transfer with SCP

I learned how `scp` can transfer files between Linux machines over SSH.

General syntax:

```bash
scp [file] [username]@[IP]:[destination]
```

Example:

```bash
scp script.py john@192.168.10.5:/home/john/scripts
```

This connected the Linux file-management concepts to remote systems and helped reinforce how SSH-based remote access works.

---

### 6. SSH Remote Access

I practiced connecting to the TryHackMe lab machine through SSH.

General syntax:

```bash
ssh username@MACHINE_IP
```

The room also reinforced an important distinction between:

- AttackBox IP
- Lab machine IP

The AttackBox and target machine are separate systems, so the target's IP must be used when connecting to the lab machine.

---

### 7. Hashing

I learned the basic concept of hashing.

A hash is a one-way representation of input data. It is commonly used for things such as integrity checking and password storage.

I encountered several hash algorithms during the room, including:

- MD4
- MD5
- SHA-1
- SHA-256

I also learned that hash length and formatting can provide clues about the possible hash type, but format alone does not always uniquely identify a hash.

---

### 8. Hash Identification

I learned that tools can help identify unknown hashes.

One tool introduced in the room was:

```bash
hash-identifier
```

The room also introduced Haiti as a more modern alternative.

The important lesson was that automated identification provides possibilities rather than absolute certainty.

---

### 9. Cracking Hashes with John the Ripper

I learned the basic concept of password cracking against hashes using a wordlist.

The general workflow is:

```text
Hash
  ↓
Identify hash type
  ↓
Choose wordlist
  ↓
John the Ripper
  ↓
Potential plaintext password
```

Example structure:

```bash
john --wordlist=/path/to/wordlist hash.txt
```

I also learned that the correct John format may need to be specified for certain hash types.

---

### 10. Base64 Encoding and Decoding

I learned that Base64 is **encoding**, not encryption.

Encoding changes how data is represented, while the underlying data itself is not protected by a secret key.

The Linux `base64` utility can decode Base64 data.

Example:

```bash
base64 -d encoded.txt
```

This reinforced the difference between:

```text
Encoding ≠ Encryption
```

---

### 11. GPG Encryption and Decryption

I learned the basics of file encryption and decryption using GPG.

Encryption converts readable data into protected ciphertext.

Example encryption:

```bash
gpg --cipher-algo AES-128 --symmetric history_logs.txt
```

Decryption:

```bash
gpg history_logs.txt.gpg
```

I learned that GPG can create encrypted files using the `.gpg` extension.

---

### 12. Cracking Encrypted GPG Files

I learned that John the Ripper can also be used against encrypted GPG files after converting the GPG data into a format John can process.

The general workflow is:

```text
GPG encrypted file
        ↓
     gpg2john
        ↓
     John-readable hash
        ↓
 John + wordlist
        ↓
      Password
        ↓
     GPG decrypt
```

Example:

```bash
gpg2john encrypted.gpg > hash.txt
```

Then the resulting hash can be processed by John.

---

### 13. SQL Databases

I received an introduction to reading SQL databases from Linux.

Important SQL concepts included:

- Databases
- Tables
- Rows
- Columns
- Records

Useful MySQL commands included:

```sql
SHOW DATABASES;
USE database_name;
SHOW TABLES;
DESCRIBE table_name;
SELECT * FROM table_name;
```

I learned that security investigations may require reading databases to locate credentials, configuration information, or other sensitive data.

---

### 14. Final Linux Challenge

The final challenge combined several of the skills from the room.

The challenge required me to:

- Navigate Linux directories
- Read files
- Follow information from one file to another
- Work with credentials
- Access systems through SSH
- Interact with a SQL database
- Identify credentials
- Switch users
- Work toward root access

This demonstrated how individual Linux commands become much more useful when combined into a larger investigation.

---

## Practical Experience

During this room I worked inside a TryHackMe AttackBox and interacted with a separate lab machine.

I encountered an important networking issue where I initially attempted to SSH into the AttackBox IP instead of the lab machine IP.

This helped reinforce the difference between:

```text
AttackBox
    ↓
Attacker environment

Lab Machine
    ↓
Target environment
```

I also used Linux locally through WSL while working with hashing tools, which gave me additional experience installing and using security utilities outside the TryHackMe AttackBox.

---

## Key Takeaways

- `find` is extremely useful for filesystem enumeration.
- `grep` can search file contents recursively.
- Linux file operations are fundamental to security work.
- `scp` provides secure file transfer over SSH.
- SSH requires the correct target IP and credentials.
- Hashes are one-way representations of data.
- Hash length and format can help identify possible algorithms.
- John the Ripper can test wordlists against hashes.
- Base64 is encoding, not encryption.
- GPG provides encryption and decryption functionality.
- `gpg2john` can prepare GPG files for password-cracking workflows.
- SQL databases can contain valuable security-relevant information.
- Small Linux commands can be chained together to solve larger security problems.
- Understanding Linux fundamentals is important before moving deeper into offensive security.

---

## Status

**Day 11 — Completed**

**Room:** Linux Strength Training

**Focus:** Linux fundamentals, filesystem enumeration, file manipulation, SSH/SCP, hashing, password cracking, Base64, GPG, SQL, and practical Linux investigation.

---

## Next Step

Continue along the cybersecurity roadmap while gradually strengthening Linux fundamentals alongside reconnaissance and enumeration skills.

The goal is not just to memorize commands, but to understand **why and when** each command is useful during an investigation.

---

> **Day 11 takeaway:** Linux is not just a platform for cybersecurity tools — understanding the command line itself is a core cybersecurity skill.