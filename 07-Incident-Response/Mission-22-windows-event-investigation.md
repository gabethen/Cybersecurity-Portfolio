# Mission 22 — Windows Authentication Event Investigation

## Objective

Investigate a Windows Security Event ID 4625 (failed logon) and compare it with nearby authentication activity to determine whether the behavior appears normal or suspicious.

## Event Information

* **Date/Time:** 8/20/2026 — 4:51:33 PM
* **Event ID:** 4625
* **Account Name:** WIN-I6R6VVP4E7I$
* **Logon Type:** 2
* **Failure Reason:** Unknown user name or bad password
* **Workstation Name:** WIN-I6R6VVP4E7I
* **Source Network Address:** 127.0.0.1

## Investigation

### 1. Important Information

The Logon Type, Failure Reason, Account Name, and Source Network Address were the most useful information because they helped determine the type of authentication failure and where the attempt originated.

### 2. Successful Login

A successful Event ID 4624 was found shortly after the failed attempt at 8/20/2026 at 4:53:37 PM.

### 3. Successful Logon Type

The successful login had **Logon Type 5**, which indicates a service logon rather than an interactive user login.

### 4. Source Network Address

The successful login had a blank Source Network Address, while the failed attempt showed **127.0.0.1**, which is the local loopback address.

### 5. Account Comparison

Both events involved the same account name: **WIN-I6R6VVP4E7I$**. The `$` at the end of the account name suggests that this is likely a computer or machine account rather than a normal human user account.

### 6. Additional Activity

No immediately suspicious activity was identified after the successful login. Event ID 4672 showed special privileges being assigned, while Event ID 4688 showed process creation activity that would require additional review to determine whether the process was expected.

## Assessment

The Event ID 4625 does not provide enough evidence to immediately classify the activity as malicious or as a confirmed security incident.

However, the activity should not automatically be considered a normal forgotten-password event. The account appears to be a machine account, and the successful authentication used Logon Type 5, indicating a service logon.

Further investigation should focus on identifying the service associated with the account, reviewing the process recorded in Event ID 4688, and comparing the activity with other events from the same system.

## Key Lesson

A single failed login does not automatically indicate malicious activity. Investigating the account type, logon type, source address, related events, and activity surrounding the authentication attempt provides better context and helps avoid jumping to conclusions.

## Skills Practiced

* Windows Security Event Log analysis
* Event ID 4625 investigation
* Event ID 4624 correlation
* Logon Type analysis
* Source IP analysis
* Machine account identification
* Event correlation
* Incident assessment
* Security investigation documentation
