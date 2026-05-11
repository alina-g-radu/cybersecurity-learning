# Wireshark Cheatsheet

---

## Display Filters

| Filter                          | Description                   |
| ------------------------------- | ----------------------------- |
| `ip.addr == 192.168.1.1`        | Traffic to/from host          |
| `ip.src == 10.0.0.1`            | Source IP only                |
| `ip.dst == 10.0.0.1`            | Destination IP only           |
| `tcp.port == 443`               | TCP on port 443               |
| `udp.port == 53`                | UDP DNS traffic               |
| `http`                          | All HTTP traffic              |
| `http.request`                  | HTTP requests only            |
| `http.response.code == 200`     | HTTP 200 OK responses         |
| `dns`                           | All DNS packets               |
| `dns.qry.name == "example.com"` | DNS query for domain          |
| `tls`                           | TLS/SSL traffic               |
| `tcp.flags.syn == 1`            | SYN packets (new connections) |
| `tcp.flags.rst == 1`            | RST packets (resets)          |
| `icmp`                          | Ping / ICMP traffic           |
| `arp`                           | ARP requests/replies          |
| `frame.len > 1000`              | Large packets (>1000 bytes)   |

---

## Filter Operators & Logic

| Operator               | Description              |
| ---------------------- | ------------------------ |
| `&&` or `and`          | Logical AND              |
| `\|\|` or `or`         | Logical OR               |
| `!` or `not`           | Logical NOT              |
| `==  !=  >  <  >=  <=` | Comparison operators     |
| `contains`             | Field contains substring |
| `matches`              | Regex match              |
| `in {80 443 8080}`     | Value in set             |

**Examples:**

```
ip.addr == 1.1.1.1 && tcp
!(arp || dns)
http.request && ip.src == 192.168.1.0/24
```

---

## Capture Filters (BPF Syntax)

> Set before capturing — not the same as display filters.

| Filter                         | Description       |
| ------------------------------ | ----------------- |
| `host 192.168.1.1`             | Capture one host  |
| `net 192.168.0.0/24`           | Entire subnet     |
| `port 80`                      | Only port 80      |
| `portrange 1-1024`             | Well-known ports  |
| `tcp`                          | TCP only          |
| `udp`                          | UDP only          |
| `not port 22`                  | Exclude SSH       |
| `host 1.1.1.1 and port 53`     | DNS to Cloudflare |
| `ether host aa:bb:cc:dd:ee:ff` | By MAC address    |

---

## PCAP Analysis Workflow

1. **Open file** — `File → Open` or drag `.pcap`/`.pcapng` into Wireshark
2. **File summary** — `Statistics → Capture File Properties` (duration, packet count, interface)
3. **Protocol breakdown** — `Statistics → Protocol Hierarchy`
4. **Top talkers** — `Statistics → Conversations` (by IP/port)
5. **All hosts** — `Statistics → Endpoints`
6. **Follow a stream** — right-click a packet → `Follow → TCP / UDP / HTTP Stream`
7. **Export files** — `File → Export Objects` (HTTP, SMB, etc.)
8. **Resolve names** — `View → Name Resolution → Resolve Network/Transport`

---

## TCP & Stream Analysis

| Filter                        | Description                                  |
| ----------------------------- | -------------------------------------------- |
| `tcp.stream eq 0`             | Filter by stream (increment for each stream) |
| `tcp.analysis.retransmission` | Retransmitted packets                        |
| `tcp.analysis.zero_window`    | Zero window packets                          |
| `tcp.analysis.duplicate_ack`  | Duplicate ACKs                               |
| `tcp.analysis.out_of_order`   | Out-of-order packets                         |
| `tcp.analysis.flags`          | All TCP issues                               |

**TCP stream graph:** `Statistics → TCP Stream Graphs → Round Trip Time`

---

## Common Protocol Filters

