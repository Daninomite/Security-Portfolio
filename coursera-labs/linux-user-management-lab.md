\# Lab Write-Up: Managing User Access in Linux

\*\*Date:\*\* March 31, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Linux User and Group Management



\## Objective

Practice adding and removing users from a Linux system,

managing group memberships, and assigning file ownership

to ensure proper access control.



\## Commands Used

| Command | Purpose |

|---|---|

| `sudo useradd` | Add a new user to the system |

| `sudo usermod -g` | Change a user's primary group |

| `sudo chown` | Change ownership of a file |

| `sudo usermod -a -G` | Add a user to a supplementary group |

| `sudo groupdel` | Delete a group from the system |



\## What I Did



\### Step 1 — Added a New Employee

Created a new user account for researcher9:

```bash

sudo useradd researcher9

```



\### Step 2 — Assigned Primary Group

Added researcher9 to their primary group:

```bash

sudo usermod -g research\_team researcher9

```



\### Step 3 — Assigned File Ownership

Made researcher9 the owner of their relevant project file:

```bash

sudo chown researcher9 /home/researcher2/projects/project\_r.txt

```



\### Step 4 — Added to Supplementary Group

Added researcher9 to the sales\_team supplementary group

giving them access to additional resources:

```bash

sudo usermod -a -G sales\_team researcher9

```



\### Step 5 — Deleted the Employee

Removed researcher9 from the system entirely:

```bash

sudo groupdel researcher9

```



\## Understanding sudo

Every command here starts with `sudo` which stands for 

\*\*"superuser do"\*\*. This is required for administrative 

tasks like managing users and groups — it temporarily 

grants elevated privileges to execute the command. Only 

authorized administrators should have sudo access.



\## Understanding Primary vs Supplementary Groups

| Group Type | Purpose |

|---|---|

| Primary group | The main group a user belongs to — applied to files they create |

| Supplementary group | Additional groups giving access to extra resources |



\## What I Learned

\- How to add and remove users from a Linux system

\- The difference between primary and supplementary groups

&#x20; and why both matter for access control

\- How to assign file ownership to specific users with `chown`

\- Why `sudo` is required for user management tasks and why

&#x20; limiting who has sudo access is a security best practice

\- Proper offboarding matters — removing a departed employee

&#x20; from the system immediately is critical to prevent 

&#x20; unauthorized access



\## Why This Matters in Cybersecurity

User and group management is a core responsibility in 

maintaining a secure environment. Improper user access 

is one of the leading causes of security incidents —

whether from ex-employees retaining access, users having

more permissions than needed, or files being owned by the

wrong accounts. As a security analyst, knowing how to 

audit and manage user access is an essential daily skill.

