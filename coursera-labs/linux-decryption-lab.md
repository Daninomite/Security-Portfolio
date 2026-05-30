\# Lab Write-Up: Decrypting an Encrypted Message

\*\*Date:\*\* May 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Linux Cryptography and Classical Ciphers



\## Objective

Use Linux command line tools to investigate an encrypted

message, identify the encryption method used, and decrypt

the message back to its original plaintext form.



\## Commands Used



| Command | Purpose |

|---|---|

| `pwd` | Print working directory — confirm current location |

| `ls` | List contents of a directory |

| `ls -a` | List all files including hidden ones |

| `cat` | Read contents of a file |

| `tr` | Translate/transform characters for decryption |

| `openssl` | Decrypt encrypted files using AES-256 |

| `cd` | Change directory |



\## What I Did



\### Step 1 — Explored the Home Directory

Started by confirming my location and listing directory

contents:

```bash

pwd

ls

```

Then read the README file to understand the task:

```bash

cat README.txt

```

This provided context and instructions for the

decryption investigation.



\### Step 2 — Found a Hidden File

Used ls -a to reveal hidden files in the directory

that don't appear with a standard ls command:

```bash

ls -a

```

Discovered the hidden file `.leftShift3` — in Linux

files starting with a dot are hidden by default.

This is significant from a security perspective as

attackers often hide malicious files this way.



Read the hidden file contents:

```bash

cat .leftShift3

```

The file contained a Caesar cipher — one of the

oldest known encryption methods where each letter

is shifted a fixed number of positions in the alphabet.



\### Step 3 — Decrypted the Caesar Cipher

Used the tr command to reverse the Caesar cipher

by shifting letters back 3 positions to the left:

```bash

cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"

```

This revealed the hidden plaintext message contained

in the cipher. The tr command works by mapping each

character in the first set to the corresponding

character in the second set — effectively reversing

the shift.



\### Step 4 — Decrypted the Encrypted Data File

Navigated to the correct directory:

```bash

cd \~

```

Used openssl to decrypt the AES-256 encrypted file

using the recovered password from the Caesar cipher:

```bash

openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted \\

\-out Q1.recovered -k ettubrute

```

Breaking down this command:

\- `aes-256-cbc` — encryption algorithm used

\- `-pbkdf2` — key derivation function for security

\- `-a` — base64 encoded input

\- `-d` — decrypt mode

\- `-in Q1.encrypted` — input encrypted file

\- `-out Q1.recovered` — output recovered file

\- `-k ettubrute` — decryption key



\### Step 5 — Verified and Read the Recovered File

Confirmed the decrypted file was created:

```bash

ls

```

Read the recovered file to reveal the hidden message:

```bash

cat Q1.recovered

```



\## Understanding the Encryption Methods Used



| Method | Type | Security Level | Notes |

|---|---|---|---|

| Caesar Cipher | Classical | Very Weak | Easily broken |

| AES-256-CBC | Modern Symmetric | Very Strong | Industry standard |

| PBKDF2 | Key Derivation | Strong | Slows brute force |



\## The Investigation Flow



This demonstrates a layered approach to hiding

information — a classical cipher concealing the

key to a modern encrypted file.



\## What I Learned

\- How to find hidden files in Linux using ls -a —

&#x20; a critical skill for forensic investigations

\- How Caesar ciphers work and how to reverse them

&#x20; using the tr command

\- How to use openssl to decrypt AES-256 encrypted

&#x20; files from the command line

\- The significant difference in security between

&#x20; classical and modern encryption methods

\- How attackers chain multiple obfuscation methods

&#x20; together to hide information

\- The importance of the password ettubrute — a

&#x20; reference to "Et tu, Brute?" suggesting the

&#x20; Caesar cipher connection was intentional



\## Why This Matters in Cybersecurity

Decryption skills are essential for SOC analysts

and incident responders. Real world scenarios include:

\- Decrypting captured malware communications

\- Recovering encrypted files during forensic analysis

\- Identifying weak encryption used to hide stolen data

\- Understanding how attackers use encryption to evade

&#x20; detection

\- Analyzing encrypted payloads during threat hunting



The ability to work with both classical and modern

encryption methods from the Linux command line is

a practical skill used in digital forensics and

incident response daily.

