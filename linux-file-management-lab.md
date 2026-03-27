\# Lab Write-Up: Linux File Management

\*\*Date:\*\* March 26, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Linux Command Line Basics



\## Objective

Practice managing files and directories in a Linux environment 

using the command line as a security analyst.



\## Commands Used

| Command | Purpose |

|---|---|

| `mkdir` | Create a new directory |

| `rmdir` | Remove a directory |

| `mv` | Move a file to another location |

| `rm` | Delete a file |



\## What I Did



\*\*Step 1 — Created a new directory\*\*

Created a subdirectory called `logs` inside `/home/analyst`:

```bash

mkdir /home/analyst/logs

```



\*\*Step 2 — Removed a directory\*\*

Deleted an unneeded `temp` subdirectory:

```bash

rmdir /home/analyst/temp

```



\*\*Step 3 — Moved a file\*\*

Moved `Q3patches.txt` into the `reports` subdirectory:

```bash

mv Q3patches.txt /home/analyst/reports

```



\*\*Step 4 — Deleted a file\*\*

Removed the `tempnotes.txt` file:

```bash

rm tempnotes.txt

```



\*\*Step 5 — Created a new file\*\*

Created a `tasks.txt` file in the `notes` subdirectory to 

document completed work:

```bash

touch tasks.txt

```



\## What I Learned

\- How to navigate and manage a Linux file system from the 

&#x20; command line

\- Why command line file management matters in cybersecurity —

&#x20; many security tools and servers run on Linux with no 

&#x20; graphical interface

\- The difference between `rm` and `rmdir` and when to use each

\- How security analysts organize their working directories 

&#x20; for efficiency



\## Why This Matters in Cybersecurity

Linux is the most widely used operating system in servers, 

security tools, and SOC environments. Being comfortable 

managing files from the command line is a fundamental skill 

for any security analyst.

