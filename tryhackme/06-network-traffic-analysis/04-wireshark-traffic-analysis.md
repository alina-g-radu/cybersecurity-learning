# Wireshark: Traffic Analysis

## What I learned

- Network scanning and protocol analysis can be identified directly from packet behavior in Wireshark.
- Different scan types produce different packet patterns, which can be used for detection and investigation.

---

## Key concepts

### TCP Connect Scan

- Uses full three-way handshake
- Uses `nmap -sT`
- Works without privileged access
- Typically larger packets (>1024 bytes)

- Open port:
  SYN → SYN/ACK → ACK

- Closed port:
  SYN → RST/ACK

- Wireshark filter:
  `tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024`

---

### SYN Scan

- Does NOT complete full handshake
- Uses `nmap -sS`
- Requires privileged access
- More stealthy than TCP connect scan

- Open port:
  SYN → SYN/ACK → RST

- Closed port:
  SYN → RST/ACK

- Wireshark filter:
  `tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size <= 1024`

---

### UDP Scan

- No handshake process
- Uses `nmap -sU`
- Open port → no response
- Closed port → ICMP error response

- Closed UDP port:
  ICMP Type 3, Code 3 (Destination unreachable / Port unreachable)

- Wireshark filter:
  `icmp.type==3 and icmp.code==3`

---

### ARP (Address Resolution Protocol)

- Used to map IP addresses to MAC addresses in local networks
- Works only within the local network (not routable)
- No authentication (can be abused)

Common patterns:

- Request / Reply
- Gratuitous ARP
- ARP announcements

ARP poisoning (MITM attack):

- Attacker sends fake ARP replies
- Goal is to manipulate IP ↔ MAC mapping
- Used for traffic interception or sniffing

Suspicious indicator:

- Multiple ARP replies for the same IP address

---

### DHCP (Dynamic Host Configuration Protocol)

- Automatically assigns IP addresses and network configuration to devices

---

### NetBIOS

- Allows communication between applications on different hosts in a LAN
- Common in Windows environments

---

### Kerberos

- Authentication protocol used in Windows domains
- Provides secure identity verification over untrusted networks

---

### ICMP (Internet Control Message Protocol)

- Used for diagnostics and network troubleshooting (e.g., ping)
- High ICMP traffic or abnormal packet sizes may indicate tunneling

---

### DNS (Domain Name System)

- Converts domain names into IP addresses
- Essential for normal network communication

---

### Traffic tunneling

- Technique used to hide data inside allowed protocols
- Also known as port forwarding in some contexts
- Can be used for legitimate or malicious purposes

---

## Why it matters in SOC

- Network traffic analysis helps detect scanning, reconnaissance, and attack behavior in real time.
- Understanding scan patterns helps SOC analysts identify malicious activity early in the attack chain.

---

## Tools / activities used

- Practiced analyzing multiple PCAP files using Wireshark
- Identified scan types based on packet behavior and filters
