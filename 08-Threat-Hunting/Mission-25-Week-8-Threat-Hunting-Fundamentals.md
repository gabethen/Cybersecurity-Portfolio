# Mission 25 — Week 8 Threat Hunting Fundamentals

## Objective

Learn the fundamentals of threat hunting and understand how threat hunting differs from traditional alert-driven incident response.

The primary objective was to understand how a SOC analyst can proactively search for potentially malicious activity that may have bypassed existing security detections.

Threat hunting is a proactive, hypothesis-driven process in which analysts search security data for evidence of suspicious or malicious behavior rather than waiting for an alert. :contentReference[oaicite:0]{index=0}

---

## 1. What Is Threat Hunting?

Threat hunting is the proactive process of searching an environment for signs of malicious or suspicious activity that may not have triggered an existing security alert.

A traditional SOC workflow often looks like:

**Alert → Investigate → Determine if Malicious**

Threat hunting changes the workflow to:

**Hypothesis → Search → Find Evidence → Investigate → Determine Risk**

Instead of waiting for a SIEM to identify suspicious activity, a threat hunter asks:

> "What could an attacker be doing in this environment that our existing detections might not identify?"

Threat hunting is generally human-led, proactive, and hypothesis-driven. :contentReference[oaicite:1]{index=1}

---

## 2. Why Threat Hunting Matters

Attackers do not always trigger obvious security alerts.

An attacker who obtains legitimate credentials may:

1. Log in normally.
2. Use legitimate tools.
3. Move through the environment.
4. Access sensitive applications.
5. Collect information.
6. Attempt to avoid triggering existing detections.

A SOC that only investigates alerts may miss this type of activity.

Threat hunting allows analysts to proactively search for behavioral patterns that may indicate compromise.

---

## 3. Threat Hunting vs. Incident Response

| Incident Response | Threat Hunting |
|---|---|
| Usually begins with an alert or reported incident | Begins with a hypothesis or question |
| Reactive | Proactive |
| Investigates known suspicious activity | Searches for potentially hidden activity |
| Determines scope and responds | Searches for threats that may have evaded detection |
| Often time-sensitive | Can be performed continuously |

### Example

**Incident Response:**

> SIEM detected 20 failed logins from an external IP. Investigate the activity.

**Threat Hunting:**

> Have any accounts in our environment authenticated from unusual locations during normally inactive hours?

The first example responds to an existing alert.

The second proactively searches for suspicious behavior.

---

## 4. Threat Hunting Hypothesis

A threat hunt normally begins with a hypothesis.

A hypothesis is a specific and testable statement about potentially malicious activity.

Example:

> **"An attacker may be using compromised credentials to access internal systems outside the user's normal working hours."**

The analyst then determines what evidence could support or weaken the hypothesis.

Potential data sources include:

- Authentication logs
- Windows Security logs
- VPN logs
- Endpoint telemetry
- DNS logs
- Firewall logs
- SIEM data
- Cloud authentication logs

A strong hypothesis gives the hunt direction and helps define the data sources, scope, and evidence required for the investigation. :contentReference[oaicite:2]{index=2}

---

## 5. Threat Hunting Using Week 7 Knowledge

The authentication investigations from Week 7 can be used as a foundation for threat hunting.

A possible hypothesis could be:

> **"Compromised credentials may be being used to access sensitive applications outside normal working hours."**

A threat hunter could search for:

- Successful logins between 12 AM and 5 AM
- Users authenticating from unfamiliar IP addresses
- Multiple failed attempts followed by successful authentication
- Sensitive application access immediately after authentication
- Large downloads following unusual authentication activity

This demonstrates how previously learned SOC investigation techniques can be applied proactively.

---

## 6. Threat Hunting Process

A basic threat hunt can follow these steps:

### 1. Create a Hypothesis

Determine what suspicious behavior is being investigated.

### 2. Identify Data Sources

Determine where evidence of the suspected behavior would appear.

### 3. Search

Search relevant security telemetry for activity matching the hypothesis.

### 4. Analyze

Determine whether the results represent normal or abnormal activity.

### 5. Investigate

If suspicious activity is discovered, investigate the surrounding evidence.

### 6. Document

Record the hypothesis, data sources, searches, findings, and conclusion.

### 7. Improve Detection

If the hunt identifies useful indicators or behaviors, the results can be used to improve automated detections.

Threat hunting can therefore contribute to better detection coverage by identifying gaps in existing security controls. :contentReference[oaicite:3]{index=3}

---

# Knowledge Check

## Scenario

There have been no alerts involving compromised accounts.

A threat hunter creates the following hypothesis:

> **"An attacker may be using compromised credentials to access employee accounts outside normal working hours."**

Authentication logs are searched and the following activity is discovered:

```text
User: jsmith
Time: 2:31 AM
Source IP: 185.XX.XX.42
Result: Successful Login
Normal Hours: 8 AM–5 PM
Previous IP: Corporate Network
