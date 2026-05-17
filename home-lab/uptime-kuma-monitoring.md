\# Home Lab Project: Network Monitoring with Uptime Kuma

\*\*Date:\*\* May 2026

\*\*Project Type:\*\* Home Lab Setup

\*\*Status:\*\* Active and Expanding



\## Project Overview

Built a self-hosted network monitoring system on a Kali

Linux VM that sends real time alerts to my phone when

monitored services or devices go down. This project

demonstrates practical skills in virtualization, Docker,

network monitoring, and alerting systems used in real

SOC environments.



\## Tools and Technologies Used



| Tool | Purpose |

|---|---|

| VirtualBox | Virtualization platform hosting Kali Linux |

| Kali Linux | Primary security-focused operating system |

| Docker | Container platform for running Uptime Kuma |

| Uptime Kuma | Self-hosted monitoring and alerting dashboard |

| Telegram | Mobile notification delivery via custom bot |

| Wireshark | Network traffic analysis and packet capture |



\## What I Built



\### Step 1 — Virtualization Environment

Set up a Kali Linux VM using VirtualBox on a Windows

ThinkPad laptop with virtualization enabled at the

BIOS level. Configured the VM in bridge mode to allow

it to monitor real home network traffic.



\### Step 2 — Docker Installation

Installed Docker on Kali Linux to run containerized

applications:

```bash

sudo apt update

sudo apt install docker.io -y

sudo systemctl start docker

sudo systemctl enable docker

```



\### Step 3 — Uptime Kuma Deployment

Deployed Uptime Kuma in a Docker container with

persistent storage and automatic restart:

```bash

sudo docker run -d --restart=always -p 3001:3001 \\

\-v uptime-kuma:/app/data --name uptime-kuma \\

louislam/uptime-kuma:1

```

Accessed the dashboard at http://localhost:3001



\### Step 4 — Telegram Bot Setup

Created a custom Telegram bot for phone notifications:

\- Used BotFather in Telegram to create a new bot

\- Retrieved bot API token from BotFather

\- Found Chat ID using the Telegram API

\- Connected bot to Uptime Kuma notification system

\- Tested and confirmed alerts deliver to phone



\### Step 5 — Configured Monitors

Set up the following monitors with Telegram alerts:



| Monitor | Type | Status |

|---|---|---|

| Google | HTTP(s) | ✅ Active |

| Home Router (10.0.0.1) | Ping | ✅ Active |



\### Step 6 — Network Traffic Analysis

Used Wireshark in Kali Linux to analyze real home

network traffic including:

\- DNS queries showing devices looking up websites

\- MDNS traffic from smart TV (Hisense)

\- ARP traffic from Amazon Echo devices

\- IPv4 and IPv6 traffic identification



\## Key Concepts Demonstrated

\- \*\*Containerization\*\* — running applications in Docker

\- \*\*Network monitoring\*\* — tracking uptime of services

&#x20; and devices

\- \*\*Alerting systems\*\* — real time phone notifications

\- \*\*Network analysis\*\* — capturing and reading network

&#x20; traffic with Wireshark

\- \*\*Virtualization\*\* — running Kali Linux in VirtualBox

\- \*\*BIOS configuration\*\* — enabling hardware

&#x20; virtualization for VM support



\## What I Learned

\- How to deploy and manage Docker containers in Linux

\- How to set up a self-hosted monitoring solution

\- How to create and configure Telegram bots for alerts

\- How to read and analyze network traffic in Wireshark

\- The difference between DNS, MDNS, and ARP traffic

\- How smart home devices communicate on a network

\- Why network monitoring is critical in SOC environments



\## Why This Matters in Cybersecurity

Network monitoring is a core responsibility of SOC

analysts. Being able to:

\- Deploy monitoring tools in a Linux environment

\- Configure real time alerting systems

\- Analyze network traffic for anomalies

\- Identify devices and their behavior on a network



These are all skills used daily in professional security

operations. This home lab project demonstrates hands on

experience with the same concepts and tools used in

enterprise SOC environments.



\## Future Plans

\- Add more monitors for home network devices

\- Set up Suricata or Snort IDS for intrusion detection

\- Configure alerts for suspicious network behavior

\- Expand Wireshark analysis skills

\- Document network baseline for anomaly detection

