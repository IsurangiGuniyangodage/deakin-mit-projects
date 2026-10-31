# SIT716: Network Security Labs

**Unit:** Computer Networks and Security, Deakin University
**Type:** Individual lab investigations

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
I used Mininet, Wireshark and virtual machines to capture real traffic, compare normal and abnormal behaviour, and be clear about what the evidence does and doesn't prove.

## Main investigation: DHCP starvation attack
- **Baseline:** captured one complete DHCP Discover, Offer, Request and ACK exchange. The client got `10.0.0.101`, the transaction ID linked all four messages, and it took about **3.0 seconds**, not the roughly one second I predicted.
- **Attack:** in an isolated three-host Mininet network with an **eleven-address pool**, spoofed client identities used up all **11 of 11 leases**.
- **Result:** the legitimate host got no DHCP Offer. Filtering its transaction in Wireshark showed **25 Discover packets with no Offer**.
- **Why this is convincing:** I combined the lease file, the packet captures and the unanswered requests as evidence, rather than treating a high packet count as proof.
- **Defence:** monitoring lease use and client identity patterns, and controlling DHCP requests at the network edge.

## Other labs
- **Addressing and routing:** split a /24 into two /25 networks, and compared OSPF path cost with RIP hop count using captured TTL and protocol fields.
- **IP spoofing and ICMP:** showed that a forged source IP can redirect ICMP replies, and told ARP apart from traffic inside IP.
- **TCP:** captured the three-way handshake and explored a SYN flood, after fixing VM addressing problems first.
- **Web and DNS:** a fresh GitHub Pricing page load produced 83 requests, used HTTP/2 and TLS 1.3. I also queried DNS records, including MX and SOA.
- **Tunnelling:** compared direct HTTP, IP-in-IP and SSH local forwarding to show that encapsulation is not encryption. Where lab connections timed out, I checked the packets against the command output and reported them as intermittent lab connectivity, not as application failures.

## Skills shown
Packet analysis, protocol behaviour, attack and defence reasoning, careful evidence-based conclusions.

**Tools:** Mininet, Open vSwitch, Wireshark, VirtualBox, Ubuntu.
