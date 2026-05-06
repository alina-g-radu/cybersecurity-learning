# Phishing Prevention

## What I learned

- Email security relies on authentication mechanisms that help verify whether an email is legitimate or spoofed.
- The main standards used for email authentication are SPF, DKIM, and DMARC.

---

## Key concepts

### SPF (Sender Policy Framework)

Used to verify which servers are allowed to send emails on behalf of a domain.

Example SPF record:

- `v=spf1 ip4:127.0.0.1 include:_spf.google.com -all`
- `v=spf1` → version of SPF record
- `ip4:127.0.0.1` → allowed sending IP address
- `include:_spf.google.com` → allows Google’s mail servers
- `-all` → reject all other sources

### DKIM (DomainKeys Identified Mail)

Used to verify that an email has not been altered and was sent by an authorized domain using cryptographic keys.

Example DKIM record:

- `v=DKIM1; k=rsa; p=<public_key>`
- `v=DKIM1` → DKIM version
- `k=rsa` → encryption algorithm used
- `p=` → public key used to verify the signature

---

### DMARC (Domain-based Message Authentication, Reporting and Conformance)

Ensures SPF and DKIM results align with the sender’s domain and defines how to handle failed authentication.

Example DMARC record:
`v=DMARC1; p=quarantine; rua=mailto:postmaster@website.com`

- `v=DMARC1` → version
- `p=quarantine` → policy (send suspicious emails to spam)
- `rua=` → email address for aggregate reports

---

### S/MIME

Secure/Multipurpose Internet Mail Extensions used for:

- digitally signing emails
- encrypting email content

---

## Why it matters in SOC

- These mechanisms help detect email spoofing and prevent phishing attacks.
- SOC analysts use them to verify whether emails are legitimate or malicious.

---

## Tools / activities used

- Analyzed PCAP files containing SMTP traffic
- Inspected email authentication mechanisms (SPF, DKIM, DMARC)

---

## Personal notes

- Email authentication does not stop all phishing, but it significantly reduces spoofing attempts.
- Understanding SPF, DKIM, and DMARC is essential for investigating email-based attacks.
