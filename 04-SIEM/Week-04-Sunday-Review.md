# Week 04 - Sunday Review

## 1. What is the difference between a SIEM alert and a confirmed security incident?

A SIEM alert is a notification that identifies activity requiring investigation. It collects and correlates information from different log sources to help analysts identify potentially suspicious behavior. A confirmed security incident is an event that has been investigated and verified using available evidence.

---

## 2. Why should a SOC analyst avoid assuming that every alert is malicious?

A SOC analyst should avoid assuming that every alert is malicious because not all alerts represent a real security threat. Some alerts may be caused by normal user behavior, such as entering an incorrect password or forgetting login credentials. Additional evidence and context are needed before reaching a conclusion.

---

## 3. What does event correlation mean, and why is it useful?

Event correlation is the process of connecting multiple related events to understand the larger context of an investigation. Individual events may appear normal or harmless on their own, but when combined, they may reveal suspicious or potentially malicious behavior that would not have been identified from a single alert.

---

## 4. What factors help determine an alert's priority?

The following factors help determine an alert's priority:

* Is the activity still occurring?
* What is the potential impact?
* Is a privileged or administrator account involved?
* Did endpoint protection generate a warning?
* Could other users, devices, or systems be affected?
* Is the activity unusual for the user or device?
* Does the alert involve unauthorized changes or suspicious behavior?

---

## 5. What is the difference between severity and priority?

Severity describes the potential impact or seriousness of an event. Priority determines how quickly the alert should be investigated based on factors such as risk, urgency, and potential impact.

---

## 6. Which Week 4 concept do you feel most confident about?

The Week 4 concept I feel most confident about is correlating SIEM events. I understand that connecting related events helps analysts build a timeline and identify suspicious patterns. However, I still need more hands-on practice using SIEM platforms.

---

## 7. Which concept do you want to practice more?

I have a better understanding of the concepts covered during Week 4, but I would like more hands-on practice with SIEM investigations. Additional experience reviewing alerts, correlating events, and analyzing logs would help me build confidence and apply these concepts more effectively.

---

# Sunday Investigation Challenge

## Scenario

| Time     | Event                                        |
| -------- | -------------------------------------------- |
| 10:02 AM | User `rpatel` has four failed login attempts |
| 10:04 AM | Successful login from the same device        |
| 10:06 AM | PowerShell launches an unknown script        |
| 10:07 AM | A new local administrator account is created |
| 10:08 AM | Endpoint protection generates a warning      |
| 10:10 AM | SIEM alert generated                         |

### Additional Information

* The user normally works between **9:00 AM and 5:00 PM**.
* The PowerShell script is **unknown**.
* The new administrator account is **not approved by IT**.
* Activity is still occurring.

---

## 1. Which events are most concerning?

The most concerning events are:

* An unknown PowerShell script was launched.
* A new local administrator account was created without IT approval.
* Endpoint protection generated a warning.
* The activity is still occurring.

These events are especially concerning when viewed together because they may indicate unauthorized changes or an active security threat.

---

## 2. Would you escalate this alert? Why or why not?

Yes, I would escalate this alert because an unknown PowerShell script created an unauthorized administrator account, endpoint protection generated a warning, and the activity is still occurring. Although the activity has not yet been confirmed as malicious, the combination of indicators creates enough risk to justify escalation while the investigation continues.

---

## 3. What evidence would you collect immediately?

I would immediately collect:

* The full PowerShell command and script content.
* The device involved.
* The user account associated with the activity.
* Windows Event Logs related to PowerShell execution and account creation.
* Details about the new administrator account, including when and how it was created.
* EDR alerts and endpoint activity.
* The source IP address and related network connections.
* Authentication activity before and after the alert.
* Whether the same script or administrator account appeared on other devices.

---

## 4. SOC Analyst Summary

The SIEM identified an unknown PowerShell script that created an unauthorized local administrator account, followed by an endpoint protection warning. Although the user logged in during normal working hours after four failed login attempts, the unauthorized account creation and ongoing activity warrant immediate escalation and further investigation.

---

# Week 04 Overall Review

Week 4 strengthened my understanding of SIEM alert investigations, event correlation, alert triage, and prioritization. I learned that a SIEM alert is the starting point of an investigation rather than proof of malicious activity. I also learned to evaluate alerts based on context, risk, potential impact, and urgency before deciding whether escalation is necessary. I feel more confident connecting related events and identifying suspicious patterns, but I want more hands-on SIEM practice to strengthen my investigative skills.
