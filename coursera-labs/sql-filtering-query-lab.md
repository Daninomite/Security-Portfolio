\# Lab Write-Up: SQL WHERE Clause and Filtering

\*\*Date:\*\* April 7, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* SQL Filtering with WHERE and LIKE



\## Objective

Use SQL WHERE clauses to filter database results and retrieve

specific information about employee devices and departments

in an organization's database.



\## Scenario

As a security analyst I needed to:

\- Identify machines running specific operating systems

\- Locate employees in specific departments

\- Find employees working in specific office locations

\- Use pattern matching to broaden search results



\## Keywords Used



| Keyword | Purpose |

|---|---|

| `WHERE` | Filters results based on a condition |

| `=` | Exact match filter |

| `LIKE` | Pattern matching filter |

| `%` | Wildcard — matches any number of characters |



\## What I Did



\### Step 1 — Listed All Machines and Operating Systems

Retrieved device IDs and operating systems from the

machines table:

```sql

SELECT device\_id, operating\_system FROM machines;

```



\### Step 2 — Filtered for Specific Operating System

Used WHERE to find only machines running OS 2:

```sql

SELECT device\_id, operating\_system FROM machines

WHERE operating\_system = 'OS 2';

```

This returns only the rows where the operating system

exactly matches 'OS 2' — useful for identifying devices

that need specific patches or updates.



\### Step 3 — Listed Employees by Department

Filtered employees table to find Finance department staff:

```sql

SELECT \* FROM employees WHERE department = 'Finance';

```



Then retrieved Sales department employees:

```sql

SELECT \* FROM employees WHERE department = 'Sales';

```



\### Step 4 — Found Employees by Office Location

Retrieved employees in a specific office:

```sql

SELECT \* FROM employees WHERE office = 'South-109';

```



Then used LIKE with a wildcard to find all employees

in any South office:

```sql

SELECT \* FROM employees WHERE office LIKE 'South%';

```

The `%` wildcard matches anything after 'South' so this

returns South-109, South-110, South-120 etc. all in

one query.



\## Understanding WHERE vs LIKE



| Filter | Use When | Example |

|---|---|---|

| `WHERE col = 'value'` | You know the exact value | `WHERE department = 'Finance'` |

| `WHERE col LIKE 'value%'` | You know only part of the value | `WHERE office LIKE 'South%'` |



\## What I Learned

\- The WHERE clause is how you filter SQL results to find

&#x20; exactly what you need instead of returning everything

\- Exact matching with `=` is great when you know precisely

&#x20; what you're looking for

\- LIKE and the `%` wildcard are powerful for pattern matching

&#x20; when you only know part of the value

\- Single quotes are required around text values in SQL

\- As a security analyst these filtering skills are essential

&#x20; for narrowing down thousands of log entries to find

&#x20; suspicious activity quickly



\## Why This Matters in Cybersecurity

In a real SOC environment databases can contain millions

of records. Being able to filter precisely with WHERE and

LIKE means the difference between finding a threat quickly

and being buried in irrelevant data. For example:

\- Finding all login attempts from a specific country

\- Identifying all devices missing a critical patch

\- Locating all employees in a compromised department

\- Searching logs for entries matching a partial IP address

