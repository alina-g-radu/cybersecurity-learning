# Linux Log Analysis Cheat Sheet

## Log Inspection

- `head file.log`  
  → Preview the first lines of a log file

---

## Filtering Logs

- `cat file.log | grep "KEYWORD"`  
  → Search for specific entries

- `cat file.log | grep "KEYWORD" | head`  
  → Limit output for quick review

---

## Extracting Fields

- `cut -d' ' -fX`  
  → Extract specific columns from log data

Example:

- `cat firewall.log | cut -d' ' -f5`  
  → Extract IP addresses

---

## Counting & Sorting

- `sort`  
  → Sort output

- `uniq -c`  
  → Count occurrences

- `sort -nr`  
  → Sort numerically (descending)

Example:

- `cat firewall.log | grep "BLOCK" | cut -d' ' -f5 | sort -nr | uniq -c`  
  → Find most frequent IPs

---

## Investigating Specific IPs

- `cat file.log | grep [IP_ADDRESS]`  
  → Filter activity for a specific IP

---

## Detecting Failed Logins

- `cat vpn_auth.log | grep FAIL`  
  → Show failed authentication attempts

---

## Pattern Recognition

- Repeated connections → possible scanning
- Multiple failed logins → possible brute-force
- Regular intervals → possible beaconing
