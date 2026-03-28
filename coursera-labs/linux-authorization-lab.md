\# Lab Write-Up: Managing Authorization in Linux

\*\*Date:\*\* March 28, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Linux File Permissions and Authorization



\## Objective

Practice checking and managing file and directory permissions 

in Linux to ensure only authorized users have appropriate 

access to sensitive files.



\## Commands Used

| Command | Purpose |

|---|---|

| `pwd` | Print working directory — confirm current location |

| `ls -l` | List files with detailed permission information |

| `ls -a` | List all files including hidden files |

| `ls -la` | List all files including hidden with full details |

| `chmod` | Change file or directory permissions |



\## What I Did



\### Step 1 — Checked Current Permissions

Used `ls -l` and `ls -la` to view permissions for all files 

in the projects directory, including hidden files:

```bash

ls -l

ls -la

```

This displayed the permission string for each file, for example:

`-rwxrw-r--` which breaks down as:

\- `-` = file type (- for file, d for directory)

\- `rwx` = owner permissions (read, write, execute)

\- `rw-` = group permissions (read, write)

\- `r--` = other permissions (read only)



\### Step 2 — Fixed Incorrect Permissions

Found and corrected files with inappropriate permissions:



Removed write access for others on `project\_k.txt`:

```bash

chmod o-w project\_k.txt

```



Removed read access for group on `project\_m.txt`:

```bash

chmod g-r project\_m.txt

```



\### Step 3 — Managed Hidden File Permissions

Checked and corrected permissions on the hidden file 

`.project\_x.txt`:

```bash

ls -la .project\_x.txt

chmod u-w .project\_x.txt

chmod g+r .project\_x.txt

chmod g-w .project\_x.txt

```



\### Step 4 — Secured the Drafts Directory

Checked and removed unauthorized access from the drafts 

directory:

```bash

ls -la /home/researcher2/projects/drafts

chmod g-x drafts

```

Removing execute (`x`) permission from a directory prevents 

users from entering or accessing it entirely.



\## Understanding chmod Syntax

| Symbol | Meaning |

|---|---|

| `u` | User (owner) |

| `g` | Group |

| `o` | Others |

| `+` | Add permission |

| `-` | Remove permission |

| `r` | Read |

| `w` | Write |

| `x` | Execute |



\## What I Learned

\- How to read Linux permission strings and understand what 

&#x20; they mean for security

\- The difference between user, group, and other permissions

&#x20; and why separating them matters

\- How to use `chmod` to add and remove specific permissions

\- Why hidden files (starting with `.`) still need permission 

&#x20; management — they aren't hidden from everyone

\- Removing execute permission from a directory is how you 

&#x20; prevent users from accessing it entirely — not just removing 

&#x20; read permission



\## Why This Matters in Cybersecurity

Misconfigured file permissions are one of the most common 

security vulnerabilities in Linux systems. A file with too 

many permissions can expose sensitive data or allow 

unauthorized users to modify critical files. As a security 

analyst, auditing and correcting file permissions is a 

routine but critical task in maintaining a secure environment.

