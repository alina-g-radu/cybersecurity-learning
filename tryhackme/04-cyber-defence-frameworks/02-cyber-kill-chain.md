# Cyber Kill Chain

## What I learned

- During the reconnaissance phase, attackers may gather information without directly interacting with the target by using publicly available data.
- There are multiple methods for delivering a payload, such as phishing emails, USB drops, and watering hole attacks (compromising websites frequently visited by a target group).
- Signs of exploitation may include unexpected process execution, registry changes, creation of new services, or suspicious command-line activity.
- The Cyber Kill Chain is an older model (introduced in 2011) and should be used alongside more modern frameworks such as MITRE ATT&CK or the Unified Kill Chain.

## Key concepts

- Cyber Kill Chain: A model describing the stages of a cyber attack.
- Reconnaissance: The research and planning phase of an attack.
- Weaponization: Creating a payload by combining exploits with malware.
- Delivery: Transmitting the payload to the target.
- Exploitation: Executing malicious code on the target system.
- Installation: Establishing persistence (e.g., installing a backdoor).
- Command and Control (C2): Allowing the attacker to remotely control the compromised system.
- Actions on Objectives: Achieving the attacker’s final goal ( data exfiltration, system disruption).

## Why it matters in SOC

- Understanding the stages of an attack helps analysts detect threats earlier and respond more effectively at different points in the attack lifecycle.

## Tools / activities used

- Reconstructed the Cyber Kill Chain for a real-world cyber attack scenario (target's 2013 data breach).

## Personal notes

- Even though it is an older model, the Cyber Kill Chain is still useful for understanding attack flow and can be more effective when combined with modern frameworks.
