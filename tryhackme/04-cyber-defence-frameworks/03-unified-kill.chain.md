# Unified Kill Chain

## What I learned

- Frameworks such as STRIDE, DREAD, and CVSS are used in threat modeling to identify and assess risks.
- In cybersecurity, an asset refers to any valuable system component, such as hardware, software, or data.
- The Unified Kill Chain (UKC) expands traditional kill chain models into 18 phases, covering the full attack lifecycle.
- UKC organizes attacks into three main goals: initial foothold (in), network propagation (through), and actions on objectives (out).

## Key concepts

- Threat Modeling: A process used to identify, analyze, and reduce security risks in systems or applications.
- Unified Kill Chain (UKC): A framework that combines and extends traditional kill chain models to provide a more detailed view of modern attacks.

## UKC Goals

#### Goal: In (Initial Foothold)

Gaining initial access to the target system:

- Reconnaissance  
  → Gathering information about the target (e.g., OSINT, scanning)

- Weaponization  
  → Creating a payload by combining malware with an exploit

- Delivery / Social Engineering  
  → Delivering the payload to the target (e.g., phishing, malicious links)

- Exploitation  
  → Executing malicious code on the target system

- Persistence  
  → Maintaining long-term access to the system

- Defense Evasion  
  → Avoiding detection by security tools

- Command & Control (C2)  
  → Establishing communication with the attacker’s server

---

#### Goal: Through (Propagation)

Expanding access and moving within the network:

- Discovery  
  → Identifying systems, users, and network structure

- Privilege Escalation  
  → Gaining higher-level permissions (e.g., admin access)

- Execution  
  → Running malicious commands or scripts on compromised systems

- Credential Access  
  → Stealing usernames, passwords, or authentication tokens

- Lateral Movement  
  → Moving to other systems within the network

---

#### Goal: Out (Actions on Objectives)

Achieving the attacker’s final goal:

- Collection  
  → Gathering sensitive data (files, credentials, etc.)

- Exfiltration  
  → Transferring data out of the network

- Impact  
  → Disrupting systems (e.g., ransomware, data destruction)

## Why it matters in SOC

- The Unified Kill Chain helps analysts understand and track attacker behavior across the entire attack lifecycle, improving detection and response at multiple stages.

## Tools / activities used

- Mapped attacker actions to the corresponding phases of the Unified Kill Chain.

## Personal notes

- The Unified Kill Chain provides a more complete and modern view of attacks compared to the traditional Cyber Kill Chain, making it more useful for real-world analysis.
