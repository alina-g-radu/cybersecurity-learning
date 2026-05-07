# Network Traffic Basics

## What I learned

- Network traffic should be analyzed to monitor performance, detect abnormalities, and investigate suspicious internal or external communication.
- Each layer of the TCP/IP model contains important network information:
  - Application layer  
    → application headers + payload (data), varies depending on protocol

  - Transport layer  
    → transport headers (usually TCP or UDP)

  - Internet layer  
    → source IP, destination IP, and TTL

  - Link layer  
    → physical addressing information (MAC addresses, etc.)

- There are two main sources of network traffic:
  - intermediary devices (routers, switches)
  - endpoint devices (laptops, servers, etc.)

- Network traffic flow types:
  - North-South traffic → between LAN and WAN (internal ↔ external)
  - East-West traffic → within the same LAN (internal communication)

---

## Key concepts

- Network Traffic Analysis (NTA)  
  → process of capturing, inspecting, and analyzing network data as it flows through a network

- Network tap  
  → physical device placed inline to copy network traffic for analysis

- Port mirroring  
  → software-based method to copy traffic from one network port to another for monitoring

---

## Why it matters in SOC

- Helps detect suspicious or malicious activity in the network.
- Supports incident response by allowing analysts to reconstruct attacks.
- Helps validate and investigate alerts from security tools.

---

## Tools / activities used

- Analyzed network traffic and identified correct placement of monitoring tools (tap / mirroring)

---

## Personal notes

- Understanding network traffic flow makes it much easier to detect unusual behavior in a SOC environment.
