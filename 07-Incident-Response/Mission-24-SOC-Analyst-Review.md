# Mission 24 — SOC Analyst Review

## Objective

Review the key concepts and investigation techniques learned during Week 7, including alert triage, authentication analysis, Windows Security Event Logs, event correlation, threat assessment, and evidence-based incident classification.

The objective was to demonstrate the ability to analyze multiple security indicators together and determine the appropriate level of response without making unsupported conclusions.

---

## Scenario 1 — Suspicious Authentication Activity

### Scenario

User `mgarcia` had 8 failed login attempts from an unfamiliar IP address at 1:47 AM, followed by a successful login. The account then accessed the company's payroll application.

The user's normal working hours were 8 AM–5 PM, and the user normally connected from the corporate network.

### 1. Classification

I classified the activity as:

**Suspicious Activity — Further Investigation Required**

The SIEM generated an alert, but the available evidence was not sufficient to immediately confirm a security incident.

The combination of unusual login time, unfamiliar IP address, multiple failed login attempts, and access to a sensitive payroll application warranted further investigation.

### 2. Major Red Flags

* 8 failed login attempts
* Unfamiliar IP address
* Access to the payroll application
* Login at 1:47 AM
* Activity outside the user's normal corporate network

### 3. Investigation Priorities

I would investigate:

* Source IP address and reputation
* User authentication history
* User and device information
* Timeline of activity
* Payroll application activity
* Endpoint and security logs
* Whether the user was legitimately working at the time

### Analyst Lesson

Suspicious authentication activity should be investigated using multiple sources of evidence before determining whether an account has been compromised.

---

## Scenario 2 — Windows Authentication Investigation

### Scenario

The following Windows Security events were identified:

| Time       | Event ID | Activity                    |
| ---------- | -------: | --------------------------- |
| 3:12:41 PM |     4625 | Failed logon                |
| 3:13:02 PM |     4624 | Successful logon            |
| 3:13:02 PM |     4672 | Special privileges assigned |
| 3:13:05 PM |     4688 | New process created         |

The account was:

`WIN-PC01$`

The failed authentication showed:

`127.0.0.1`

The successful authentication used:

**Logon Type 5**

### 1. Important Observations

The sequence of events stood out:

**4625 → 4624 → 4672 → 4688**

The privilege assignment and process creation events required additional investigation.

### 2. Account Analysis

The `$` at the end of `WIN-PC01$` suggests that the account is likely a computer or machine account rather than a normal human user account.

### 3. Logon Type Analysis

Logon Type 5 indicates a **service logon** rather than an interactive user login.

### 4. Malicious Activity Assessment

The available evidence does not prove malicious activity.

The machine-account naming convention, local loopback address, and service logon provide plausible legitimate explanations.

However, the activity should not automatically be considered benign because the associated privilege assignment and process creation events require additional context.

### 5. Next Investigation Steps

I would investigate:

1. Event ID 4672 to determine which privileges were assigned.
2. Event ID 4688 to identify the process that was created.
3. Whether the process was expected and legitimate.
4. Which service was associated with the machine account.
5. Additional Windows Security and System events.

### Analyst Lesson

Individual Windows events should be analyzed in context. A failed Event ID 4625 does not automatically indicate malicious activity.

---

## Scenario 3 — High-Risk Authentication Activity

### Scenario

User `jsmith` experienced:

* 12 failed login attempts
* Successful authentication
* Unfamiliar external IP address
* Login at 2:14 AM
* Access to the HR/payroll application
* 4 GB data download
* PowerShell execution shortly after login

### 1. Classification

I initially considered this a **confirmed security incident** because of the large number of suspicious indicators.

After further analysis, the more appropriate SOC classification is:

**High-Confidence Suspicious Activity / Probable Security Incident — Immediate Escalation and Investigation Required**

The evidence is extremely concerning, but confirmation should be based on establishing that the activity was unauthorized or malicious.

### 2. Most Concerning Indicators

The three most concerning indicators were:

1. **4 GB data download from HR/payroll**
2. **PowerShell execution immediately after suspicious authentication**
3. **12 failed login attempts followed by successful authentication from an unfamiliar external IP at 2:14 AM**

The unusual login time and sensitive application access were additional supporting indicators.

### 3. Immediate Investigation and Response Priorities

I would:

* Investigate the source IP address.
* Review the user's authentication history.
* Identify the device used for authentication.
* Investigate the PowerShell execution.
* Determine what HR/payroll data was accessed.
* Determine what information was included in the 4 GB download.
* Search for other accounts associated with the source IP.
* Review endpoint and network activity.
* Preserve relevant logs and evidence.
* Escalate according to incident response procedures.
* Consider account containment or credential reset if authorized and supported by the investigation.

