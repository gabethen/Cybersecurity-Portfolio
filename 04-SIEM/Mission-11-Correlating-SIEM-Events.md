# Mission 11 - Correlating SIEM Events

## Objective

Learn how SOC analysts correlate multiple SIEM events to determine whether they are related and require further investigation.

---

## Questions & Answers

### 1. Which events in the timeline appear most suspicious, and why?

Based on the SIEM event timeline, the following events appear most suspicious:

- Five failed login attempts at **9:07 AM**.
- PowerShell launching at **9:10 AM**.
- Installation of software that is **not approved** by the company's IT department at **9:11 AM**.
- A connection to an unfamiliar external IP address at **9:12 AM**.

These events could indicate suspicious activity when viewed together. However, additional evidence is needed before determining whether the activity is malicious.

---

### 2. Why is it important to review the entire timeline instead of focusing only on the SIEM alert?

It is important to review the entire timeline because one event alone does not tell the complete story. Correlating multiple events helps determine whether they are related and provides the context needed to make informed decisions during an investigation.

---

### 3. Would you escalate this investigation? Explain your reasoning using the evidence provided.

Yes. I would escalate this investigation for further analysis because several suspicious events occurred in sequence, including failed login attempts, PowerShell execution, unauthorized software installation, and communication with an unfamiliar external IP address. Although this does not confirm malicious activity, the combination of indicators justifies escalation while additional evidence is collected.

---

### 4. What additional evidence would you collect before declaring this a confirmed security incident?

Before declaring this a confirmed security incident, I would investigate:

- Which device is involved.
- What happened before and after the alert.
- Whether this is normal behavior for the user.
- Whether the external IP has communicated with other devices.
- Windows Security Event Logs.
- EDR alerts.
- The file hash and reputation of the installed software.
- Firewall and network traffic logs.

---

### 5. If you were briefing another SOC analyst, how would you summarize this investigation?

The investigation identified multiple failed login attempts followed by a successful login, PowerShell execution, unauthorized software installation, and communication with an unfamiliar external IP address. While these events do not confirm malicious activity, their sequence and correlation warrant escalation for further investigation and continued evidence collection.

---

## What I Learned

This mission taught me that a single alert rarely tells the entire story. By correlating multiple events into a timeline, SOC analysts can better understand user behavior, identify suspicious patterns, and determine when an investigation should be escalated while continuing to gather evidence.
