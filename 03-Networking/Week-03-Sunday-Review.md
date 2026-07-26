# Week 03 - Sunday Review

## 1. Looking back on Week 3, what concept are you most confident about now?

The concept I am most confident about now is network communication and the flow of network traffic. While I do not know every step yet, I understand the overall process of how devices communicate and how data travels across a network.

---

## 2. What part of networking do you think will take the most practice to master?

I believe memorizing common ports and understanding the services they are associated with will take the most practice. I also want to become more confident in determining which pieces of context are most important during a security investigation.

---

## 3. How has your way of thinking changed when you look at network activity or security alerts?

My way of thinking has changed because I now have a better understanding of what I am looking at when reviewing network activity or security alerts. I understand how IP addresses, ports, protocols, and packets work together, which helps me analyze activity more effectively instead of simply seeing technical information.

---

## 4. Imagine you're explaining networking to someone with no cybersecurity experience. In two or three sentences, how would you describe why networking is important for a SOC analyst?

Networking is important for a SOC analyst because it helps explain how devices communicate and leave behind digital footprints. Those digital footprints provide valuable evidence that allows analysts to investigate activity, gather facts, and determine whether an event is normal or potentially malicious without making assumptions.

---

## 5. Looking ahead to Week 4, what are you most excited to learn?

I am looking forward to expanding my understanding of networking and SIEMs. I want to better understand why SIEM platforms are such an important tool for SOC analysts and how they help collect, organize, correlate, and analyze security events during an investigation.

---

# Weekly Investigation Challenge

### Scenario

- Unknown IP address connected to an employee's computer.
- Connection used SSH (Port 22).
- Activity occurred at 2:45 AM.
- There were 200 connections within 15 minutes.

### My Investigation Steps

1. Investigate the unknown IP address and determine its owner and reputation.
2. Review the user's login activity, including successful and failed login attempts, and determine whether the login time is normal.
3. Investigate the destination IP address and determine whether it belongs to a trusted organization.
4. Review the 200 SSH connections to understand why so many connections occurred within a short period.
5. Determine whether other devices or IP addresses within the environment also communicated with the same destination IP address.

---

# Week 03 Overall Reflection

Week 3 strengthened my understanding of networking and how it supports cybersecurity investigations. I learned that network traffic alone does not prove malicious activity and that a SOC analyst must gather evidence before making conclusions. I now understand the importance of IP addresses, ports, protocols, packets, and network context when investigating security events. Although I still need more practice with common ports and investigative workflows, I feel much more confident reading network activity than I did at the beginning of the week.
