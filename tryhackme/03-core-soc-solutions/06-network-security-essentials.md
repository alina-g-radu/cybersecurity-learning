# Title

## What I learned

- Workstations are the most common entry point for attackers because they are often less monitored
- File and Database Servers are targeted by ransomware operator
- Application Servers are also highly targeted because they are externally facing
- Active Directories are targeted for privilage escalation, persistence and lateral movement
- You can't defend what you can't see
- Repetition from one source to many destinations = Scanning.
- Repetition from one source to one destination = Brute-forcing.
- Traffic at perfect, regular intervals = Malware beaconing.

## Key concepts

- Network visibility: monitoring and understanding what's happening across the network
- Network boundary: separates the internal network from the external Internet

## Why it matters in SOC

- Visibility is required to know what is going on in the network and if something is attacked

## Commands / tools used

- Investigated a breach using permiter logs such as firewall, ids amd vpn logs
- Commands used:
  - cat firewall.log | grep "BLOCK" | head
    - to check the blocked requests
  - cat firewall.log | grep "BLOCK" | cut -d' ' -f5 | cut -d: -f1 | sort -nr | uniq -c
    - to check which ip had the most block requests
  - at firewall.log | grep [ip address] | grep "ALLOW"
    - to check if any requests were allowed
  - cat vpn_auth.log | grep FAIL | cut -d' ' -f3 | sort -nr | uniq -c
    - to check the number of failed attempts
- Analyzed the same logs via splunk

## Personal notes

-
