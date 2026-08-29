Week 6 — Mission 18 
Windows Event Log Investigation

Date: August 13, 2026
Lab: Windows 11 ARM64 VM
Objective: Investigate Windows Security Event Logs and distinguish normal system activity from potentially suspicious authentication activity.

Environment
Windows 11 ARM64
QEMU 10.0 ARM VM
4 GB RAM
4 CPU cores
32 GB VirtIO SCSI virtual disk
UTM Guest Tools installed
Network connectivity verified
Events Investigated
Event ID 4624 — Successful Logon

Findings:

Account: WIN-I6R6VVP4E7I$
Logon Type: 5
Source Network Address: Blank

Assessment: 🟢 Benign / Expected

The $ indicates a computer account, and Logon Type 5 represents a service logon. No remote source address was present.

Event ID 4625 — Failed Logon

Findings:

Account: WIN-I6R6VVP4E7I$
Domain: WORKGROUP
Failure Reason: Unknown user name or bad password
Logon Type: 2
Workstation: WIN-I6R6VVP4E7I
Source: 127.0.0.1
Timestamp: August 13, 2026 at 5:36:41 PM

Assessment: 🟢 Likely Benign

The authentication attempt originated from the local machine (127.0.0.1) and involved the computer account. The timestamp was consistent with the intentional failed-login test performed during the investigation.

SOC lesson: A failed login does not automatically indicate an attack. Analysts must correlate the event with the account, source, timestamp, and surrounding activity.

Event ID 4672 — Special Privileges Assigned

Account: SYSTEM
Domain: NT AUTHORITY

Privileges observed:

SeAssignPrimaryTokenPrivilege
SeTcbPrivilege
SeSecurityPrivilege
SeTakeOwnershipPrivilege
SeLoadDriverPrivilege
SeBackupPrivilege
SeRestorePrivilege
SeDebugPrivilege
SeSystemEnvironmentPrivilege
SeImpersonatePrivilege
SeDelegateSessionUserImpersonatePrivilege

Assessment: 🟢 Expected Windows Activity

The NT AUTHORITY\SYSTEM account legitimately operates with highly privileged permissions required for core Windows functions.

Key SOC Takeaway

Event IDs should not be investigated in isolation.

A SOC analyst correlates:

Event ID + Account + Logon Type + Source IP + Timestamp + Context

A single failed login may be harmless. Repeated failed logins against a privileged account from an unfamiliar external IP would be considerably more suspicious.

Skills Practiced
Windows Event Viewer
Security log analysis
Event ID investigation
Authentication analysis
Logon Type interpretation
Source IP analysis
Event correlation
Privilege analysis
Benign vs. suspicious activity assessment
Basic SOC investigation methodology
