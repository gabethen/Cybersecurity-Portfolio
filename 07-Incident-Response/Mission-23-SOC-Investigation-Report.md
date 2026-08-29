# Mission 23 — SOC Investigation Report

## 1. Investigation Overview

This report consolidates the security investigations completed during Week 7, focusing on incident response fundamentals, suspicious authentication activity, and Windows Security Event Log analysis.

The investigations progressed from a simulated SIEM alert involving a potentially compromised user account to a hands-on investigation of Windows authentication events in a Windows virtual machine.

The primary objective was to determine whether authentication activity appeared normal, suspicious, or potentially malicious by examining the available evidence and correlating related events.

The investigations demonstrated the importance of analyzing authentication attempts in context rather than treating individual security alerts as confirmed incidents. Relevant factors included failed and successful authentication attempts, login times, source addresses, account types, logon types, and related Windows events.

The overall approach throughout Week 7 was to:

* Identify suspicious activity.
* Collect and examine relevant evidence.
* Correlate related security events.
* Compare activity against expected behavior.
* Assess the likelihood of malicious activity.
* Avoid making conclusions unsupported by available evidence.
* Recommend additional investigation or response actions when appropriate.

The investigations reinforced the role of a SOC analyst in distinguishing between security alerts, suspicious activity, and confirmed security incidents through evidence-based analysis.
## 2. Mission 20 — Incident Response Fundamentals

### Scenario

A SIEM generated an alert at 2:14 AM indicating that user `jsmith` successfully authenticated to their account. The login originated from an unfamiliar IP address and was followed by multiple failed login attempts. Shortly afterward, the account accessed a sensitive internal application that the user does not normally access.

### Initial Classification

The activity was classified as an **alert requiring investigation**, rather than an immediately confirmed security incident.

The alert identified potentially suspicious authentication activity, but additional evidence was required to determine whether the activity was malicious or had a legitimate explanation.

### Suspicious Indicators

Several factors increased the level of concern:

* Authentication activity occurred at an unusual time.
* The login originated from an unfamiliar IP address.
* Multiple failed authentication attempts occurred.
* The account subsequently accessed a sensitive internal application.
* The application was not normally associated with the user's activity.

These indicators could be consistent with credential-based attacks, including password guessing or brute-force activity.

### Investigation Priorities

The next investigative steps would include reviewing:

* Source IP address and reputation
* User authentication history
* Login locations and timestamps
* The user's normal activity patterns
* Applications accessed after authentication
* Any sensitive data accessed, modified, or downloaded
* Other activity associated with the account or source IP

### Response Considerations

If additional evidence confirmed that the account had been compromised, the appropriate response would be to follow the organization's incident response procedures. Depending on authorization and organizational policy, containment could include disabling the account or resetting its credentials.

The scope of the activity would then need to be determined, findings documented, and the incident escalated as required.

### Assessment

The key decision was **not to immediately declare a confirmed security incident**.

A SOC analyst should avoid assuming that suspicious authentication activity is automatically malicious. Multiple failed logins can have legitimate explanations, such as a user repeatedly entering an incorrect password.

Additional evidence and contextual analysis are required before making a final determination.

### Key Lesson

A security alert is an indication that activity requires investigation, not proof that a security incident has occurred. Effective incident response depends on collecting evidence, establishing context, and making decisions based on the available facts.

### Skills Demonstrated

* Alert triage
* Incident classification
* Authentication investigation
* IP address investigation
* Account compromise analysis
* Incident response fundamentals
* Evidence-based decision making

## 3. Mission 21 — Suspicious Authentication Investigation

### Scenario

A SIEM alert showed that user `jsmith` experienced 12 failed login attempts between 2:14 AM and 2:19 AM, followed by a successful authentication.

The successful login originated from an unfamiliar IP address outside the organization's known IP ranges. At 2:23 AM, the account accessed the company's HR application.

### Evidence Identified

The following indicators increased the level of concern:

* 12 failed login attempts within approximately five minutes.
* A successful login occurred after the failed attempts.
* Authentication occurred during an unusual time period.
* The source IP was unfamiliar and outside the organization's known IP ranges.
* The account accessed a sensitive HR application shortly after authentication.
* The activity was inconsistent with the user's normal working hours of approximately 8 AM to 5 PM.

### Authentication Analysis

The sequence of failed authentication attempts followed by a successful login was particularly important.

