# Phishing Investigation – Suspicious Credential Harvesting Email

## Scenario

A user reported receiving an email requesting an urgent password reset through a suspicious link.

---

## Investigation Workflow


## Initial Triage

- Alert Source: User Report / Email Security Alert
- Severity: Medium
- Investigation Start Time:
- Analyst: Pavani MV

---

## Investigation

### Email Analysis

- Sender Address: security@contoso-helpdesk.com
- Reply-To: 
- Subject: Action Required: Review Secure Document
- Authentication Results (SPF/DKIM/DMARC)

SPF: Verifies whether the sending server is authorized to send email for the domain.

DKIM: Verifies that the email content hasn't been modified after it was signed.

DMARC: Defines how receiving mail servers should handle emails that fail SPF and/or DKIM and ensures domain alignment.

### URL Analysis

- Domain Reputation
- WHOIS
- VirusTotal Results

### Attachment Analysis

- File Name
- File Hash
- Sandbox Results

### User Activity

- Was the URL clicked?
- Credentials Entered?
- MFA Triggered?

---

## Impact Assessment

- Number of affected users
- Mailbox compromised?
- Credentials exposed?

---

## Containment

- Block sender
- Block URL
- Reset password
- Revoke sessions

---

## Eradication

- Remove malicious emails
- Block Indicators

---

## Recovery

- Enable MFA
- User Awareness
- Monitor account

---

## MITRE ATT&CK

- T1566 - Phishing
- T1078 - Valid Accounts

---

## Lessons Learned

Document improvements to detection, user awareness, or response processes.
