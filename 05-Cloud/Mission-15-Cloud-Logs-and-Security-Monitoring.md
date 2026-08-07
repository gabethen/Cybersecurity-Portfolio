# Mission 15 - Cloud Logs and Security Monitoring

## Objective

Learn how SOC analysts use cloud logs to investigate user activity, identify suspicious behavior, and determine whether additional investigation or escalation is required.

---

# Questions & Answers

## 1. Which events appear most suspicious, and why?

The following events appear the most suspicious:

* User `jlee` was granted a temporary administrator role.
* The administrator role was approved, but no change request exists.
* User `jlee`, who normally works in the Marketing department, accessed HR payroll records that are not normally required for their job.
* The user downloaded 2.5 GB of files, which is the largest download ever performed by this account.
* The user logged out shortly after downloading the files.

Viewed individually, some of these events may not appear suspicious. However, when correlated together, they indicate potentially unauthorized access to sensitive information and warrant further investigation.

---

## 2. Why is it important to review the entire timeline instead of only the cloud alert?

It is important to review the entire timeline because a single cloud alert rarely tells the complete story. Reviewing all related events helps identify patterns, understand what happened before and after the alert, and determine whether multiple events together indicate suspicious or unauthorized activity.

---

## 3. Would you escalate this investigation? Explain your reasoning.

Yes, I would escalate this investigation. The user was granted temporary administrator privileges without a documented change request, accessed sensitive HR payroll records that are outside their normal job responsibilities, and performed the largest data download ever recorded for the account. These events represent a significant deviation from the user's normal behavior and justify escalation while the investigation continues.

---

## 4. What additional cloud logs or evidence would you collect?

I would collect:

* Authentication logs to verify the login location, IP address, and device used.
* Audit logs to review permission changes, administrator role assignments, and who approved the temporary administrator role.
* Data access logs to determine exactly which files were viewed and downloaded.
* Device information to identify the endpoint used during the session.
* Previous account activity to determine whether similar behavior has occurred before.
* Cloud activity logs to identify any additional actions performed before or after the download.
* Any related alerts involving the same user, device, or IP address.

---

## 5. SOC Analyst Summary

Cloud monitoring generated an alert after user `jlee`, a Marketing employee, received temporary administrator privileges without a documented change request. The user accessed HR payroll records, downloaded 2.5 GB of sensitive data—the largest download ever recorded for the account—and then logged out shortly afterward. Due to the unauthorized privilege change, unusual access pattern, and abnormal data download, the incident should be escalated for further investigation.

---

# What I Learned

This mission reinforced the importance of analyzing cloud logs as a complete timeline instead of focusing on a single alert. I learned how authentication logs, audit logs, and data access logs work together to help SOC analysts identify unusual behavior, verify access, and determine whether activity requires escalation. I also learned that understanding a user's normal behavior is critical when evaluating cloud security events.
