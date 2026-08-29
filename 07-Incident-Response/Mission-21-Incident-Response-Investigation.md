# Mission 21 — Incident Response Investigation
 
## Scenario

A SIEM alert showed that user `jsmith` had 12 failed login attempts between 2:14 AM and 2:19 AM, followed by a successful login. The login originated from an unfamiliar IP address outside the company's known IP ranges. At 2:23 AM, the account accessed the company's HR application.

## 1. What Stands Out?

Several activities stood out during the investigation:

- 12 failed login attempts followed by a successful login.
- The activity occurred between 2:14 AM and 2:19 AM.
- The login originated from an unfamiliar location and IP address.
- The IP address was not within the company's known IP ranges.
- The user accessed the sensitive HR application shortly after successfully logging in.

## 2. Why Is the Timing Important?

The timing is important because it allows the analyst to compare the activity against the user's normal behavior. The user normally works between 8 AM and 5 PM, making activity around 2 AM unusual and worthy of further investigation.

## 3. Why Is the Successful Login Concerning?

The successful login is more concerning because it occurred after 12 failed login attempts. This could indicate a password-guessing or brute-force attempt in which someone eventually obtained the correct credentials. However, the activity does not automatically prove that the account was compromised.

## 4. How Did the IP Information Change My Assessment?

The unfamiliar IP increased my level of concern because it was not part of the company's known IP ranges and had not previously been associated with the user. I would investigate the IP's reputation, location, ownership, and previous activity before making a final determination.

## 5. What Additional IP Information Would I Investigate?

I would investigate:

- Source and geographic location
- IP reputation
- Whether the IP is associated with known malicious activity
- Whether the IP is associated with a VPN, proxy, or other anonymizing service
- Whether other accounts have connected from the same IP
- Previous connections between the IP and the organization's environment

## 6. Is the Activity Consistent With the User's Normal Behavior?

No. The activity does not appear consistent with the user's normal behavior because the user normally works between 8 AM and 5 PM, while the login activity occurred around 2 AM.

## 7. What Would I Investigate Next?

I would investigate the IP address, the user's device, authentication history, and activity performed after the successful login. I would also determine whether any sensitive HR information was accessed, downloaded, or changed. If additional evidence indicated unauthorized activity, I would escalate the alert and follow the organization's incident response procedures.

## Final Assessment

I classified this as **Suspicious Activity — Continue Monitoring**.

There are several red flags, including the 12 failed login attempts, unusual login time, unfamiliar IP address, successful authentication, and subsequent access to a sensitive HR application. However, I would not immediately declare a confirmed security incident because suspicious activity does not automatically mean an account has been compromised.

Further investigation would be necessary to determine whether the activity was malicious or had a legitimate explanation.

## Key Lesson

Not every suspicious event is automatically a security incident. A SOC analyst should investigate the surrounding context and available evidence before determining whether malicious activity has occurred.

## Skills Practiced

- SIEM alert investigation
- Authentication analysis
- IP address investigation
- User behavior analysis
- Alert triage
- Incident classification
- Account compromise investigation
- Evidence-based decision making
- Incident response fundamentals
