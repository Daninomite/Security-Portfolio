\# Home Lab Project: Enabling LAN Connectivity Between ThinkPad \& Beelink Mini S

\*\*Date:\*\* June 2026

\*\*Project Type:\*\* Home Lab — Networking \& Troubleshooting

\*\*Status:\*\* Completed



\## Project Overview

Successfully established full network communication between a Lenovo ThinkPad and a Beelink Mini S within a home lab environment. Both devices were connected via Ethernet to the same switch, but were initially unable to communicate or respond to ping requests.



This project documents the troubleshooting process, identification of the root cause, and the final configuration that enabled reliable IPv4 connectivity — a foundational skill for any cybersecurity or systems professional.



\---



\## Environment



| Component | Details |

|---|---|

| Device 1 | Lenovo ThinkPad — Windows 11 |

| Device 2 | Beelink Mini S — Windows 11 |

| Network | Ethernet → Switch → Router/Modem |

| Subnet | 10.0.0.0/24 |

| IPv4 Addresses | ThinkPad: 10.0.0.199, Beelink: 10.0.0.249 |

| Tools Used | Windows Firewall, Command Prompt (ping, ipconfig) |



\---



\## What I Built



\### Step 1 — Physical Network Setup

\- Connected both devices to the same unmanaged switch using Ethernet cables

\- Switch uplinked to the home router/modem

\- Verified both devices were using Ethernet (not Wi‑Fi)



\### Step 2 — IPv4 Verification

Checked IPv4 addresses on both systems:



ThinkPad: 10.0.0.199

Beelink: 10.0.0.249





Both devices were correctly assigned to the 10.0.0.x subnet, confirming they should be able to communicate.



Also identified a secondary address on the ThinkPad:



192.168.56.1





This was recognized as a VirtualBox Host‑Only Adapter, not part of the LAN, and safely ignored.



\### Step 3 — Initial Connectivity Test

Attempted to ping each device from the other:



ping 10.0.0.249

ping 10.0.0.199



Both resulted in: 

Request timed out.





This confirmed a communication block despite correct subnet configuration.



\### Step 4 — Root Cause Identification

Reviewed Windows Firewall settings and discovered:



\- Two ICMPv4 inbound rules existed on each machine:

\- File and Printer Sharing (Echo Request – ICMPv4-In) — Domain

\- File and Printer Sharing (Echo Request – ICMPv4-In) — Private, Public



The network profile in use was Private, but the Private/Public ICMP rule was disabled, preventing ping responses.



\### Step 5 — Firewall Rule Fix

Enabled the correct inbound rule on both devices:



\- Echo Request – ICMPv4-In (Private)

\- Echo Request – ICMPv4-In (Public)



This allowed ICMP traffic (ping) across the LAN.



\### Step 6 — Successful Connectivity Test

Re‑ran ping tests:



Reply from 10.0.0.249: bytes=32 time<1ms TTL=128

Reply from 10.0.0.249: bytes=32 time<1ms TTL=128

Reply from 10.0.0.249: bytes=32 time<1ms TTL=128

Reply from 10.0.0.249: bytes=32 time<1ms TTL=128





Both devices successfully communicated over IPv4.



\---



\## Final Home Lab Network Architecture



| Device | Role | IPv4 | Status |

|---|---|---|---|

| ThinkPad | Primary workstation, SIEM host, Kali VM | 10.0.0.199 | Connected |

| Beelink Mini S | Secondary node for offloading workloads | 10.0.0.249 | Connected |

| VirtualBox Adapter | Host‑only VM network | 192.168.56.1 | Isolated (expected) |



This establishes a functional multi‑node home lab ready for SIEM, Wazuh, Splunk, Proxmox, or distributed security tooling.



\---



\## What I Learned

\- How to identify and compare IPv4 subnets

\- How Windows network profiles affect firewall behavior

\- How ICMP (ping) is controlled by Windows Firewall

\- How to enable inbound ICMPv4 rules for LAN communication

\- How to differentiate physical network adapters from virtual adapters

\- Why connectivity can fail even when devices share the same subnet

\- How to validate network paths using ping and ipconfig



\---



\## Why This Matters in Cybersecurity

Network troubleshooting is a core skill for SOC analysts, penetration testers, and system administrators.

Being able to:



\- Diagnose connectivity failures

\- Understand subnets and routing

\- Work with Windows Firewall

\- Validate communication between nodes



…is essential for building and maintaining real‑world security environments.



This project demonstrates practical, hands‑on experience with foundational networking concepts — the kind used daily in enterprise environments.



\---



\## Next Steps

\- Assign static IPs to stabilize the lab

\- Move Splunk or Wazuh to the Beelink to offload ThinkPad resources

\- Install Proxmox on the Beelink for VM orchestration

\- Build a multi‑node SIEM environment

\- Document additional troubleshooting and configuration projects for GitHub



