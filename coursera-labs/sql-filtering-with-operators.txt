# Lab Write-Up: SQL Filtering with Operators
**Date:** April 10, 2026
**Platform:** Coursera — Google Cybersecurity Certificate
**Topic:** SQL Date, Time, and Numeric Filtering

## Objective
Use SQL comparison operators and the BETWEEN keyword to
filter login attempt data by date ranges, time ranges,
and event IDs to investigate suspicious activity.

## Scenario
As a security analyst I needed to:
- Identify login attempts made after a specific date
- Filter login attempts within a date range
- Find login attempts made during unusual hours
- Locate specific events by ID number

## Keywords and Operators Used

| Operator/Keyword | Purpose |
|---|---|
| `>` | Greater than |
| `>=` | Greater than or equal to |
| `<` | Less than |
| `<=` | Less than or equal to |
| `BETWEEN ... AND` | Filters within an inclusive range |

## What I Did

### Step 1 — Filtered by Date
Retrieved all login attempts made after May 9th 2022:
```sql
SELECT * FROM log_in_attempts
WHERE login_date > '2022-05-09';
```

Then included May 9th itself using >= :
```sql
SELECT * FROM log_in_attempts
WHERE login_date >= '2022-05-09';
```

### Step 2 — Filtered by Date Range
Used BETWEEN to find login attempts within a specific
date range:
```sql
SELECT * FROM log_in_attempts
WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11';
```
BETWEEN is inclusive meaning it includes both the start
and end dates in the results.

### Step 3 — Filtered by Time
Found login attempts made before 7:00 AM which could
indicate suspicious after-hours activity:
```sql
SELECT * FROM log_in_attempts
WHERE login_time < '07:00:00';
```

Then narrowed it to a specific one hour window:
```sql
SELECT * FROM log_in_attempts
WHERE login_time BETWEEN '06:00:00' AND '07:00:00';
```

### Step 4 — Filtered by Event ID
Retrieved all events with an ID of 100 or higher:
```sql
SELECT * FROM log_in_attempts
WHERE event_id >= '100';
```

Then narrowed to a specific range of event IDs:
```sql
SELECT * FROM log_in_attempts
WHERE event_id BETWEEN '100' AND '150';
```

## Understanding > vs >=

| Operator | Includes the value? | Example |
|---|---|---|
| `>` | No — excludes the value | `> '2022-05-09'` starts from May 10th |
| `>=` | Yes — includes the value | `>= '2022-05-09'` starts from May 9th |

## What I Learned
- How to use comparison operators to filter by dates,
  times, and numbers in SQL
- The difference between `>` and `>=` and why it matters
  when investigating specific dates
- BETWEEN is a cleaner way to filter ranges instead of
  combining two WHERE conditions
- Time based filtering is essential for identifying
  after hours login attempts which are a common indicator
  of compromised accounts
- Event IDs help analysts quickly locate and track
  specific security events in large datasets

## Why This Matters in Cybersecurity
Date and time filtering is one of the most critical SQL
skills for a SOC analyst. Real security investigations
almost always involve timeline analysis — figuring out
exactly when suspicious activity occurred. Being able to
quickly filter logs by date ranges, time windows, and
event IDs means you can reconstruct attack timelines
and identify anomalies efficiently instead of manually
searching through thousands of records.