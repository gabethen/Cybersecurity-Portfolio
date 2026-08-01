# Mission 12 - Alert Triage and Prioritization

## Objective

Learn how SOC analysts evaluate alert severity, risk, and urgency to determine which alerts should be investigated first.

---

## Questions & Answers

### 1. Which alert would you investigate first, and why?

I would investigate **Alert B** first because PowerShell launched an unknown script that attempted to create a new user account. Endpoint protection also generated warnings, and the activity is still occurring. These indicators could represent an active security threat and require immediate investigation.

---

### 2. Rank all three alerts from highest to lowest priority.

1. **Alert B — Suspicious PowerShell Activity**

   Alert B is the highest priority because the activity is still occurring, an unknown PowerShell script attempted to create a new user account, and endpoint protection generated warnings. The combination of active activity and potentially unauthorized account creation creates a higher level of risk.

2. **Alert A — Failed Login Attempts**

   Alert A is the second-highest priority because there were 10 failed login attempts. However, no successful login occurred, and no additional endpoint or network alerts were generated. The activity should still be investigated to determine whether it was caused by a user error, a password-related issue, or an attempted unauthorized login.

3. **Alert C — Unusual Network Connection**

   Alert C is the lowest priority based on the available information because the user normally works remotely, and the connection used port 443, which is commonly associated with HTTPS traffic. However, the unfamiliar external IP should still be investigated because port 443 does not automatically make a connection safe.

---

### 3. What makes Alert B more urgent than the other alerts?

Alert B is more urgent because the activity is still occurring. In addition, an unknown PowerShell script attempted to create a new user account, and endpoint protection generated warnings. These events may indicate an active security threat that could affect the system if not investigated quickly.

---

### 4. What information would you collect before escalating Alert A?

Before escalating Alert A, I would review:

* Windows Security and authentication logs.
* The source IP address associated with the failed login attempts.
* Whether the attempts came from one device or multiple devices.
* Whether other user accounts received similar failed login attempts.
* Whether user `jsmith` was attempting to log in at that time.
* Whether the user recently changed or forgot their password.
* Any additional endpoint or network activity related to the account.

I would also continue monitoring the account for additional suspicious activity.

---

### 5. What information would you collect before escalating Alert C?

Before escalating Alert C, I would investigate:

* Whether the unfamiliar IP address communicated with other devices in the organization.
* The owner and reputation of the external IP address.
* Whether the user normally connects to the IP address.
* Whether any files or data were downloaded or transferred.
* The amount and duration of the network traffic.
* Whether any endpoint or security alerts occurred before or after the connection.

---

### 6. If you were writing a brief note to your SOC team, how would you summarize your priority decision?

Based on the three alerts, **Alert B should receive the highest priority** because an unknown PowerShell script attempted to create a new user account, endpoint protection generated warnings, and the activity is still ongoing. Alert A should be investigated next because it contains multiple failed login attempts, although no successful login or additional endpoint or network alerts were observed. Alert C is currently the lowest priority because the user normally works remotely and the connection used port 443, but the unfamiliar external IP should still be reviewed for reputation and related activity.

---

## What I Learned

This mission taught me that SOC alerts should be prioritized based on potential impact, risk, and urgency. An alert involving active suspicious activity, attempted account creation, and endpoint warnings may require immediate attention, while other alerts may need additional context before escalation. I also learned that common ports, such as port 443, do not automatically make network activity safe. SOC analysts must review the complete context before reaching a conclusion.
