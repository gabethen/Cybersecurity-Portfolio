# Week 04 Reflection

## 1. What was the most important SIEM investigation skill you learned this week?

The most important SIEM investigation skill I learned this week is that analysts need to gather evidence from multiple log sources before determining whether an alert is malicious and requires escalation. A single alert does not always provide enough context, so reviewing multiple sources helps create a more accurate investigation.

---

## 2. How has your understanding of SIEM alerts changed since the beginning of the week?

My understanding of SIEM alerts has changed because I now understand that SIEM helps analysts identify, prioritize, and investigate potential security events. I have a better understanding that alerts need to be evaluated based on risk, context, and available evidence instead of assuming every alert is malicious.

---

## 3. Why is event correlation important during a security investigation?

Event correlation is important because a single event may not appear malicious by itself, but multiple related events can reveal a larger security concern. Connecting events together helps SOC analysts understand timelines, identify patterns, and determine whether activity requires further investigation.

---

## 4. What factors would you use to decide which alert should be investigated first?

I would prioritize alerts based on factors such as:

- Whether the activity is still occurring.
- Whether endpoint protection generated warnings.
- The potential impact of the activity.
- Whether privileged accounts are involved.
- Whether unauthorized changes are being made.

For example, suspicious PowerShell activity that attempts to create an unknown administrator account would require immediate attention.

---

## 5. What part of SIEM investigations do you still want to practice?

I would like to continue practicing SIEM investigations to build more confidence. I understand the basic concepts, but I still feel like I am in the beginner stage and need more experience reviewing alerts, correlating events, and understanding how analysts use SIEM platforms during real investigations.

---

# Weekly Scenario

## Which alert would you investigate first?

I would investigate **Alert 2** first.

---

## Why?

Alert 2 has the highest priority because an unknown PowerShell script was executed, attempted to create a new administrator account, generated endpoint protection warnings, and the activity is still occurring. These indicators suggest a potentially active security threat that requires immediate investigation.

---

## What evidence would you collect before escalating it?

Before escalating Alert 2, I would collect:

- The device involved.
- The user account involved.
- The PowerShell script that was executed.
- The purpose and behavior of the script.
- Any unknown IP addresses involved.
- Additional endpoint protection alerts.
- Windows Event Logs.
- User authentication activity before and after the event.
- Any changes made to accounts or system settings.

---

# Week 04 Overall Reflection

Week 4 helped me better understand how SOC analysts use SIEM platforms to investigate and prioritize security alerts. I learned that alerts should not be judged individually but instead analyzed through correlation, context, and evidence. I also learned the importance of prioritizing incidents based on risk and urgency. While I still need more practice using SIEM tools confidently, I have developed a stronger understanding of how analysts approach investigations.
