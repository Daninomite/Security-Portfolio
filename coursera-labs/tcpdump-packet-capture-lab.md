\# Lab Write-Up: Capturing My First Packet with tcpdump

\*\*Date:\*\* July 2026

\*\*Platform:\*\* Coursera — Google Cybersecurity Certificate

\*\*Topic:\*\* Network Packet Capture Using tcpdump



\## Objective

Use tcpdump to capture live network traffic from the

command line, save captures to a file, and filter

packet data for analysis — a fundamental skill for

network forensics and security investigations.



\## Tools Used

tcpdump — command line packet analyzer

curl — command line tool for making web requests

ifconfig — network interface configuration tool



\## What I Did



\### Step 1 — Identified Available Network Interfaces

Used ifconfig to view all available network interfaces

and their current configuration:

sudo ifconfig



This shows all network interfaces available for

capturing traffic including their IP addresses,

MAC addresses, and connection status.



Then used tcpdump to list all available capture

interfaces:

sudo tcpdump -D



This lists every interface tcpdump can capture on

numbered for easy reference.



\### Step 2 — Captured Live Network Traffic

Used tcpdump to capture live traffic on the eth0

interface in verbose mode, limited to 5 packets:

sudo tcpdump -i eth0 -v -c5



Breaking down the flags:

\-i eth0 = capture on eth0 interface

\-v = verbose output, more packet detail

\-c5 = stop after capturing 5 packets



\### Step 3 — Saved Traffic to a Packet Capture File

Captured 9 packets on port 80 and saved to a .pcap

file for later analysis:

sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap \&



Breaking down the flags:

\-i eth0 = capture on eth0 interface

\-nn = no hostname or port name resolution

\-c9 = stop after 9 packets

port 80 = only capture HTTP traffic

\-w capture.pcap = write output to file

\& = run in background



Then generated HTTP traffic to capture:

curl opensource.google.com



Verified the capture file was created:

ls -l capture.pcap



\### Step 4 — Filtered and Read the Packet Capture File

Read the saved capture file in verbose mode:

sudo tcpdump -nn -r capture.pcap -v



Breaking down the flags:

\-nn = disable name resolution

\-r capture.pcap = read from file

\-v = verbose output



Then read the capture displaying raw hex data:

sudo tcpdump -nn -r capture.pcap -x



The -x flag displays packet contents in hexadecimal

format — useful for examining raw payload data.



\## Commands Reference



| Command | Purpose |

|---|---|

| sudo ifconfig | View network interfaces and IP info |

| sudo tcpdump -D | List all available capture interfaces |

| sudo tcpdump -i eth0 -v -c5 | Capture 5 packets verbosely on eth0 |

| sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap \& | Capture 9 HTTP packets to file |

| curl opensource.google.com | Generate HTTP traffic to capture |

| ls -l capture.pcap | Verify capture file was created |

| sudo tcpdump -nn -r capture.pcap -v | Read capture file verbosely |

| sudo tcpdump -nn -r capture.pcap -x | Read capture file in hex format |



\## Understanding tcpdump Flags



| Flag | Meaning |

|---|---|

| -i | Specify network interface |

| -v | Verbose — more packet detail |

| -c | Count — stop after N packets |

| -nn | No name resolution for IPs or ports |

| -w | Write output to file |

| -r | Read from file |

| -x | Display in hexadecimal format |

| \& | Run process in background |

| port 80 | Filter for specific port |



\## What I Learned

\- How to identify available network interfaces using

&#x20; ifconfig and tcpdump -D

\- How to capture live network traffic from the command

&#x20; line using tcpdump

\- The difference between capturing to screen vs saving

&#x20; to a .pcap file for later analysis

\- How the -nn flag prevents DNS resolution during

&#x20; capture which speeds up the process

\- How to use curl to generate web traffic for capture

\- How to read and filter saved packet capture files

\- How hexadecimal output with -x reveals raw packet

&#x20; payload data

\- Why running tcpdump with \& in background allows

&#x20; simultaneous traffic generation with curl

\- How tcpdump and Wireshark complement each other —

&#x20; tcpdump captures from command line, Wireshark

&#x20; analyzes graphically



\## tcpdump vs Wireshark



| Feature | tcpdump | Wireshark |

|---|---|---|

| Interface | Command line | Graphical GUI |

| Best for | Remote servers, scripts | Visual analysis |

| Output | Text or .pcap file | Visual packets |

| .pcap files | Yes | Yes |

| Filters | BPF syntax | Display filters |



Both tools read the same .pcap file format — you can

capture with tcpdump and analyze in Wireshark!



\## Why This Matters in Cybersecurity

tcpdump is an essential tool for SOC analysts because:

\- Many servers have no graphical interface — only CLI

\- Captures can be taken remotely via SSH

\- Scripted captures can run automatically on schedules

\- .pcap files can be shared with team members for

&#x20; collaborative investigation

\- Faster and lighter than running Wireshark on servers

\- Used in incident response to capture evidence quickly



Being comfortable with both tcpdump and Wireshark

gives a security analyst complete flexibility in any

environment whether graphical or command line only.

