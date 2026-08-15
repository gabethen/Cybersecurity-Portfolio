# Week 6 — Mission 19
## Windows Security Investigation Report

**Date:** August 15, 2026  
**Analyst:** Gabe  
**Environment:** Windows 11 ARM64 Virtual Machine  
**Platform:** UTM / QEMU 10.0 ARM

---

## 1. Investigation Objective

The objective of this investigation was to analyze Windows Security Event Logs and determine whether authentication and privilege-related events represented normal system activity or potentially suspicious behavior.

The investigation focused on:

- Event ID 4624 — Successful Logon
- Event ID 4625 — Failed Logon
- Event ID 4672 — Special Privileges Assigned to a New Logon

---

## 2. Lab Environment

The investigation was performed inside an isolated Windows 11 ARM64 virtual machine.

| Component | Configuration |
|---|---|
| Operating System | Windows 11 ARM64 |
| Architecture | ARM64 |
| Virtualization | QEMU 10.0 ARM |
| CPU | 4 cores |
| Memory | 4 GB |
| Storage | 32 GB VirtIO SCSI |
| Network | Shared Network |
| Guest Tools | UTM Guest Tools |

The Windows installation and virtual disk were verified before beginning the investigation.

---

## 3. Investigation Timeline

### Event 4624 — Successful Logon

A successful service logon was identified for the computer account:

`WIN-I6R6VVP4E7I$`

**Logon Type:** 5  
**Source Network Address:** Blank

The account name ending in `$` indicates a computer account. Logon Type 5 represents a service logon.

**Assessment:** Benign / Expected

---

### Event 4625 — Failed Logon

A failed authentication event was identified.

**Account:** `WIN-I6R6VVP4E7I$`  
**Domain:** `WORKGROUP`  
**Failure Reason:** Unknown user name or bad password  
**Logon Type:** 2  
**Workstation:** `WIN-I6R6VVP4E7I`  
**Source Address:** `127.0.0.1`  
**Timestamp:** August 13, 2026 at 5:36:41 PM

The source address `127.0.0.1` is the loopback address, indicating that the activity originated from the local system.

The event was correlated with an intentional failed-login test performed during the investigation.

**Assessment:** Benign / Informational

---

### Event 4672 — Special Privileges Assigned

A special-privilege event was identified for:

**Account:** `SYSTEM`  
**Domain:** `NT AUTHORITY`

The event included multiple highly privileged Windows permissions, including:

- `SeDebugPrivilege`
- `SeBackupPrivilege`
- `SeRestorePrivilege`
- `SeTakeOwnershipPrivilege`
- `SeLoadDriverPrivilege`
- `SeImpersonatePrivilege`

These privileges provide significant access to Windows resources and processes.

However, the account receiving them was `NT AUTHORITY\SYSTEM`, which is expected to operate with elevated privileges for core Windows functions.

**Assessment:** Benign / Expected

---

## 4. Evidence Analysis

The investigation demonstrated that individual Windows security events must be analyzed within their surrounding context.

The failed authentication event initially appeared noteworthy because it represented a failed login. However, additional evidence showed:

- The account was a computer account.
- The source address was `127.0.0.1`.
- The activity originated locally.
- The timestamp correlated with an intentional test.

Therefore, the event did not provide evidence of a remote attack.

The Event 4672 investigation demonstrated a similar principle. The privileges assigned were highly powerful, but the receiving account was the expected Windows SYSTEM account.

---

## 5. Severity Assessment

| Event | Assessment | Reason |
|---|---|---|
| 4624 | Low / Benign | Expected service logon |
| 4625 | Low / Benign | Local test activity from 127.0.0.1 |
| 4672 | Low / Benign | Expected SYSTEM privileges |

No evidence of external compromise was identified within the events reviewed during this investigation.

---

## 6. SOC Analyst Takeaway

A security event should not automatically be classified as malicious simply because the event represents a failed login or elevated privilege.

Effective investigation requires correlation between:

**Event ID + Account + Logon Type + Source Address + Timestamp + Context**

For example, repeated Event 4625 failures against a privileged account from an unfamiliar external IP address would require substantially more investigation than the locally generated event observed during this lab.

---

## 7. Skills Demonstrated

- Windows Event Viewer
- Windows Security Log analysis
- Event ID identification
- Authentication analysis
- Logon Type analysis
- Source IP analysis
- Event correlation
- Privilege analysis
- Security event classification
- SOC investigation methodology
- Incident documentation

---

## 8. Final Conclusion

The investigation identified several authentication and privilege-related Windows security events.

All investigated events were assessed as benign based on the available evidence and surrounding context.

The primary lesson from this investigation was that SOC analysts should avoid making conclusions from individual events in isolation. Events must be correlated with account information, timestamps, source addresses, logon types, and expected system behavior.

This investigation provided hands-on experience analyzing Windows security telemetry inside a controlled virtual cybersecurity lab.