This pattern could be consistent with password guessing or brute-force activity in which an attacker eventually obtained valid credentials. However, the available evidence alone was not sufficient to conclusively prove that the account had been compromised.

The unusual login time and unfamiliar source IP increased the risk level because they did not match the user's established behavior.

### IP Investigation

The source IP would require additional investigation to determine:

* Geographic location
* Ownership
* Reputation
* Previous malicious activity
* Whether it was associated with a VPN or proxy
* Whether other organizational accounts had authenticated from the same address
* Whether the IP had previously interacted with the organization's environment

### Post-Authentication Activity

The access to the HR application at 2:23 AM was significant because it involved a sensitive internal application shortly after the suspicious authentication.

Further investigation would be required to determine whether the account accessed, modified, or downloaded sensitive HR information.

### Final Assessment

The activity was classified as:

**Suspicious Activity — Continue Monitoring**

The combination of repeated failed authentication attempts, successful authentication, an unfamiliar external IP address, unusual login time, and subsequent access to a sensitive HR application created multiple indicators of potential account compromise.

However, the evidence available at this stage did not conclusively establish that the activity was malicious.

### Recommended Next Steps

A SOC analyst should continue investigating:

1. The source IP address and reputation.
2. The user's authentication history.
3. The device associated with the login.
4. Applications and resources accessed after authentication.
5. Any sensitive information accessed or downloaded.
6. Other accounts associated with the same IP address.
7. Additional authentication and endpoint events surrounding the incident.

If additional evidence confirmed unauthorized activity, the alert should be escalated and the organization's incident response procedures initiated.

### Key Lesson

Suspicious activity should be evaluated using multiple pieces of evidence rather than a single event. Correlating authentication attempts, timestamps, IP information, user behavior, and post-authentication activity allows a SOC analyst to make a more informed assessment.

### Skills Demonstrated

* SIEM alert investigation
* Authentication analysis
* IP address investigation
* User behavior analysis
* Alert triage
* Incident classification
* Account compromise investigation
* Evidence-based decision making
* Incident response fundamentals

## 4. Mission 22 — Windows Authentication Investigation

### Objective

The objective was to investigate Windows Security Event ID 4625, representing a failed logon, and correlate it with nearby authentication and system activity to determine whether the behavior appeared normal or suspicious.

### Initial Event

The investigated Event ID 4625 contained the following information:

* **Date/Time:** August 20, 2026 — 4:51:33 PM
* **Event ID:** 4625
* **Account Name:** `WIN-I6R6VVP4E7I$`
* **Logon Type:** 2
* **Failure Reason:** Unknown user name or bad password
* **Workstation Name:** `WIN-I6R6VVP4E7I`
* **Source Network Address:** `127.0.0.1`

### Event Correlation

A successful Event ID 4624 was identified shortly afterward at **4:53:37 PM**.

The successful authentication used **Logon Type 5**, indicating a service logon rather than an interactive user login.

The failed authentication showed `127.0.0.1` as the source network address, which is the local loopback address. The successful authentication had a blank source network address.

### Account Analysis

Both the failed and successful authentication events involved the same account:

`WIN-I6R6VVP4E7I$`

The `$` at the end of the account name is an important indicator because it suggests that the account is likely a **computer or machine account rather than a normal human user account**.

This changed the interpretation of the failed authentication event. A failed login involving a machine account should not automatically be interpreted in the same way as a failed login involving a normal user account.

### Additional Events

Additional Windows Security events were identified during the investigation:

* **Event ID 4672** — Special privileges assigned to a new logon.
* **Event ID 4688** — A new process was created.

These events provide additional context but require further investigation to determine whether the associated activity was expected.

The process recorded in Event ID 4688 should be identified and evaluated to determine whether it was a legitimate Windows or application process.

### Assessment

The Event ID 4625 did **not provide sufficient evidence to classify the activity as malicious or as a confirmed security incident**.

The local loopback address, machine-account naming convention, and subsequent Logon Type 5 authentication provide plausible explanations for the activity.

However, the event should not automatically be dismissed as a normal authentication failure.

### Recommended Investigation

The next investigative steps would include:

1. Identify the service associated with `WIN-I6R6VVP4E7I$`.
2. Examine the Event ID 4688 process creation event.
3. Determine whether the process was expected.
4. Correlate additional authentication events from the same system.
5. Review the surrounding Windows Security and System logs.
6. Determine whether any unexpected privileged activity occurred.

