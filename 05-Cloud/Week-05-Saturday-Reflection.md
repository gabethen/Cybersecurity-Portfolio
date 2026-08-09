# Week 05 - Saturday Reflection

## Cloud Security

### 1. What was the most important cloud security concept you learned this week?

The most important cloud security concepts I learned this week were the differences between IaaS, PaaS, and SaaS and the importance of cloud logs for a SOC analyst. Understanding the different cloud service models helps me understand who is responsible for different parts of the environment, while cloud logs provide evidence that can be used during investigations.

---

### 2. How has your understanding of cloud security changed since the beginning of the week?

My understanding of cloud security has changed because I now have a better understanding of cloud computing and the responsibilities shared between the cloud provider and the customer. I also have a better understanding of how users, permissions, data, and cloud activity can create security risks that a SOC analyst needs to investigate.

---

### 3. Why is IAM important to a SOC analyst?

Identity and Access Management is important to a SOC analyst because it helps determine who has access to cloud resources and what actions they are authorized to perform. IAM information can help an analyst identify unusual login activity, unauthorized permission changes, privilege escalation, and suspicious access to sensitive resources.

---

### 4. Why is the principle of least privilege important?

The principle of least privilege is important because users should only receive the permissions necessary to perform their jobs. Limiting unnecessary access reduces the potential impact if an account is compromised or misused.

---

### 5. What makes cloud activity suspicious?

Cloud activity may become suspicious when it differs from a user's normal behavior. Examples include:

* Unusual login locations.
* Unexpected privilege changes.
* Access to sensitive information.
* Large or unusual downloads.
* Activity outside a user's normal behavior.
* Unauthorized changes to accounts or cloud resources.
* Access to resources that are unrelated to the user's job responsibilities.

---

### 6. Which cloud security topic do you still want more practice with?

I would like more practice understanding how to prevent cloud security incidents and data leaks. I want to become better at identifying what to look for in cloud activity and understanding what actions a SOC analyst should take when suspicious activity is discovered.

---

# Weekly Scenario

## 7. Would you consider this a high-priority investigation? Why?

Yes, I would consider this a high-priority investigation because the user normally has read-only access but received administrator permissions without a documented request. The user then accessed sensitive customer information and downloaded 4 GB of data, which is unusual for the account. The combination of the privilege increase, sensitive data access, and unusually large download creates a significant security concern.

---

## 8. What would you investigate first?

I would investigate:

* Who the user is.
* What device was used.
* Who granted the administrator permissions.
* Whether the permission change was authorized.
* What IP address and location were associated with the login.
* What data was accessed and downloaded.
* Whether the activity matches the user's normal behavior.

---

## 9. What evidence would you collect?

I would collect:

* Username and account information.
* Device information.
* IP address and login location.
* Authentication and MFA logs.
* Details about the data that was downloaded.
* Cloud audit logs showing who granted the permissions.
* Permission and role-change records.
* Data access logs.
* Previous user activity for comparison.

---

## 10. What containment action might you recommend?

I would recommend temporarily revoking the unauthorized administrator permissions and restricting the user's cloud access while the investigation continues. I would also consider isolating the device if there is evidence that it may be compromised, then escalate the incident and preserve relevant evidence before making additional changes.

---

## 11. In 2–3 sentences, explain what you learned about cloud security this week.

I learned that cloud providers and customers share security responsibilities depending on the service model. I also learned that IAM and cloud logs are important tools for SOC analysts because they help identify who accessed resources, what permissions they had, what actions they performed, and whether their behavior was unusual or potentially malicious.

---

# Week 05 Overall Reflection

This week helped me understand that cloud security is not simply about protecting a server or network. It also involves understanding identities, permissions, data access, cloud service models, and user behavior. I am still at a beginner stage with cloud security, but I now have a better foundation for understanding how a SOC analyst investigates suspicious cloud activity.
