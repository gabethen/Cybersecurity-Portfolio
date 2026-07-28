# Mission 10 - Introduction to SIEM Alert Investigations

## Objective

Learn how SOC analysts investigate SIEM alerts by gathering evidence from multiple log sources before determining whether an alert represents malicious activity.

---

## Scenario

A SIEM generates the following alert:

| Field | Value |
|--------|-------|
| Alert | Multiple Failed Logins |
| User | jsmith |
| Device | HR-Laptop-14 |
| Time | 8:42 AM |
| Failed Attempts | 7 |
| Successful Login | Yes (8:45 AM) |

### Additional Information

- The user normally logs in between **8:30 AM and 9:00 AM**.
- The successful login came from the **same device**.
- No antivirus or endpoint alerts were generated.
- No unusual network connections were detected after the login.

---

# Questions & Answers

## 1. What information in this alert appears normal?

Based on the available information, most of the activity appears normal. The user successfully logged in from the same device during their normal working hours, and there were no unusual network connections or endpoint security alerts after the login.

---

## 2. What information might require additional investigation?

The seven failed login attempts should be investigated further. While the user may have simply forgotten their password, it is also important to determine whether someone else attempted to access the account before the legitimate user successfully logged in.

---

## 3. Based only on the available evidence, would you immediately escalate this as a security incident? Why or why not?

Based on the current evidence, I would not immediately escalate this as a security incident. Although multiple failed login attempts occurred, the successful login came from the same device during the user's normal working hours. Additionally, no unusual network activity or endpoint security alerts were detected. More evidence would be needed before determining that the activity is malicious.

---

## 4. What additional logs or evidence would you review before making a final decision?

Before making a final decision, I would review:

- Windows Security Event Logs
- Endpoint Detection and Response (EDR) logs
- Active Directory authentication logs
- SIEM timeline for related events
- User login history to determine whether this behavior is normal

Reviewing multiple sources helps build context and ensures that conclusions are based on evidence rather than assumptions.

---

## 5. If you had to summarize your investigation in one or two sentences, what would you tell your team?

The investigation identified seven failed login attempts followed by a successful login from the same device during the user's normal working hours. No additional endpoint or network indicators of compromise were observed, so the activity appears consistent with a user entering an incorrect password before successfully authenticating. Continued monitoring is recommended if similar behavior persists.

---

# What I Learned

This mission reinforced that SIEM alerts are starting points for investigations rather than proof of malicious activity. I learned that SOC analysts must gather evidence from multiple sources, evaluate the surrounding context, and avoid making assumptions before determining whether an alert represents a security incident. By reviewing logs, user behavior, device activity, and network events together, analysts can make informed and accurate decisions.
