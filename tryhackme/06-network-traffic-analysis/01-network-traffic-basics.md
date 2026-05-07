# Network Traffic Basiscs

## What I learned

- Network trafic should be analysed to monitor network performance, check for abnormalities in the network and inspect suspicious communcation internally and externally
- On each layer of the TCP/IP model can be found important infromation about the network:
  - application: the application header infromation and the application data ( the payload) and it's different based on the protocol used
  - transport : transport header ( most cases TCP or UDP)
  - internet: source and destination IP and TTL
  - link: more addressing information
- There are two network traffic source: intermeediary annd endpoint
- Network traffic flow: north-south traffic : LAN to WAN and vice verse and East-West: within the LAN

## Key concepts

- NTA (Network Traffic Analysis): a process that encompasses capturing, inspecting, and analyzing data as it flows in a network.
- Network tap: a physical device you place inline in your network which creates a copy of all the network traffic
- Port mirroring: software approach to copying packets from one port on an intermediary device to another that is attached to

## Why it matters in SOC

- Because it helps detect suspicious or malicious activity, reconstruct attacks during incident response and verify and validate alerts.

## Commands / tools used

- Analyzed network traffic and placed the tap on the correct position

## Personal notes

-
