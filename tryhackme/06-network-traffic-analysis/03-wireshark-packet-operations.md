# Wireshark: Packet Operations

## What I learned

- The Statistics menu helps analysts understand the overall traffic picture, including protocols, endpoints, conversations, and protocol-specific details such as DNS and HTTP traffic.
- There are two types of filters in Wireshark:
  - Capture filters  
    → applied before packets are captured
  - Display filters  
    → applied after packets have already been captured

---

## Key concepts

### Statistics Menu

- Resolved addresses  
  → identifies available IP addresses and DNS names

- Protocol Hierarchy  
  → displays protocols in a tree structure with packet counts and percentages

- Conversations  
  → shows communication between two specific endpoints

- Endpoints  
  → lists all communicating devices observed in the capture

- IPv4 / IPv6  
  → filters packets by IP version

- DNS statistics  
  → breaks down DNS traffic and queries

- HTTP statistics  
  → analyzes HTTP traffic details

---

## Why it matters in SOC

- Packet statistics and filtering help analysts quickly identify suspicious communication patterns and investigate network activity more efficiently.
- Filters reduce noise and make large PCAP files easier to analyze.

---

## Tools / activities used

- Used Wireshark to analyze a PCAP file
  - Investigated traffic using the Statistics menu
  - Applied display filters to inspect specific packets and protocols

---

## Personal notes

- Display filters make investigations significantly easier when dealing with large packet captures.
- The Statistics menu provides a useful overview before diving into packet-level analysis.
