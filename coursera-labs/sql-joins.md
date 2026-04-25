\# Lab Write-Up: SQL Joins

\*\*Date:\*\* April 10, 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* SQL INNER JOIN, LEFT JOIN, and RIGHT JOIN



\## Objective

Use SQL joins to combine data from multiple tables to

investigate relationships between employees, their

machines, and their login attempts.



\## Scenario

As a security analyst I needed to:

\- Find information on employees and their assigned machines

\- Identify machines that may not have assigned employees

\- Find employees who may not have assigned machines

\- Connect employee data with their login attempt history



\## Join Types Used



| Join Type | What It Returns |

|---|---|

| INNER JOIN | Only rows that match in BOTH tables |

| LEFT JOIN | All rows from left table, matches from right |

| RIGHT JOIN | All rows from right table, matches from left |



\## What I Did



\### Step 1 — Inner Join: Employees and Machines

Retrieved only employees who have a matching machine

and machines that have a matching employee:



SELECT \* FROM machines

INNER JOIN employees

ON machines.device\_id = employees.device\_id;



This returns only records where a device\_id exists

in BOTH tables — employees without machines and

machines without employees are excluded.



\### Step 2 — Left Join: Employees and Machines

Retrieved all machines whether or not they have

an assigned employee:



SELECT \* FROM machines

LEFT JOIN employees

ON machines.device\_id = employees.device\_id;



All machines appear in results. Where there is no

matching employee the employee columns show NULL.

Useful for finding unassigned machines.



\### Step 3 — Right Join: Employees and Machines

Retrieved all employees whether or not they have

an assigned machine:



SELECT \* FROM machines

RIGHT JOIN employees

ON machines.device\_id = employees.device\_id;



All employees appear in results. Where there is no

matching machine the machine columns show NULL.

Useful for finding employees without assigned devices.



\### Step 4 — Inner Join: Employees and Login Attempts

Connected employee records with their login attempt

history:



SELECT \* FROM employees

INNER JOIN log\_in\_attempts

ON employees.username = log\_in\_attempts.username;



Returns only employees who have made login attempts

and only login attempts that match a known employee.



\## Understanding NULL in Joins

When using LEFT or RIGHT joins some cells may show

NULL meaning there is no matching data in the other

table. In security this is actually useful information:

\- A machine with NULL employee data = unassigned device

\- An employee with NULL machine data = no assigned device

\- Either could indicate a security concern worth

&#x20; investigating



\## What I Learned

\- INNER JOIN is the most restrictive — only matched

&#x20; rows from both tables appear

\- LEFT JOIN keeps everything from the first table

&#x20; regardless of matches

\- RIGHT JOIN keeps everything from the second table

&#x20; regardless of matches

\- The ON clause always uses the shared column that

&#x20; connects the two tables

\- NULL values in join results are meaningful in

&#x20; security investigations — they reveal missing

&#x20; relationships worth examining

\- The table listed in FROM is always the LEFT table

&#x20; and the table listed after JOIN is always the

&#x20; RIGHT table



\## Why This Matters in Cybersecurity

Security investigations often require combining data

from multiple sources. Joins allow analysts to:

\- Connect login attempts to specific employees

\- Link devices to their assigned users

\- Identify orphaned accounts or unassigned devices

\- Build complete pictures of security incidents by

&#x20; combining data that lives in separate tables