### Final Assessment

**Assessment: Suspicious Activity Requiring Additional Context**

The available evidence does not establish malicious activity. However, additional correlation is appropriate because the investigation involved a failed authentication, a subsequent successful service logon, special privileges, and process creation.

The investigation demonstrates why individual Windows events should be evaluated within their surrounding context rather than analyzed in isolation.

### Key Lesson

A single Event ID 4625 does not automatically indicate an attack. Account type, logon type, source address, related events, and surrounding system activity must be considered before determining whether authentication behavior is legitimate or suspicious.

### Skills Demonstrated

* Windows Security Event Log analysis
* Event ID 4625 investigation
* Event ID 4624 correlation
* Logon Type analysis
* Source address analysis
* Machine account identification
* Event correlation
* Privilege analysis
* Process creation analysis
* Incident assessment
* Security investigation documentation

## 5. Evidence Correlation

The Week 7 investigations demonstrated how correlating multiple pieces of evidence can provide a more accurate assessment than analyzing individual security events in isolation.

### Mission 20 Correlation

Mission 20 introduced the concept of investigating a suspicious authentication alert before determining whether it represented a confirmed security incident.

The primary indicators were:

* Unusual authentication time
* Unfamiliar source IP
* Multiple failed authentication attempts
* Access to a sensitive internal application

The investigation demonstrated that these indicators were sufficient to warrant investigation but not enough by themselves to confirm compromise.

### Mission 21 Correlation

Mission 21 provided additional context and demonstrated how multiple suspicious indicators can increase confidence that an event may represent an account compromise.

The sequence was:

**12 failed login attempts → successful authentication → unfamiliar external IP → sensitive HR application access**

The combination of these events was significantly more concerning than any individual event.

The unusual time of the authentication and the unfamiliar IP address were inconsistent with the user's normal behavior, while the subsequent HR application access increased the potential impact.

Additional investigation was still required before declaring a confirmed incident.

### Mission 22 Correlation

Mission 22 demonstrated event correlation using actual Windows Security logs.

The investigation followed this sequence:

**Event ID 4625 → Event ID 4624 → Event ID 4672 → Event ID 4688**

The failed authentication was followed by a successful service logon involving the same apparent machine account. Additional privilege-assignment and process-creation events provided further context.

Unlike Mission 21, the evidence in Mission 22 did not strongly indicate an external account compromise. The local loopback address and machine-account naming convention provided plausible explanations for the authentication activity.

### Overall Correlation

The three investigations demonstrate an important SOC principle:

**The significance of a security event depends on its context.**

A failed authentication attempt by itself may be harmless. Multiple failed attempts followed by a successful authentication from an unfamiliar external IP and access to a sensitive application is considerably more concerning.

Similarly, a failed Windows authentication involving a machine account and the local system should be interpreted differently from a suspicious external user authentication.

Effective investigation therefore requires correlating:

* Authentication events
* Account identity
* Account type
* Logon type
* Source address
* Timestamp
* User behavior
* Application activity
* Privilege assignments
* Process creation
* Other related security events

### Analyst Takeaway

The investigations reinforced the importance of **evidence correlation before classification**.

Rather than asking whether a single event is malicious, a SOC analyst should ask:

> **What happened before and after this event, and does the combined evidence indicate abnormal or unauthorized activity?**

This approach reduces false positives, improves investigation accuracy, and supports better incident response decisions.

## 6. Threat Assessment

The Week 7 investigations produced different levels of security concern depending on the surrounding evidence.

### Mission 20

The Mission 20 activity was classified as an alert requiring investigation. Although the unusual login time, unfamiliar IP address, failed authentication attempts, and sensitive application access were concerning, there was not enough evidence to confirm account compromise.

**Threat Level: Suspicious — Further Investigation Required**

### Mission 21

Mission 21 presented the highest level of concern. The combination of 12 failed login attempts, a successful authentication, an unfamiliar external IP address, unusual login time, and subsequent HR application access was consistent with possible credential compromise.

However, no definitive evidence of compromise was established.

**Threat Level: High Suspicion — Escalation Recommended if Additional Evidence Confirms Unauthorized Activity**

### Mission 22

Mission 22 presented a different situation. The authentication involved what appeared to be a machine account, the source address was the local loopback address, and the successful authentication used Logon Type 5.

