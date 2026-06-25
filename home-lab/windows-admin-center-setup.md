\# Home Lab Project: Windows Admin Center Gateway Setup

\*\*Date:\*\* June 2026

\*\*Project Type:\*\* Home Lab — Remote Server Management

\*\*Status:\*\* In Progress — Reinstall Planned



\## Project Overview

Configured and troubleshot Windows Admin Center (WAC) on

the Beelink Mini S home server to enable remote management

from the ThinkPad workstation. This project demonstrates

real world enterprise server administration skills including

service diagnosis, remote access configuration, and

systematic troubleshooting methodology.



\## Environment



| Component | Details |

|---|---|

| Server | Beelink Mini S — Windows 11 Pro |

| Workstation | Lenovo ThinkPad T480s — Windows 11 |

| Target Software | Windows Admin Center (WAC) |

| Target Port | 6516 |

| Auth Method | Windows Authentication |

| Connection | Local network via ethernet switch |



\## What is Windows Admin Center?



Windows Admin Center is Microsoft's browser-based server

management tool used in enterprise environments to:

\- Remotely manage Windows servers and workstations

\- Monitor system performance and event logs

\- Manage storage, networking, and services

\- Access PowerShell remotely

\- View and manage running processes and services



\## Problem Statement



After installing WAC on the Beelink server remote access

from the ThinkPad failed consistently. Symptoms included:



\- Remote browser unable to load the WAC page

\- netstat -an | findstr 6516 showed no active listener

\- Test-NetConnection to port 6516 failed

\- Service ServerManagementGateway did not exist

\- Local access worked but remote access did not



\## Troubleshooting Process



\### Step 1 — Initial Diagnosis

Used Windows networking commands to verify service

state and port binding:



netstat -an | findstr 6516

Result: No listener found



Test-NetConnection -ComputerName BEelink-IP -Port 6516

Result: Connection failed



Get-Service ServerManagementGateway

Result: Service did not exist — critical finding



\### Step 2 — Root Cause Identified

Determined that the WAC v2 installer forces desktop

mode instead of true gateway mode.



Desktop mode vs Gateway mode:



| Feature | Desktop Mode | Gateway Mode |

|---|---|---|

| ServerManagementGateway service | Not created | Created |

| Port binding | Not bound | Binds to port |

| Remote access | Not supported | Fully supported |

| Event log access | Errors | Full access |

| Use case | Local only | Enterprise/remote |



Key indicator — installer showed external/internal

port range screen — signature of v2 desktop mode.



\### Step 3 — Reinstallation Attempt

Attempted reinstallation with correct settings:

\- Remote access enabled

\- Port 6516 specified

\- Windows Authentication selected

\- Allow access to any computer

\- HTTP for WinRM

\- Automatic updates enabled



Result: WAC UI loaded but ServerManagementGateway

service still absent — v2 installer forced desktop

mode regardless of selected options.



\### Step 4 — Event Log Errors

After installation event logs showed:

RemoteException: The source was not found

Inaccessible logs: Security



Confirmed WAC running in desktop mode without proper

gateway service permissions.



\## Root Cause Summary



The WAC v2 installer does not support true gateway mode.

It repeatedly installs in desktop mode which:

\- Skips ServerManagementGateway service creation

\- Does not bind the specified port for remote access

\- Blocks Security event log access

\- Appears functional locally but fails remotely



\## Resolution Plan



Complete reinstall using classic WAC MSI installer:

https://aka.ms/WACDownload



Steps:

1\. Uninstall current WAC from Beelink

2\. Download classic MSI installer

3\. Run installer selecting gateway mode

4\. Configure port 6516 with Windows Authentication

5\. Enable remote access and WinRM over HTTP

6\. Verify ServerManagementGateway service exists

7\. Fix Security log permissions if needed

8\. Test remote connectivity from ThinkPad



Verification commands post-install:

Get-Service ServerManagementGateway

netstat -an | findstr 6516

Test-NetConnection -ComputerName Beelink-IP -Port 6516



\## What I Learned

\- Difference between WAC desktop mode and gateway mode

\- How to use netstat and Test-NetConnection to diagnose

&#x20; port binding and remote connectivity issues

\- Why ServerManagementGateway service is the key

&#x20; indicator of successful gateway installation

\- How to read Windows event log errors to confirm

&#x20; service configuration problems

\- Importance of using correct installer version for

&#x20; enterprise software deployment

\- Systematic troubleshooting — isolate, diagnose,

&#x20; identify root cause, plan resolution



\## Why This Matters in Cybersecurity

Remote server management is a core skill for SOC analysts

and security engineers. Troubleshooting a failed WAC

gateway installation demonstrates real world server

administration skills including service diagnosis, port

analysis, Windows authentication configuration, and

remote access troubleshooting — all directly applicable

to SOC and IT security roles.



\## Next Steps

\- Complete reinstall using classic MSI installer

\- Verify stable remote access from ThinkPad

\- Configure Security event log access permissions

\- Document successful gateway configuration

\- Integrate WAC alerts with Wazuh and Splunk

