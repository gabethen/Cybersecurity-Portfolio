# Mission 14 - Cloud Identity and Access Management (IAM)

## Objective

Understand how cloud environments manage identity, access, roles, and permissions, and learn how SOC analysts investigate suspicious cloud account activity.

---

## Scenario

| Time    | Event                                                                          |
| ------- | ------------------------------------------------------------------------------ |
| 9:00 AM | User `mgarcia` logs in                                                         |
| 9:02 AM | MFA is successfully completed                                                  |
| 9:05 AM | User requests administrator permissions                                        |
| 9:07 AM | Administrator permissions are granted                                          |
| 9:10 AM | User accesses a cloud storage folder containing sensitive customer information |
| 9:12 AM | User downloads 4 GB of data                                                    |
| 9:15 AM | Cloud security alert generated                                                 |

### Additional Information

* `mgarcia` normally has **read-only access**.
* The administrator permission request was **not approved by the user's manager**.
* The user has **never downloaded this amount of data before**.
* The activity is still occurring.

---

# Questions & Answers

## 1. What is the difference between authentication and authorization?

**Authentication** verifies a user's identity and answers the question, **“Who are you?”**

Examples include:

* Username and password
* Multi-factor authentication (MFA)
* Security keys
* Biometric verification, such as a fingerprint or facial scan

**Authorization** determines what an authenticated user is allowed to access or do and answers the question, **“What are you allowed to do?”**

For example, authorization may determine whether a user can view sensitive data, download files, create accounts, or change administrator permissions.

---

## 2. Which events in the scenario are most concerning, and why?

The most concerning events are:

* User `mgarcia` requested and received administrator permissions.
* The permission request was not approved by the user's manager.
* The user accessed a cloud storage folder containing sensitive customer information.
* The user downloaded 4 GB of data, which is unusual for this account.
* The activity is still occurring.

These events are concerning because they show an unauthorized increase in privileges followed by unusual access to sensitive information and a large data download.

---

## 3. Why is the principle of least privilege important in this scenario?

The principle of least privilege is important because user `mgarcia` normally has read-only access. Granting administrator permissions provided access beyond what the user normally needs for their role.

The privilege increase may have enabled access to sensitive customer information and contributed to the unusual 4 GB data download. Limiting users to only the permissions required for their jobs helps reduce the risk of unauthorized access and data exposure.

---

## 4. Would you escalate this alert? Why or why not?

Yes, I would escalate this alert because administrator permissions were granted without the user's manager approving the request. The user then accessed sensitive customer information and downloaded an unusually large amount of data while the activity was still ongoing.

Although the activity has not yet been confirmed as malicious, the unauthorized privilege increase, sensitive data access, unusual download volume, and ongoing activity create enough risk to require immediate escalation.

---

## 5. What evidence would you collect before taking action?

Before taking action, I would collect:

* The device and IP address used to access the cloud account.
* Cloud authentication and login logs.
* MFA details and authentication history.
* Information about who granted the administrator permissions.
* The reason or process used to grant the permissions.
* Cloud audit logs showing permission changes.
* Details about which customer files or data were accessed.
* Information about what data was downloaded and where it was transferred.
* Whether `mgarcia` was the person who performed the activity.
* Previous account activity to determine whether this behavior is unusual.
* Any related alerts involving other users, devices, or cloud resources.

---

## 6. What containment action might be appropriate?

I would temporarily suspend the user's cloud session or account and revoke the newly granted administrator permissions while preserving the relevant evidence. The organization should verify the user's identity and determine whether the activity was authorized before restoring access.

Additional containment actions may include blocking suspicious sessions or IP addresses and temporarily restricting access to sensitive cloud resources, following the organization's incident-response procedures.

---

## 7. SOC Analyst Summary

Cloud security monitoring identified user `mgarcia`, who normally has read-only access, receiving unapproved administrator permissions and then accessing sensitive customer information. The account downloaded 4 GB of data, which is unusual for the user, and the activity remained ongoing. The alert should be escalated, with the elevated permissions and active session temporarily restricted while authentication, permission, and data-access logs are investigated.

---

# What I Learned

This mission taught me that cloud IAM controls who can access cloud resources and what actions they are authorized to perform. I learned the difference between authentication and authorization and why the principle of least privilege is important for reducing unnecessary access. I also learned that an unauthorized privilege increase followed by unusual access to sensitive data may require immediate investigation, containment, and escalation.
