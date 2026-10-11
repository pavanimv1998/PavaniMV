# Atypical Travel Investigation Playbook

## Overview

This playbook provides a structured approach for investigating atypical travel alerts generated when a user account authenticates from geographically distant locations within a time frame that is unlikely for legitimate travel. The objective is to determine whether the activity is expected, suspicious, or indicative of account compromise.

---

# Alert Information

| Field | Value |
|--------|-------|
| Alert ID | IR-2026-0214 |
| Alert Source | Microsoft Defender XDR / Microsoft Entra ID Identity Protection |
| Alert Name | Atypical Travel Detected |
| Severity | Medium |
| Detection Time | 2026-10-11 08:45 UTC |
| Analyst | Pavani M |
| Status | Closed - Benign |

---

# User Information

| Field | Value |
|--------|-------|
| User | john.doe@contoso.com |
| Department | Finance |
| Device | FIN-LT-104 |
| User Risk | Low |
| Sign-in Risk | Medium |

---

# Sign-in Activity

| Time (UTC) | Country | City | Public IP | Result |
|------------|----------|------|------------|--------|
| 07:05 | India | Hyderabad | 203.0.113.24 | Success |
| 08:32 | Germany | Frankfurt | 198.51.100.87 | Success |

Estimated travel time between the two locations is not feasible, resulting in an Atypical Travel alert.

---

# Authentication Details

| Field | Value |
|--------|-------|
| MFA | Successfully Completed |
| Authentication Method | Microsoft Authenticator |
| Device ID | 6fd5b89c-2ad9-4f72-bb6d-9c1c8b7d55af |
| Operating System | Windows 11 |
| Browser | Microsoft Edge |

---

# Investigation Steps

## 1. Review Sign-in Logs

- Verified successful authentication events.
- Compared source IP addresses.
- Reviewed sign-in history for the previous seven days.
- Identified no additional suspicious authentication attempts.

---

## 2. IP Reputation Analysis

| IP Address | Reputation |
|------------|------------|
| 203.0.113.24 | Trusted |
| 198.51.100.87 | Microsoft Azure Datacenter |

Result:

No malicious reputation identified.

---

## 3. Device Validation

Verified:

- Same Device ID observed
- Same browser
- Same operating system
- Same authentication method

No evidence of a new or unmanaged device.

---

## 4. User Validation

Confirmed with the user that:

- A corporate VPN was enabled.
- No unauthorized login activity was observed.
- User confirmed ownership of both authentication events.

---

## 5. Conditional Access Review

- MFA enforced
- Compliant device
- Corporate VPN in use
- No Conditional Access policy violations

---

# Root Cause

The second authentication originated from a Microsoft cloud endpoint while the user was connected through the organization's VPN, resulting in an atypical travel detection.

No evidence of credential compromise or malicious activity was identified.

---

# Impact Assessment

| Item | Status |
|------|--------|
| Credential Compromise | No |
| MFA Bypass | No |
| Data Access | Normal |
| Device Compromise | No |
| Lateral Movement | Not Observed |

---

# MITRE ATT&CK

| Technique | Description |
|-----------|-------------|
| T1078 | Valid Accounts |

---

# Detection Opportunities

- Impossible Travel
- New Country Login
- New Device Sign-in
- Anonymous IP Detection
- Risky Sign-in Correlation

---

# Recommendations

- Continue enforcing MFA.
- Maintain Conditional Access policies.
- Monitor repeated atypical travel alerts for the same account.
- Review VPN exit locations to reduce false positives.

---

# Investigation Outcome

**Classification:** Benign Positive

Reason:

Investigation confirmed the activity originated from the user's corporate VPN and a trusted Microsoft cloud service. Authentication occurred from the same managed device with successful MFA verification. No indicators of account compromise were identified.

---

# Lessons Learned

- VPN infrastructure can generate atypical travel alerts.
- Correlating device identity, MFA status, and IP reputation helps reduce false positives.
- User validation is an important step before escalating identity-related alerts.
