# Mission 07 - Network Fundamentals

## Overview

In this mission, I learned the fundamentals of networking and how network communication creates valuable evidence during a SOC investigation.

A SOC analyst must understand how devices communicate in order to investigate suspicious activity, identify abnormal connections, and determine whether network behavior is legitimate or potentially malicious.

---

# Key Concepts Learned

## IP Addresses

An IP address identifies a device on a network.

Example:
192.168.1.25

An IP address can be compared to a building address because it identifies where communication is being sent.

---

## Ports

A port identifies the service or application being used for communication.

Examples:

| Port | Service |
|------|---------|
| 80 | HTTP |
| 443 | HTTPS |
| 22 | SSH |
| 53 | DNS |

An IP address identifies the device, while a port identifies the specific service being accessed.

---

## Protocols

Protocols are rules that allow devices to communicate.

Examples:

- HTTP - Web traffic
- HTTPS - Secure web traffic
- DNS - Translates domain names into IP addresses
- TCP - Reliable communication
- UDP - Faster communication with less verification

---

# Investigation Questions

## 1. Why is understanding networking important for a SOC analyst?

Understanding networking is important because communication between connected devices creates evidence that can be used during investigations. Network activity can reveal suspicious connections, unauthorized access, malware communication, or unusual data transfers.

---

## 2. Explain the difference between an IP address and a port.

An IP address identifies a device on a network, similar to a building address.

A port identifies the specific service or application being used for communication, similar to a specific door within that building.

---

## 3. A computer communicates with an unknown IP address at 3 AM. Is this automatically malicious?

No, this is not automatically malicious. Additional evidence is required before making a decision.

Questions I would ask include:

- Who owns the IP address?
- Is the user normally active at this time?
- Was any information transferred?
- Is this normal behavior for the device?

---

## 4. Port Matching

- HTTPS → Port 443
- DNS → Port 53
- SSH → Port 22
- HTTP → Port 80

---

# Investigation Scenario

## Alert

Device:
Finance-PC-04

User:
Mike

Event:
Outbound connection detected

Destination:
Unknown external IP

Port:
443

Time:
1:15 AM

Data:
2GB transferred

---

## Investigation Questions

Before determining whether this activity is malicious, I would investigate:

1. Who owns this device?
2. Is the user normally active at this time?
3. Where is the destination IP located?
4. Has this IP address been reported as suspicious before?
5. What data was transferred?
6. Was this activity expected or part of a normal business process?

---

# Key Takeaway

Network activity alone does not prove malicious behavior. A SOC analyst must investigate the context surrounding the connection, including the user, device, destination, timing, and data transferred before making a decision.

Understanding networking helps analysts follow digital footprints and build accurate investigation timelines.