| Protocol    | Filter            | Default Port |
| ----------- | ----------------- | ------------ |
| HTTP        | `http`            | 80           |
| HTTPS / TLS | `tls`             | 443          |
| DNS         | `dns`             | UDP 53       |
| DHCP        | `dhcp` or `bootp` | 67/68        |
| ICMP        | `icmp`            | —            |
| ARP         | `arp`             | —            |
| FTP         | `ftp`             | 21           |
| SSH         | `ssh`             | 22           |
| SMB         | `smb2`            | 445          |
| NTP         | `ntp`             | UDP 123      |
| VoIP        | `sip` / `rtp`     | 5060         |
| HTTP/3      | `quic`            | UDP 443      |
| Kerberos    | `kerberos`        | 88           |
| LDAP        | `ldap`            | 389          |

---

## Useful Field References

| Field                                  | Description              |
| -------------------------------------- | ------------------------ |
| `frame.number`                         | Packet number            |
| `frame.time_relative`                  | Time since first packet  |
| `frame.len`                            | Total frame length       |
| `eth.src` / `eth.dst`                  | Source / destination MAC |
| `ip.ttl`                               | Time to live             |
| `tcp.seq` / `tcp.ack`                  | Sequence / ACK number    |
| `tcp.window_size`                      | TCP window size          |
| `http.host`                            | HTTP Host header         |
| `http.request.uri`                     | Requested URL path       |
| `tls.handshake.extensions_server_name` | SNI hostname in TLS      |
| `dns.qry.name`                         | DNS queried domain name  |

---

## Keyboard Shortcuts

| Shortcut        | Action                              |
| --------------- | ----------------------------------- |
| `Ctrl+F`        | Find packet                         |
| `Ctrl+G`        | Go to packet number                 |
| `Ctrl+E`        | Start/stop capture                  |
| `Ctrl+R`        | Reload / re-read file               |
| `Ctrl+M`        | Mark / unmark packet                |
| `Ctrl+T`        | Set / unset time reference          |
| `Ctrl+Alt+F`    | Apply display filter                |
| `Ctrl+Z`        | Clear display filter                |
| `Ctrl+D`        | Filter expression builder           |
| `Ctrl+Shift+E`  | Export packet dissections           |
| `Space`         | Scroll down packet list             |
| `Alt+→ / Alt+←` | Next / previous packet in selection |

---

## Default Color Coding

| Color    | Meaning          |
| -------- | ---------------- |
| Green    | TCP connections  |
| Blue     | UDP traffic      |
| Yellow   | ARP / broadcast  |
| Pink/Red | TCP errors / RST |
| Purple   | ICMP             |
| Orange   | Bad checksum     |

Customize via `View → Coloring Rules`.

---

## tshark (Command Line)

```bash
# Read a PCAP file
tshark -r file.pcap

# Apply a display filter
tshark -r file.pcap -Y "http"

# Extract specific fields
tshark -r file.pcap -T fields -e ip.src -e ip.dst -e http.host

# Capture live traffic to file
tshark -i eth0 -w output.pcap

# Apply capture filter
tshark -i eth0 -f "port 80" -w output.pcap

# Limit capture to 100 packets
tshark -i eth0 -c 100

# Protocol hierarchy stats
tshark -r file.pcap -q -z io,phs

# TCP conversation stats
tshark -r file.pcap -z conv,tcp

# Merge multiple PCAPs
mergecap -w merged.pcap a.pcap b.pcap
```

---

## Other tips

- **Quick filter from packet** — right-click any field → `Apply as Filter` or `Prepare as Filter`
- **Add custom columns** — right-click a detail field → `Apply as Column`
- **Relative timestamps** — `View → Time Display Format → Seconds Since Beginning`
- **Decrypt TLS** — supply a key log file via `Edit → Preferences → Protocols → TLS → (Pre)-Master-Secret log file`
- **Expert analysis** — `Analyze → Expert Information` for a summary of errors, warnings, and notes
- **I/O graph** — `Statistics → I/O Graph` to visualize traffic volume over time
- **Anonymize IPs** — `editcap --anonymize-fields ip.addr out.pcap in.pcap`
- **Split large PCAP** — `editcap -c 10000 big.pcap split.pcap` (10k packets per file)
