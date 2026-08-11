# Week 05 - Sunday Review

## Cloud Security

### 1. What is the difference between IaaS, PaaS, and SaaS?

**IaaS (Infrastructure as a Service)** provides customers with cloud infrastructure such as virtual machines, storage, and networking. The cloud provider manages the underlying infrastructure while the customer manages the operating system, applications, and configurations.

**PaaS (Platform as a Service)** allows customers to develop and run applications while the cloud provider manages the underlying infrastructure and platform.

**SaaS (Software as a Service)** provides customers with ready-to-use applications. The cloud provider manages the application and most of the underlying infrastructure, while the customer is primarily responsible for users, access, and data security.

---

### 2. What is the shared responsibility model?

The shared responsibility model means that cloud security responsibilities are divided between the cloud provider and the customer.

I think of cloud security like renting an apartment: the landlord keeps the building secure, but you are responsible for locking your own door and protecting your belongings. In the same way, the cloud provider protects the physical infrastructure, while the customer is responsible for protecting their data, accounts, passwords, configurations, applications, and access.

---

### 3. What is the difference between authentication and authorization?

**Authentication** verifies a user's identity and answers, **"Who are you?"**

**Authorization** determines what resources and actions a user is allowed to access or perform and answers, **"What are you allowed to do?"**

---

### 4. Why is the principle of least privilege important?

The principle of least privilege is important because users should only have the access required to perform their jobs. Limiting unnecessary permissions reduces the potential impact of a compromised or misused account.

---

### 5. What types of cloud logs would you review during an investigation?

**Authentication logs** can help identify who logged in, when they logged in, where they logged in from, and how they authenticated.

**Audit logs** provide a record of administrative and system actions, helping analysts determine who did what, when, and sometimes from where.

**Data access logs** can show when data was viewed, copied, modified, downloaded, or otherwise accessed.

---

### 6. What cloud activity would make you suspicious?

Examples of suspicious cloud activity include:

* An unusually large file or data download.
* A user receiving permissions they do not normally need.
* Repeated unusual security alerts.
* A user accessing sensitive data outside their normal responsibilities.
* Login activity from an unusual location.
* Unexpected administrator or privilege changes.
* Activity that differs significantly from the user's normal behavior.

---

### 7. Why is it important to understand a user's normal behavior?

Understanding a user's normal behavior helps SOC analysts identify unusual activity. For example, if a user who normally has read-only access suddenly receives administrator permissions and downloads a large amount of sensitive data, that deviation from normal behavior can indicate a potential security issue.

---

# Sunday Investigation Challenge

## 8. What are the three most concerning events?

The three most concerning events are:

1. The user received administrator permissions without an approved change request.
2. The user accessed sensitive HR information despite normally working in Marketing.
3. The user downloaded 4 GB of data, which is the largest download ever recorded for the account.

The fact that the activity is still occurring makes the situation even more urgent.

---

## 9. Would you escalate this? Why?

Yes, I would escalate this investigation because the user received unauthorized elevated privileges, accessed sensitive information outside their normal job responsibilities, and downloaded an unusually large amount of data. The activity is also still occurring, which increases the urgency and potential impact of the situation.

---

## 10. What would you investigate first?

I would first determine exactly what data was accessed and downloaded, who performed the activity, and which device and session were involved. I would then investigate why the administrator permissions were granted and whether the activity was authorized.

---

## 11. What evidence would you collect?

I would collect:

* The device and IP address used to access the cloud account.
* Cloud authentication and login logs.
* Audit logs showing when and how administrator permissions were granted.
* The identity of the person or process that granted the permissions.
* Details about the data that was accessed and downloaded.
* The reason or process used to grant the permissions.
* Whether `mgarcia` was actually the person who performed the activity.
* Previous account activity to determine whether this behavior is unusual.
* Any related alerts involving other users, devices, or cloud resources.

---

## 12. What containment action would you recommend?

I would temporarily suspend the user's cloud session and revoke the unauthorized administrator access while preserving the relevant evidence. Additional restrictions could be applied if the investigation shows that the device or account has been compromised.

---

## 13. SOC Analyst Summary

A cloud security alert identified user `mgarcia`, who normally has read-only access, receiving administrator permissions without an approved change request. The user then accessed sensitive HR information and downloaded 4 GB of data, the largest download ever recorded for the account, despite normally working in Marketing. Because the activity is still occurring and represents a significant deviation from normal behavior, the incident should be escalated and the elevated access temporarily restricted.

---

# 14. What is the biggest thing you learned about cloud security this week?

The biggest thing I learned about cloud security this week is the importance of gathering evidence and knowing where to look for it. I learned that cloud investigations can involve authentication logs, audit logs, data access logs, user behavior, permissions, devices, and IP addresses. Understanding where to find this information helps a SOC analyst investigate an alert without making assumptions.

---

# Week 05 Overall Review

Week 5 helped me build a foundation in cloud security. I learned about IaaS, PaaS, SaaS, the shared responsibility model, IAM, least privilege, and cloud logging.

More importantly, I learned how these concepts connect during a security investigation. A SOC analyst needs to understand who accessed a cloud environment, what permissions they had, what changed, what data they accessed, whether the activity was normal, and what evidence can be collected before taking action.

I still want more hands-on practice with cloud security, especially learning how to identify and respond to potential cloud data leaks and compromised accounts.
