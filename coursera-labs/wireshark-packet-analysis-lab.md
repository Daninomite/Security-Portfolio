\# Lab Write-Up: Analyzing Packets with Wireshark

\*\*Date:\*\* July 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Packet Capture Analysis and Display Filters



\## Objective

Use Wireshark to open and analyze a packet capture file,

examine individual packet details across protocol layers,

and apply display filters to isolate specific network

traffic for investigation.



\## Tools Used

Wireshark — network protocol analyzer



\## What I Did



\### Step 1 — Opened Packet Capture File

Opened a .pcap file in Wireshark and explored the

basic graphical user interface including:

\- Packet list pane — shows all captured packets

\- Packet details pane — shows protocol breakdown

\- Packet bytes pane — shows raw hex and ASCII data

\- Filter bar — for applying display filters



\### Step 2 — Examined a Single Packet in Detail

Opened a detailed view of an individual packet and

explored the various protocol and data layers:

\- Ethernet II — Layer 2 MAC addresses

\- Internet Protocol (IP) — Layer 3 source/destination IPs

\- Transmission Control Protocol (TCP) — Layer 4 port info

\- Application layer data — payload content



This demonstrates how network data is encapsulated

in layers following the OSI model.



\### Step 3 — Applied Display Filters

Used Wireshark display filters to isolate specific

packets based on defined criteria rather than manually

searching through thousands of packets.



\### Step 4 — Filtered UDP DNS Traffic

Applied filters to examine DNS traffic over UDP port 53

to inspect domain name lookup requests and responses.

DNS uses UDP port 53 for standard queries — filtering

for this traffic reveals every domain name lookup

made during the capture period.



Filter used: udp.port==53



\### Step 5 — Filtered TCP Payload Data

Applied TCP filters to search for specific text content

within packet payloads. Port 80 is standard HTTP traffic

— filtering for this reveals unencrypted web traffic.



Filter used: tcp.port==80



\## Filters Used



| Filter | Purpose |

|---|---|

| ip.src==142.250.1.139 | Show packets FROM this IP address |

| ip.dst==142.250.1.139 | Show packets TO this IP address |

| eth.addr==42:01:ac:15:e0:02 | Filter by MAC address |

| udp.port==53 | Filter DNS traffic |

| tcp.port==80 | Filter HTTP traffic |



\## Understanding the Filter Syntax



| Operator | Meaning | Example |

|---|---|---|

| == | Equals | ip.src==10.0.0.1 |

| != | Does not equal | ip.src!=10.0.0.1 |

| \&\& | AND both must match | ip.src==x \&\& tcp.port==80 |

| ip.src | Source IP address | ip.src==142.250.1.139 |

| ip.dst | Destination IP address | ip.dst==142.250.1.139 |

| eth.addr | Ethernet MAC address | eth.addr==42:01:ac:15:e0:02 |

| udp.port | UDP port number | udp.port==53 |

| tcp.port | TCP port number | tcp.port==80 |



\## What I Learned

\- How to navigate the Wireshark GUI and understand

&#x20; each pane's purpose

\- How network packets are structured in layers

&#x20; corresponding to the OSI model

\- How to apply display filters to isolate specific

&#x20; traffic types from large packet captures

\- The difference between filtering by IP source vs

&#x20; destination vs MAC address

\- Why DNS uses UDP port 53 and HTTP uses TCP port 80

\- How filtering for TCP port 80 can reveal unencrypted

&#x20; payload text demonstrating why HTTPS matters

\- How MAC address filtering differs from IP filtering

&#x20; and when each is useful in an investigation



\## Why This Matters in Cybersecurity

Packet analysis is a fundamental SOC analyst skill.

Real world use cases include:

\- Investigating suspicious network connections by

&#x20; filtering for specific IP addresses

\- Identifying C2 traffic by examining DNS lookups

&#x20; to unknown domains

\- Finding data exfiltration by examining outbound

&#x20; traffic volumes and destinations

\- Detecting unencrypted credentials in HTTP traffic

\- Reconstructing attack timelines from packet captures



Wireshark is used daily in incident response, threat

hunting, and network forensics investigations.

