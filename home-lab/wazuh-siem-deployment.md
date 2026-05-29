\# Home Lab Project: Wazuh SIEM Deployment

\*\*Date:\*\* May 2026

\*\*Project Type:\*\* Home Lab — Enterprise SIEM Setup

\*\*Status:\*\* Active



\## Project Overview

Successfully deployed a full Wazuh SIEM (Security Information

and Event Management) system on a Kali Linux VM, connecting

a physical Windows endpoint as a monitored agent. This project

mirrors real world enterprise security infrastructure used by

professional SOC teams daily.



\## Environment



| Component | Details |

|---|---|

| Host Machine | Lenovo ThinkPad T480s — Windows 11 |

| Hypervisor | Oracle VirtualBox |

| VM OS | Kali Linux 2026.1 |

| VM Resources | 6GB RAM, 80GB Disk |

| SIEM Platform | Wazuh (Open Source) |

| Monitored Endpoint | Windows 11 ThinkPad (Wazuh Agent) |



\## What I Built



\### Phase 1 — Environment Preparation

\- Enabled hardware virtualization (VT-x/VT-d) at BIOS level

&#x20; on Lenovo ThinkPad to support VM hypervisor operations

\- Configured VirtualBox VM with appropriate resources —

&#x20; increased RAM from 4GB to 6GB to meet Wazuh requirements

\- Verified disk allocation using GParted confirming 61GB

&#x20; available for SIEM deployment

\- Completed full Kali Linux system upgrade (1400+ packages)

&#x20; to ensure stable base for installation



\### Phase 2 — Wazuh Server Deployment

\- Deployed Wazuh server and dashboard components on Kali

&#x20; Linux VM using official Wazuh installation script

\- Configured Wazuh indexer for log storage and analysis

\- Initialized Wazuh dashboard web application accessible

&#x20; via HTTPS on local network

\- Verified successful installation with dashboard showing

&#x20; real time alert monitoring



\### Phase 3 — Windows Agent Deployment

\- Deployed Wazuh agent on Windows 11 host machine

\- Connected physical endpoint to Wazuh server for monitoring

\- Confirmed agent registration and data flow to dashboard



\## What Wazuh Does



| Feature | Description |

|---|---|

| Log Analysis | Collects and analyzes logs from all connected endpoints |

| Intrusion Detection | Detects suspicious activity and known attack patterns |

| Vulnerability Detection | Identifies known vulnerabilities on monitored systems |

| Configuration Assessment | Checks systems against security best practices |

| Malware Detection | Identifies indicators of compromise |

| Threat Hunting | Enables proactive searching for threats |



\## Challenges Overcome

\- Troubleshot VM resource constraints requiring RAM upgrade

\- Managed large scale package upgrade (1400+ packages) on

&#x20; Kali Linux with interrupted download handling

\- Resolved disk partition allocation issues using GParted

\- Configured BIOS level virtualization settings for optimal

&#x20; VM performance



\## Initial Findings

Upon deployment Wazuh immediately began detecting activity:

\- 125 Medium severity alerts (Rule level 7-11)

\- 107 Low severity alerts (Rule level 0-6)

\- 0 Critical or High severity alerts



This demonstrates the value of continuous monitoring —

security events are happening constantly on any system

and a SIEM makes them visible and actionable.



\## What I Learned

\- How to deploy and configure an enterprise grade SIEM

\- The architecture of SIEM systems — server, indexer,

&#x20; dashboard, and agent components

\- How Wazuh categorizes and prioritizes security alerts

&#x20; by severity level

\- How to troubleshoot Linux system issues including

&#x20; resource constraints and package management

\- The importance of proper system preparation before

&#x20; deploying security tools

\- How physical endpoints are connected to centralized

&#x20; security monitoring infrastructure



\## Technical Skills Demonstrated

\- Linux system administration

\- Virtual machine configuration and optimization

\- BIOS/firmware configuration

\- Disk partition management with GParted

\- Enterprise SIEM deployment and configuration

\- Security agent deployment on Windows endpoints

\- Security alert analysis and interpretation



\## Why This Matters in Cybersecurity

Wazuh is used by real companies worldwide as their primary

SIEM platform. The ability to:

\- Deploy and configure a SIEM from scratch

\- Connect endpoints for monitoring

\- Interpret security alerts by severity

\- Maintain a monitored environment



These are core SOC Analyst skills. This project demonstrates

hands on experience with enterprise security tools that most

entry level candidates only read about in textbooks.



\## Next Steps

\- Connect additional devices as Wazuh agents

\- Investigate and document existing alerts

\- Configure custom detection rules

\- Set up Telegram alerts for critical severity events

\- Integrate with existing Uptime Kuma monitoring setup

