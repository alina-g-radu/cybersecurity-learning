# Wireshark - The Basics

## What I learned

- Wireshark is used to detect network problems, investigate security anomalies, and analyze protocol details.
- Wireshark is not an IDS; it is used for traffic analysis and investigation.
- Wireshark uses the OSI model to break down packets into layers.
- There is a useful rule for analysts:
  > "If you can click on it, you can filter and copy it."

---

## Key concepts

- Wireshark  
  → open-source, cross-platform packet analyzer used for capturing and inspecting network traffic and PCAP files

- Packet capture (PCAP)  
  → file containing captured network traffic for analysis

- Packet Details Pane  
  → section in Wireshark showing protocol layers and packet contents

---

## Why it matters in SOC

- Wireshark helps analysts investigate suspicious traffic and understand how attacks behave on the network.
- It is useful during incident response and traffic analysis.

---

## Tools / activities used

- Used wireshark to analyze a PCAP file
- Investigated packets and protocol details using Wireshark filters and packet inspection

---

## Personal notes

- Wireshark provides a very detailed view of network traffic and makes investigation much easier once filters are understood.
- Exporting packet bytes is a useful way to recover transferred files from captures.
