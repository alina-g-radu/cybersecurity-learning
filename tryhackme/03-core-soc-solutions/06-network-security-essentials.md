# Network Security Essentials

## What I learned

- Workstations are common entry points for attackers due to lower monitoring and user interaction.
- File and database servers are often targeted by ransomware operators.
- Application servers are high-value targets because they are externally exposed.
- Active Directory is frequently targeted for privilege escalation, persistence, and lateral movement.
- Effective security requires visibility: "You can't defend what you can't see."
- Repeated connections from one source to many destinations may indicate scanning activity.
- Repeated attempts from one source to a single destination may indicate brute-force attacks.
- Regular, periodic traffic patterns may indicate malware beaconing.

## Key concepts

- Network visibility: The ability to monitor and understand activity across a network.
- Network boundary: The point separating internal networks from external networks (e.g., the internet).

## Tools / activities used

- Investigated a simulated breach using perimeter logs (firewall, IDS, and VPN logs).
- Used command-line tools to analyze and filter log data.
- Analyzed the same logs using Splunk.

### Commands used

#### Log inspection

- `head firewall.log`
- `head ids_alerts.log`
- `head vpn_auth.log`  
  → Previewed log contents

#### Firewall analysis

- `cat firewall.log | grep "BLOCK" | head`  
  → Identified blocked requests

- `cat firewall.log | grep "BLOCK" | cut -d' ' -f5 | cut -d: -f1 | sort -nr | uniq -c`  
  → Found IPs with the most blocked requests

- `cat firewall.log | grep [IP_ADDRESS] | grep "ALLOW"`  
  → Checked if traffic from a suspicious IP was allowed

- `cat firewall.log | grep [IP_ADDRESS] | grep "ALLOW" | head`  
  → Previewed allowed traffic from a specific IP

- `cat firewall.log | grep [IP_ADDRESS] | cut -d' ' -f5,6,7 | uniq | sort`  
  → Reviewed unique connection patterns

#### VPN analysis

- `cat vpn_auth.log | grep FAIL | cut -d' ' -f3 | sort -nr | uniq -c`  
  → Counted failed login attempts

- `cat vpn_auth.log | grep [IP_ADDRESS]`  
  → Investigated activity from a specific IP

#### IDS analysis

- `cat ids_alerts.log | grep [IP_ADDRESS] | head`  
  → Checked alerts related to a specific IP

- `cat ids_alerts.log | grep -n [IP_ADDRESS] | grep 'SMB' | cut -d' ' -f6,7,8,9,10,19,21 | head`  
  → Investigated SMB-related alerts

- `cat ids_alerts.log | grep C2 | head`  
  → Looked for command-and-control activity

- `cat ids_alerts.log | grep -n [IP_ADDRESS] | cut -d' ' -f6,7,8,9,10,19,22,23 | head -n 15`  
  → Extracted key fields for analysis

- `cat ids_alerts.log | grep -n [IP_ADDRESS] | cut -d' ' -f6,7,8,9,10,19,22,23 | uniq -c | sort -nr | head`  
  → Identified most frequent alert patterns

## Personal notes

- Recognizing patterns in network traffic (such as scanning or brute-force behavior) is key to detecting attacks early.
