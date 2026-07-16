# Wireshark Lab 01 - HTTPS Traffic Analysis

![Platform](https://img.shields.io/badge/Platform-Windows%2011-blue)
![Tool](https://img.shields.io/badge/Tool-Wireshark-blue)
![Protocol](https://img.shields.io/badge/Protocol-DNS%20%7C%20TCP%20%7C%20TLS-green)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-success)
![License](https://img.shields.io/badge/License-MIT-yellow)

A beginner-friendly network traffic analysis lab demonstrating how an HTTPS connection is established and secured using Wireshark.

---

## Table of Contents

* [Overview](#overview)
* [Objectives](#objectives)
* [Lab Environment](#lab-environment)
* [Requirements](#requirements)
* [Scenario](#scenario)
* [Methodology](#methodology)
* [Analysis](#analysis)

  * [DNS Resolution](#1-dns-resolution)
  * [TCP Three-Way Handshake](#2-tcp-three-way-handshake)
  * [TLS Handshake](#3-tls-handshake)
  * [Source and Destination Ports](#4-source-and-destination-ports)
  * [Observed Protocols](#5-observed-protocols)
* [Evidence](#evidence)
* [Key Takeaways](#key-takeaways)
* [References](#references)

---

# Overview

This laboratory demonstrates the fundamental stages of an HTTPS connection using Wireshark.

The captured traffic includes DNS name resolution, TCP session establishment, TLS negotiation, and encrypted application traffic.

The purpose of this project is to practice packet analysis while developing practical skills commonly required in SOC, Blue Team, and Network Security roles.

---

# Objectives

* Capture live network traffic.
* Identify DNS queries and responses.
* Analyze the TCP Three-Way Handshake.
* Observe the TLS handshake process.
* Identify source and destination IP addresses.
* Analyze TCP ports.
* Understand the role of each protocol during an HTTPS connection.

---

# Lab Environment

| Component        | Details             |
| ---------------- | ------------------- |
| Operating System | Windows 11          |
| Browser          | Google Chrome       |
| Capture Tool     | Wireshark 4.x       |
| Network          | Home Network        |
| Website          | https://pt.wikipedia.org/ |

---

# Requirements

* Wireshark installed
* Internet connection
* Administrator privileges (recommended)
* Basic knowledge of networking concepts

---

# Scenario

A user opens a secure website in a web browser.

The objective is to capture and analyze every stage of the communication between the client and the remote server.

---

# Methodology

1. Start packet capture.
2. Open an Incognito browser window.
3. Visit https://example.com.
4. Wait for the page to load.
5. Stop the capture.
6. Apply protocol-specific filters.
7. Analyze the captured packets.
8. Document the findings.

---

# Analysis

## 1. DNS Resolution

The client first contacted a DNS server to resolve the domain name into an IPv4 address.

### Wireshark Filter

```text
dns
```

### Findings

* Standard Query
* Standard Query Response
* Resolved IP Address

### Screenshot

```
images/dns.png
```

---

## 2. TCP Three-Way Handshake

The TCP connection was established using the standard three-step handshake.

### Wireshark Filter

```text
tcp.flags.syn == 1
```

### Packets Observed

| Packet  | Description                    |
| ------- | ------------------------------ |
| SYN     | Client requests a connection   |
| SYN-ACK | Server accepts the connection  |
| ACK     | Client confirms the connection |

### Screenshot

```
images/handshake.png
```

---

## 3. TLS Handshake

After TCP was established, the client and server negotiated a secure encrypted session.

### Wireshark Filter

```text
tls
```

### Messages Observed

* Client Hello
* Server Hello
* Certificate
* Application Data

### Screenshot

```
images/tls.png
```

---

## 4. Source and Destination Ports

The capture identified:

| Item             | Value          |
| ---------------- | -------------- |
| Source Port      | Ephemeral Port |
| Destination Port | 443            |

Port **443** confirms HTTPS communication.

### Screenshot

```
images/ports.png
```

---

## 5. Observed Protocols

| Protocol | Purpose                |
| -------- | ---------------------- |
| DNS      | Domain Name Resolution |
| TCP      | Reliable Transport     |
| TLS      | Secure Encryption      |
| HTTP/2   | Web Data Transfer      |

---

# Evidence

Project structure:

```text
wireshark-lab-01/
│
├── README.md
├── captures/
│   └── https-analysis.pcapng
│
├── images/
│   ├── dns.png
│   ├── handshake.png
│   ├── tls.png
│   └── ports.png
│
└── LICENSE
```

---

# Key Takeaways

* Understood how DNS resolves hostnames.
* Identified the TCP Three-Way Handshake.
* Observed the TLS negotiation process.
* Identified encrypted HTTPS traffic.
* Practiced using Wireshark display filters.
* Improved packet analysis skills.

---

# References

* Wireshark Official Documentation
* RFC 793 – Transmission Control Protocol (TCP)
* RFC 8446 – TLS 1.3
* RFC 1035 – Domain Name System (DNS)

---

**Disclaimer**

This capture was performed exclusively on my own device and network for educational purposes. No unauthorized systems or third-party networks were analyzed.
