# 📨 Phishing Investigation – Case 001

**Date:** September 2025  
**Reported By:** Employee via internal phishing report tool  
**Severity:** Medium

---

## 🚨 Incident Summary
An employee received a suspicious email claiming to be from Microsoft, urging them to reset their Office365 password. The email contained a link that appeared legitimate at first glance but was flagged by the user as suspicious.

---

## 🧪 Tools Used
- Email Header Analyzer (Outlook)
- VirusTotal
- Splunk
- Wireshark

---

## 🔍 Investigation Steps

1. **Header Analysis:**
   - `Return-Path` domain did not match the sender.
   - `Received:` IP traced to a non-Microsoft server.

2. **Link Inspection:**
   - Link redirected to: `https://login-office365-reset[.]xyz`
   - Confirmed malicious via VirusTotal (5 AV engines flagged it).

3. **Log Review via Splunk:**
   - Confirmed user clicked the link.
   - No POST or login attempts seen, suggesting no credentials were entered.

4. **Network Monitoring via Wireshark:**
   - No command-and-control (C2) traffic observed.
   - No data exfiltration detected from user’s machine.

---

## 🧩 Indicators of Compromise (IOCs)

| Type    | Value                            |
|---------|----------------------------------|
| Domain | login-office365-reset[.]xyz       |
| IP     | 45.66.77.123                      |
| Email Subject | Your account is scheduled for deletion |

---

## 🛡️ Response Actions

- Blocked domain at email gateway and firewall level.
- Forced password reset for the affected user.
- Sent phishing alert advisory to all staff.
- Added IOCs to SIEM watchlist for detection.

---

## 📚 MITRE ATT&CK Mapping

| Technique ID | Name                        |
|--------------|-----------------------------|
| T1566.002    | Spearphishing via Link      |
| T1598.002    | Phishing for Information    |

---

## ✅ Conclusion
The phishing attempt was reported quickly and no compromise occurred. Controls functioned as intended. The investigation validated that no credentials were submitted, and no further action is required.

---

**Investigator:** Butool Fatima  
**Role:** Incident Response Analyst
