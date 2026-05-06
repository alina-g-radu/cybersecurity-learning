# Phishing Analysis Fundamentals

## What I learned

- Spam and phishing are among the most common social engineering threats.
- Several protocols are involved when sending and receiving emails:
  - Simple Mail Transfer Protocol (SMTP)  
    → used to send emails
  - Post Office Protocol (POP3)  
    → downloads emails to a device
  - Internet Message Access Protocol (IMAP)  
    → syncs emails across multiple devices

---

## Key concepts

- Email header  
  → metadata about the email (sender, route, servers involved)

- Email body  
  → the actual content of the message

- Spam  
  → unsolicited bulk emails

- Phishing  
  → emails that appear trustworthy but are malicious

- Spear phishing  
  → targeted phishing aimed at a specific individual or organization

- Whaling  
  → phishing targeting high-level executives

- Smishing  
  → phishing via SMS

- Vishing  
  → phishing via voice calls

- Defanged IP address  
  → a modified IP (e.g., 192[.]168[.]1[.]1) used to safely share malicious indicators without making them clickable

---

## Why it matters in SOC

- Phishing is one of the most common initial access methods used by attackers.
- SOC analysts need to analyze emails, identify malicious indicators, and prevent users from being compromised.

---

## Tools / activities used

- Analyzed phishing email samples and identified suspicious elements (headers, content, indicators)

---

## Personal notes

- Phishing attacks rely heavily on human behavior, which makes them very effective.
- Even simple emails can lead to serious security incidents if not properly analyzed.