### 4. Evidence Needed for Confirmation

Before documenting the activity as a confirmed incident, I would want additional evidence including:

* Windows Security and authentication logs
* Source IP information
* Device information
* Authentication history
* Confirmation of whether `jsmith` was legitimately working at the time
* PowerShell execution details
* Endpoint security alerts
* Network activity
* Details regarding the 4 GB data transfer
* Evidence showing whether the activity was authorized or unauthorized

### Analyst Lesson

Even when multiple indicators strongly suggest compromise, a SOC analyst should distinguish between **high-confidence suspicious activity** and a **confirmed incident** until sufficient evidence establishes what actually occurred.

---

## Key Week 7 Concepts

### Alert vs. Suspicious Activity vs. Confirmed Incident

**Alert:**
A security monitoring system has identified activity that requires investigation.

**Suspicious Activity:**
Available evidence indicates abnormal or potentially malicious behavior, but additional investigation is required.

**Confirmed Incident:**
Sufficient evidence establishes that unauthorized or malicious activity has occurred.

---

## Windows Event IDs Reviewed

| Event ID | Meaning                                    |
| -------- | ------------------------------------------ |
| 4624     | Successful logon                           |
| 4625     | Failed logon                               |
| 4672     | Special privileges assigned to a new logon |
| 4688     | New process created                        |

---

## Important Windows Concepts

### Machine Accounts

A Windows account ending in `$` commonly indicates a computer or machine account.

Example:

`WIN-PC01$`

### Logon Type 5

Logon Type 5 indicates a **service logon**.

### Loopback Address

`127.0.0.1` is the local loopback address and indicates communication originating from the local system.

---

## Week 7 Investigation Method

My investigation approach is:

**1. Identify the alert**

Determine what security event or behavior triggered the investigation.

**2. Establish context**

Review the user, device, timestamp, source address, account type, and normal behavior.

**3. Correlate events**

Look for related authentication, privilege, process, endpoint, network, and application events.

**4. Assess risk**

Determine how concerning the combined evidence is.

**5. Investigate further**

Identify what additional evidence is needed to support or reject the initial hypothesis.

**6. Determine classification**

Classify the activity as an alert, suspicious activity, or confirmed incident based on available evidence.

**7. Escalate or contain when appropriate**

Follow organizational incident response procedures when evidence supports escalation or containment.

**8. Document findings**

Record observations, evidence, analysis, assessment, and recommended actions.

---

## Key Lessons Learned

### 1. Suspicious Does Not Automatically Mean Malicious

Security analysts should avoid making conclusions without sufficient evidence.

### 2. Context Matters

The same Event ID can have very different meanings depending on the account, source address, logon type, timing, and surrounding activity.

### 3. Correlation Is Critical

Multiple related events provide stronger investigative context than isolated events.

### 4. Account Type Matters

Machine accounts should be analyzed differently from normal user accounts.

### 5. Sensitive Application Access Increases Risk

Access to HR, payroll, or other sensitive systems following suspicious authentication should receive increased attention.

### 6. PowerShell Requires Context

PowerShell is a legitimate Windows administration tool, but execution following suspicious authentication and sensitive data access can significantly increase concern.

### 7. Data Transfer Can Indicate Impact

Large downloads from sensitive applications should be investigated to determine what information was transferred and whether the activity was authorized.

### 8. Documentation Is an Important SOC Skill

A strong investigation should clearly explain what happened, what evidence was found, what the evidence means, and what should happen next.

---

## Skills Demonstrated

* Alert triage
* Incident classification
* SIEM investigation
* Authentication analysis
* Windows Security Event Log analysis
* Event ID 4624 analysis
* Event ID 4625 analysis
* Event ID 4672 analysis
* Event ID 4688 analysis
* Logon Type analysis
* Machine account identification
* IP address investigation
* User behavior analysis
* Event correlation
* Threat assessment
* Account compromise investigation
* Endpoint investigation
* Evidence-based decision making
* Incident response fundamentals
* Security investigation documentation

---

## Final Week 7 Assessment

Week 7 strengthened my ability to investigate authentication-related security activity and evaluate events based on their surrounding context.

The investigations progressed from basic incident response concepts to suspicious authentication analysis and hands-on Windows Security Event Log correlation.

The primary lesson from Week 7 was that effective SOC analysis requires more than identifying individual security events. An analyst must correlate evidence, establish context, assess risk, and avoid making unsupported conclusions.

**Week 7 Status: Complete**
