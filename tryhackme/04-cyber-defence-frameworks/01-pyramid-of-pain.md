# Pyramid of Pain

![Pyramid of Pain](/tryhackme/04-cyber-defence-frameworks/pyramid-of-pain.png)

## What I learned

- Attackers use different techniques and indicators, some of which are easier to change than others.
- The "Pyramid of Pain" shows how difficult it is for an attacker to adapt when different types of indicators are detected and blocked.

## Key concepts

- Hash value: A fixed-length value that uniquely identifies data (e.g., a file).
- IP address: Identifies a device on a network.
- Domain name: A human-readable name that maps to an IP address.
- Host artifacts: Traces left on a system (e.g., registry keys, files, processes).
- Network artifacts: Indicators such as user-agent strings, C2 communication, or HTTP patterns.
- Tools: Software used by attackers to perform actions.
- TTPs (Tactics, Techniques, and Procedures): The methods and behaviors attackers use, often mapped using frameworks like MITRE ATT&CK.

## Why it matters in SOC

- Detecting higher-level indicators (like tools or TTPs) makes it harder for attackers to adapt, increasing the "pain" for them and improving defense effectiveness.

## Tools / activities used

- Matched scenarios to the correct levels in the Pyramid of Pain.

## Personal notes

- Focusing on behavior (TTPs) rather than simple indicators (like IPs or hashes) provides stronger and more long-term detection.
