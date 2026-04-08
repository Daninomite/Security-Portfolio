\# Lab Write-Up: Basic SQL Queries

\*\*Date:\*\* April 6, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* SQL Fundamentals for Security Analysis



\## Objective

Use SQL queries to investigate employee device update status

and analyze login activity for unusual behavior in an

organization's database.



\## Scenario

As a security analyst I needed to:

\- Determine which employee devices required updates

\- Investigate user login activity for unusual patterns

\- Use SQL to efficiently retrieve and organize relevant data

from the machines and login\_attempts tables



\## Commands Used



| Keyword | Purpose |

|---|---|

| `SELECT` | Specifies which columns to retrieve |

| `FROM` | Specifies which table to query |

| `\*` | Wildcard — selects all columns |

| `ORDER BY` | Sorts results by a specified column |



\## What I Did



\### Step 1 — Retrieved Device Information

First I pulled all data from the machines table to get

a full picture of employee devices:

```sql

SELECT \* FROM machines;

```



Then I narrowed it down to specific columns I needed:

```sql

SELECT device\_id, email\_client FROM machines;

```



Then retrieved device and patch information to identify

devices needing updates:

```sql

SELECT device\_id, operating\_system, OS\_patch\_date FROM machines;

```



\### Step 2 — Investigated Login Activity

Retrieved specific columns from the login\_attempts table

to look for unusual activity:

```sql

SELECT event\_id, country FROM log\_in\_attempts;

SELECT username, login\_date, login\_time FROM log\_in\_attempts;

```



Then pulled all login data for a complete view:

```sql

SELECT \* FROM log\_in\_attempts;

```



\### Step 3 — Sorted Data with ORDER BY

Used ORDER BY to organize login attempts chronologically

by date:

```sql

SELECT \* FROM log\_in\_attempts ORDER BY login\_date;

```



Then refined the sort by adding login time as a secondary

sort to get precise chronological order:

```sql

SELECT \* FROM log\_in\_attempts ORDER BY login\_date, login\_time;

```



\## What I Learned

\- How to use SELECT and FROM to retrieve specific data

&#x20; from a database table

\- The difference between selecting all columns with `\*`

&#x20; versus selecting specific columns — specific is better

&#x20; for efficiency and clarity

\- How ORDER BY works and why sorting by multiple columns

&#x20; gives more precise results

\- Why SQL is essential for security analysts — databases

&#x20; store massive amounts of log data that would be impossible

&#x20; to analyze manually

\- How to approach a security investigation systematically

&#x20; by starting broad then narrowing down to relevant data



\## Why This Matters in Cybersecurity

SQL is one of the most important tools in a SOC analyst's

toolkit. Security logs, user activity, device inventories,

and threat data are all stored in databases. Being able to

query that data quickly and accurately is critical for:

\- Identifying compromised accounts through login analysis

\- Tracking device compliance and patch status

\- Investigating security incidents by filtering relevant events

\- Building reports for security teams and management

