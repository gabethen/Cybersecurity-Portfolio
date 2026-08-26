# Mission 26 — Windows Authentication Threat Hunt

## Objective

Investigate unusual authentication activity on a Windows system and determine whether the observed events indicate malicious activity, a potential compromise, or legitimate system behavior.

### Hunt Hypothesis

> There may be unusual authentication activity occurring on this Windows system.

---

## Environment

* **Operating System:** Windows 11 ARM64
* **Environment:** Personal Windows virtual machine
* **Log Source:** Windows Security Event Log
* **Primary Event IDs Investigated:**

  * 4624 — Successful Logon
  * 4625 — Failed Logon
  * 4688 — Process Creation

---

## Investigation Timeline

The following authentication events were identified during the investigation:

```text
5:36:25 PM
4624 — Successful Logon
Account: WIN-I6R6VVP4E7I$
Logon Type: 5
Source: Blank

        ↓ 6 seconds

5:36:31 PM
4625 — Failed Logon
Logon Type: 2
Source: 127.0.0.1

        ↓ 3 seconds

5:36:34 PM
4625 — Failed Logon
Logon Type: 2
Source: 127.0.0.1

        ↓ 7 seconds

5:36:41 PM
4625 — Failed Logon
Logon Type: 2
Source: 127.0.0.1

        ↓

No nearby 4688 process-creation event identified
```

---

## Findings

### 1. Successful Authentication

A successful Event ID 4624 occurred at approximately **5:36:25 PM**.

* **Account:** `WIN-I6R6VVP4E7I$`
* **Logon Type:** 5
* **Source Network Address:** Blank

The account name ending in `$` indicates that it appears to be a **Windows machine account**.

Logon Type 5 represents a **service logon**, making normal Windows service activity a plausible explanation.

---

### 2. Multiple Failed Authentication Attempts

Three Event ID 4625 failures occurred shortly after the successful service logon:

* **5:36:31 PM**
* **5:36:34 PM**
* **5:36:41 PM**

All three failures:

* Involved the same system context
* Used **Logon Type 2**
* Originated from **127.0.0.1**

The short time interval between the failures makes the activity noteworthy and justified further investigation.

---

### 3. Local Origin

The failed authentication attempts originated from:

`127.0.0.1`

This is the local loopback address, meaning the authentication attempts originated from the same Windows system rather than an external network address.

This reduces the likelihood that the observed activity represents a straightforward remote authentication attack.

---

### 4. Process Correlation

Event ID 4688 was investigated to determine whether a process was created around the time of the authentication activity.

No nearby 4688 process-creation event was identified around **5:36 PM** that could be confidently correlated with the authentication failures.

The absence of a corresponding process event does not prove that no process was responsible, but it means there is currently no process-creation evidence supporting malicious execution.

---

## Evidence Supporting Suspicious Activity

The following observations support continuing the investigation:

* Multiple authentication failures occurred within approximately 10 seconds.
* The failures occurred immediately after a successful authentication.
* The same machine account was involved in the activity.
* The authentication pattern was unusual enough to warrant investigation.

---

## Evidence Against Confirmed Malicious Activity

Several findings weaken the case for an active external attack or confirmed compromise:

* The account appears to be a Windows machine account.
* The successful authentication was Logon Type 5, associated with a service.
* The failed authentications originated from `127.0.0.1`.
* No nearby 4688 process-creation event was identified.
* No evidence of external network activity was identified during this investigation.

---

## Threat Assessment

**Severity:** Medium / Low
**Classification:** Suspicious Activity
**Status:** Further Investigation Required

The authentication pattern represents an anomaly that should be documented and investigated further. However, the available evidence is insufficient to classify the activity as a confirmed security incident.

---

## Analyst Conclusion

> The hunt identified an authentication anomaly consisting of a successful service logon followed by three failed interactive logon attempts originating from the local system. The account appears to be a Windows machine account, and the failed authentications originated from `127.0.0.1`. No nearby process-creation event was identified to establish a connection between the authentication activity and potentially malicious execution.
>
> Based on the available evidence, there is insufficient evidence to determine that the activity was malicious or that the system was compromised. A legitimate Windows service, configuration issue, or other local system activity remains a plausible explanation.
>
> Further investigation should focus on the machine account, services running under that account, Windows configuration, and additional authentication or system events surrounding the activity.

---

## Recommended Next Steps

If additional investigation were required, I would:

1. Identify the Windows services associated with `WIN-I6R6VVP4E7I$`.
2. Review additional 4624 and 4625 events surrounding the timeframe.
3. Investigate related Event IDs such as 4648, 4672, and 7045.
4. Review Windows System and Application logs.
5. Check for scheduled tasks or services that could generate local authentication attempts.
6. Review network events for evidence of external communication.
7. Determine whether the authentication failures recur.
8. Compare future occurrences against the same machine account and service activity.

---

## Skills Practiced

* Threat-hunting hypothesis creation
* Windows Security Event Log analysis
* Event ID 4624 analysis
* Event ID 4625 analysis
* Event ID 4688 correlation
* Logon Type analysis
* Machine-account identification
* Authentication timeline construction
* Event correlation
* Local vs. external authentication analysis
* Process-event correlation
* Evidence-based threat assessment
* Negative finding documentation
* Avoiding confirmation bias
* SOC investigation documentation

---

## Final Assessment

**🟡 Suspicious Activity — Further Investigation Required**

The investigation identified a legitimate authentication anomaly, but the evidence does not support declaring a confirmed compromise.

The key lesson from this hunt is that **an anomaly is not automatically an incident**. A SOC analyst should document both the evidence supporting suspicion and the evidence that weakens the hypothesis before reaching a conclusion.
