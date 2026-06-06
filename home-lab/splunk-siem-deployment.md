\# Home Lab Project: Splunk SIEM Deployment \& Windows Log Analysis

\*\*Date:\*\* June 2026

\*\*Project Type:\*\* Home Lab — SIEM Configuration \& Security Analysis

\*\*Status:\*\* Active



\## Project Overview

Successfully deployed Splunk Enterprise on a Windows 11

ThinkPad laptop and configured it to ingest real Windows

security event logs. This creates a functional SIEM

environment for practicing security log analysis and

threat hunting techniques used daily by SOC analysts.



\## Environment



| Component | Details |

|---|---|

| Host Machine | Lenovo ThinkPad T480s — Windows 11 |

| SIEM Platform | Splunk Enterprise (Free License) |

| Data Sources | Windows Event Logs (Security, Application, System) |

| Events Ingested | 59,482 Security Events |

| Access URL | http://localhost:8000 |



\## What I Built



\### Step 1 — Splunk Installation

\- Downloaded Splunk Enterprise free version from

&#x20; splunk.com for Windows

\- Installed using the .msi installer on Windows 11

\- Configured admin credentials during setup

\- Accessed Splunk dashboard at http://localhost:8000



\### Step 2 — Data Ingestion Configuration

Configured Splunk to monitor local Windows Event Logs:

\- Navigated to Settings → Add Data → Monitor

\- Selected Local Event Logs as the data source

\- Enabled the following log channels:

&#x20; - Security — login attempts, privilege changes,

&#x20;   account management

&#x20; - Application — application errors and events

&#x20; - System — system level events and warnings

\- Splunk immediately began ingesting events upon

&#x20; configuration



\### Step 3 — Initial Data Verification

Ran initial search to confirm data was flowing:



index=main



Results confirmed 59,482 security events successfully

ingested from the local Windows machine — real security

data from the ThinkPad host.



\### Step 4 — Security Event Analysis

Used Splunk's Search and Reporting to investigate

Windows security events using EventCodes:



EventCode | Description | Security Relevance

4624 | Successful logon | Track authorized access

4625 | Failed logon attempt | Detect brute force attacks

4672 | Special privilege assigned | Detect privilege escalation

4720 | New user account created | Detect unauthorized accounts



Example searches used:



source="WinEventLog:Security" EventCode=4625

source="WinEventLog:Security" EventCode=4624

source="WinEventLog:Security" EventCode=4672



\## Current Home Lab SIEM Architecture



SIEM | Platform | Monitors | Location

Wazuh | Kali Linux VM | Windows endpoint and network | VM

Splunk | Windows 11 | Local Windows event logs | Host machine



Running two SIEMs simultaneously provides overlapping

coverage and demonstrates proficiency with multiple

industry standard security platforms.



\## What I Learned

\- How to install and configure Splunk Enterprise

&#x20; on a Windows system

\- How to ingest Windows Event Logs as a data source

&#x20; in Splunk

\- How Windows security EventCodes map to specific

&#x20; security relevant activities

\- How to write basic SPL queries to find specific

&#x20; security events

\- The difference between Splunk and Wazuh and how

&#x20; they complement each other

\- Why 59,000+ security events on a single machine

&#x20; shows the importance of SIEM tools



\## Key Security Event Codes Reference



EventCode | Event | Why Analysts Watch It

4624 | Successful Login | Baseline normal access patterns

4625 | Failed Login | Detect brute force or unauthorized access

4634 | Logoff | Track session duration

4648 | Explicit Credential Logon | Detect pass-the-hash attacks

4672 | Special Privileges Assigned | Detect privilege escalation

4720 | User Account Created | Detect unauthorized account creation

4732 | User Added to Group | Detect unauthorized privilege changes

4740 | Account Locked Out | Detect brute force attacks



\## Why This Matters in Cybersecurity

Splunk is one of the most widely used SIEM platforms

in enterprise environments and is listed as a required

or preferred skill in a large percentage of SOC Analyst

job postings. Being able to deploy and configure Splunk

independently, ingest and analyze real Windows security

logs, write SPL queries to find specific security events,

and interpret Windows EventCodes are core SOC analyst

skills practiced here in a real environment with actual

security data — not simulated or synthetic logs.



\## Next Steps

\- Create custom dashboards for security monitoring

\- Set up alerts for suspicious EventCodes

\- Practice threat hunting scenarios using SPL

\- Connect Splunk to Wazuh for unified visibility

\- Document specific security investigations as

&#x20; additional portfolio entries