These factors provided plausible legitimate explanations, although the associated privilege and process events warranted additional review.

**Threat Level: Low to Moderate Suspicion — Additional Context Required**

### Overall Threat Assessment

The investigations demonstrate that threat severity should be based on the totality of available evidence rather than a single security event.

---

## 7. Recommended Analyst Actions

Based on the evidence reviewed during Week 7, the following actions would be appropriate during a real SOC investigation:

### For Suspicious User Authentication

* Investigate the source IP address and reputation.
* Review the user's recent authentication history.
* Determine whether the login location is expected.
* Review the device associated with the authentication.
* Examine activity following the successful login.
* Determine whether sensitive information was accessed or downloaded.
* Search for other accounts communicating with or authenticating from the same IP.
* Escalate the investigation if evidence of unauthorized access is identified.

### For the Windows Machine Account

* Identify the service associated with `WIN-I6R6VVP4E7I$`.
* Review the Event ID 4688 process creation event.
* Determine whether the process was expected.
* Review Event ID 4672 for the associated privileged logon.
* Correlate additional Security and System events.
* Investigate repeated authentication failures if they continue occurring.

### Incident Response Considerations

If evidence confirms account compromise, response actions should follow organizational procedures and authorization requirements. Possible actions may include credential resets, account containment, endpoint investigation, evidence preservation, and escalation to the appropriate incident response team.

---

## 8. Final Assessment

The Week 7 investigations demonstrate that authentication events must be evaluated within their surrounding context.

Mission 20 established the foundation for distinguishing an alert from a confirmed incident.

Mission 21 demonstrated how multiple authentication indicators can significantly increase suspicion. The combination of repeated failed logins, successful authentication, unusual timing, an unfamiliar external IP address, and sensitive application access represented a potentially serious account compromise scenario.

Mission 22 demonstrated the importance of Windows event correlation. The Event ID 4625 failed authentication could not be evaluated independently. The associated account type, local loopback address, subsequent Event ID 4624 service logon, Event ID 4672 privilege assignment, and Event ID 4688 process creation provided additional context.

Based on the evidence available, **no confirmed security incident was established during these investigations**.

The appropriate analyst approach was to document the evidence, assess the level of suspicion, identify additional investigative requirements, and avoid making unsupported conclusions.

---

## 9. Lessons Learned

### 1. Alerts Are Not Automatically Incidents

A SIEM alert identifies activity that requires investigation. It does not automatically prove that malicious activity occurred.

### 2. Context Is Critical

Authentication events become more meaningful when analyzed alongside timestamps, source addresses, account types, logon types, and subsequent activity.

### 3. Event Correlation Improves Accuracy

Correlating multiple events can reveal patterns that are not visible when examining individual events independently.

### 4. Account Type Matters

A failed authentication involving a machine account can have a very different meaning from a failed authentication involving a normal user account.

### 5. Avoid Premature Conclusions

A SOC analyst should distinguish between suspicious behavior and confirmed malicious activity. Conclusions should be supported by available evidence.

### 6. Documentation Is Part of Incident Response

Clearly documenting observations, evidence, analysis, and recommended actions creates an investigation record that can be reviewed by other analysts and security teams.

### 7. Investigation Should Be Evidence-Based

The goal of an investigation is not simply to determine whether an event "looks bad." The analyst should determine what happened, establish context, identify inconsistencies, correlate related evidence, and make an assessment based on the available facts.

---

## 10. Skills Demonstrated

* SIEM alert triage
* Incident response fundamentals
* Incident classification
* Authentication investigation
* Windows Security Event Log analysis
* Event ID 4624 analysis
* Event ID 4625 analysis
* Event ID 4672 analysis
* Event ID 4688 analysis
* Logon Type analysis
* Machine account identification
* Source IP analysis
* User behavior analysis
* Event correlation
* Account compromise assessment
* Threat assessment
* Evidence-based decision making
* Security investigation documentation
* Incident response recommendations
* SOC analyst reporting

---

# Mission 23 Completion Summary

Week 7 demonstrated a progression from basic incident-response decision making to detailed authentication investigation and hands-on Windows event correlation.

The investigations reinforced the importance of **collecting evidence, correlating events, establishing context, and avoiding unsupported conclusions**.

These skills form a foundation for SOC analysts responsible for monitoring security alerts, investigating suspicious activity, and determining when escalation or incident response is appropriate.
