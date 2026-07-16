# Day 03 - TCP, Wireshark & Network Traffic Fundamentals

## Overview

On Day 3 of my SOC Analyst learning journey, I explored fundamental networking concepts by capturing and analyzing live network traffic using Wireshark.

This lab focused on understanding how devices communicate over a network, analyzing TCP connections, DNS queries, ICMP packets, and ARP communication.

---

## Objectives

- Install and configure Wireshark
- Capture live network traffic
- Understand TCP Three-Way Handshake
- Analyze TCP Flags
- Observe DNS Query and Response
- Analyze ICMP Echo Request and Reply
- Understand ARP Request and Response
- Practice basic Wireshark display filters

---

## Tools Used

- Wireshark 4.6.7
- Windows 10
- Command Prompt
- Home Wi-Fi Network

---

## Packet Capture

A live packet capture was performed using the Wi-Fi interface.

Capture File:

```
captures/day03-first-capture.pcapng
```

---

# TCP Three-Way Handshake

A TCP connection is established through three steps:

```
Client                  Server

SYN      ------------>

         <------------      SYN, ACK

ACK      ------------>
```

This process ensures both devices are ready to communicate before data transmission begins.

---

# TCP Flags

The following TCP flags were observed during analysis:

| Flag | Meaning |
|------|---------|
| SYN | Initiates a new TCP connection |
| SYN-ACK | Acknowledges the SYN request |
| ACK | Confirms successful communication |
| FIN | Gracefully closes a connection |
| RST | Immediately resets a connection |

---

# DNS Analysis

Display Filter

```
dns
```

Observations

- DNS queries for Google
- DNS queries for ChatGPT
- DNS responses from the local DNS server
- Standard Query and Standard Response packets

Screenshot

```
screenshots/03-dns-filter.png
```

---

# ICMP Analysis

Display Filter

```
icmp
```

A ping request was sent to Google.

Command Used

```cmd
ping google.com
```

Observed

- Echo Request
- Echo Reply
- Successful communication

Screenshots

```
screenshots/04-icmp-filter.png
screenshots/09-ping-command.png
```

---

# TCP Packet Analysis

Display Filter

```
tcp
```

Observed

- HTTPS communication
- TLS traffic
- Client Hello
- TCP sessions
- ACK packets

Screenshot

```
screenshots/05-tcp-filter.png
```

---

# TCP SYN Packets

Display Filter

```
tcp.flags.syn == 1
```

Observed

- Connection initiation packets

Screenshot

```
screenshots/06-tcp-syn.png
```

---

# TCP SYN-ACK Packets

Display Filter

```
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

Observed

- Server responses during TCP connection establishment

Screenshot

```
screenshots/07-tcp-syn-ack.png
```

---

# TCP ACK Packets

Display Filter

```
tcp.flags.ack == 1 && tcp.flags.syn == 0
```

Observed

- Normal data acknowledgement packets

Screenshot

```
screenshots/08-tcp-ack.png
```

---

# ARP Analysis

Display Filter

```
arp
```

Observed

- ARP Request
- ARP Reply
- IP to MAC Address resolution

Example

```
Who has 192.168.110.149?

192.168.110.149 is at 00:e0:4d:00:32:4b
```

Screenshot

```
screenshots/10-arp-filter.png
```

---

# Wireshark Display Filters Used

```text
dns

icmp

tcp

arp

tcp.flags.syn == 1

tcp.flags.syn == 1 && tcp.flags.ack == 1

tcp.flags.ack == 1 && tcp.flags.syn == 0
```

---

# Screenshots

| Screenshot | Description |
|------------|-------------|
| 01-wireshark-home.png | Wireshark Home Screen |
| 02-live-packet-capture.png | Live Packet Capture |
| 03-dns-filter.png | DNS Query Analysis |
| 04-icmp-filter.png | ICMP Request & Reply |
| 05-tcp-filter.png | TCP Traffic |
| 06-tcp-syn.png | SYN Packets |
| 07-tcp-syn-ack.png | SYN-ACK Packets |
| 08-tcp-ack.png | ACK Packets |
| 09-ping-command.png | Ping Command Output |
| 10-arp-filter.png | ARP Request & Reply |

---

# Key Learnings

- Installed and configured Wireshark
- Captured live network traffic
- Understood the TCP Three-Way Handshake
- Learned the purpose of common TCP flags
- Analyzed DNS requests and responses
- Observed ICMP Echo Request and Reply
- Learned how ARP resolves IP addresses to MAC addresses
- Practiced using common Wireshark display filters
- Saved and documented packet captures for future analysis

---

# Repository Structure

```
Day03-TCP-Wireshark-Fundamentals
│
├── README.md
│
├── captures
│   └── day03-first-capture.pcapng
│
└── screenshots
    ├── 01-wireshark-home.png
    ├── 02-live-packet-capture.png
    ├── 03-dns-filter.png
    ├── 04-icmp-filter.png
    ├── 05-tcp-filter.png
    ├── 06-tcp-syn.png
    ├── 07-tcp-syn-ack.png
    ├── 08-tcp-ack.png
    ├── 09-ping-command.png
    └── 10-arp-filter.png
```

---

## Next Steps

- Windows Event Logs
- Sysmon
- Microsoft Defender for Endpoint
- Microsoft Sentinel
- Kusto Query Language (KQL)
- Splunk
- Detection Engineering
- Threat Hunting

---

## Author

**Belal Ansari**

GitHub: https://github.com/ibelalansari

LinkedIn: https://linkedin.com/in/ibelalansari

SOC Learning Journey Repository:
https://github.com/ibelalansari/SOC-Learning-Journey
