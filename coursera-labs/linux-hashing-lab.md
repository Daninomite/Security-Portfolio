\# Lab Write-Up: Creating and Comparing Hash Values

\*\*Date:\*\* May 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* File Integrity and Cryptographic Hashing



\## Objective

Use Linux command line tools to generate SHA-256 hash

values for files and compare them to verify file

integrity and identify differences between files.



\## Commands Used



| Command | Purpose |

|---|---|

| `pwd` | Print working directory — confirm current location |

| `ls` | List contents of the home directory |

| `cat` | Read and display file contents |

| `sha256sum` | Generate SHA-256 cryptographic hash of a file |

| `>>` | Append output to a file |

| `cmp` | Compare two files byte by byte |



\## What I Did



\### Step 1 — Explored the Directory

Confirmed location and listed available files:

```bash

pwd

ls

```



\### Step 2 — Read the File Contents

Examined the plaintext contents of both files to

compare them visually before hashing:

```bash

cat file1.txt

cat file2.txt

```

This step shows whether files appear identical to

the human eye — which is important because files

that look the same may have hidden differences that

only hashing can reveal.



\### Step 3 — Generated SHA-256 Hashes

Computed the SHA-256 hash value for each file:

```bash

sha256sum file1.txt

sha256sum file2.txt

```

Each hash produces a unique 64 character hexadecimal

string that acts as a digital fingerprint for that

file. Even the tiniest change to a file produces a

completely different hash.



\### Step 4 — Saved Hashes to Files

Appended each hash output to its own file for

comparison:

```bash

sha256sum file1.txt >> file1hash

sha256sum file2.txt >> file2hash

```

The >> operator appends output to a file rather

than overwriting it — useful for building hash

logs over time.



\### Step 5 — Verified Hash Files

Read the saved hash files to confirm they were

written correctly:

```bash

cat file1hash

cat file2hash

```



\### Step 6 — Compared the Hash Files

Used cmp to compare the two hash files byte by byte:

```bash

cmp file1hash file2hash

```

If the files are identical cmp returns nothing.

If they differ cmp shows exactly where the first

difference occurs — confirming the files are not

the same even if they appear similar.



\## Understanding SHA-256 Hashing



SHA-256 (Secure Hash Algorithm 256-bit) produces

a fixed length 256-bit (64 character) hash from

any input regardless of file size.



Key properties of cryptographic hashes:

| Property | Description |

|---|---|

| Deterministic | Same input always produces same hash |

| One-way | Cannot reverse a hash to get original data |

| Avalanche effect | Tiny change = completely different hash |

| Fixed length | Always 64 characters regardless of file size |

| Collision resistant | Virtually impossible for two files to share a hash |



\## Example of the Avalanche Effect

Even changing one character produces a completely

different hash:


"hello"  → 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824

"hello." → 7509e5bda0c762d2bac7f90d758b5b2263fa01ccbc542ab5e3df163be08e6ca9



\## What I Learned

\- How SHA-256 hashing works and why it is used for

&#x20; file integrity verification

\- How to generate hash values from the Linux command

&#x20; line using sha256sum

\- How to save and compare hash values using >> and cmp

\- The avalanche effect — why even a single character

&#x20; change produces a completely different hash

\- Why hashing is one way — you cannot recover the

&#x20; original file from its hash alone

\- How the cmp command identifies differences between

&#x20; files at the byte level



\## Why This Matters in Cybersecurity

Hashing is one of the most important tools in a

security analyst's toolkit. Real world applications:

\- \*\*File integrity monitoring\*\* — detecting if critical

&#x20; system files have been tampered with

\- \*\*Malware analysis\*\* — identifying known malware by

&#x20; its hash value against threat intelligence databases

\- \*\*Digital forensics\*\* — verifying evidence files

&#x20; haven't been altered during investigation

\- \*\*Password storage\*\* — storing password hashes

&#x20; instead of plaintext passwords

\- \*\*Chain of custody\*\* — proving evidence integrity

&#x20; in legal proceedings



Tools like Wazuh and Splunk use file hashing

constantly to detect unauthorized changes to

monitored systems — making this a directly

applicable skill for SOC analyst work.

