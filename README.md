# Splunk SOC Lab – Brute Force Detection & Log Analysis

## Project Overview

This project demonstrates a Security Operations Center (SOC) lab implementation using Splunk SIEM.  
A brute-force attack was simulated using Hydra against a Windows Server. Security logs were collected using Splunk Universal Forwarder and analyzed using SPL queries. A real-time monitoring dashboard was developed for detection.

---

## 📄 Project Presentation

You can view the presentation here:  
🔗 [Splunk SOC Lab Presentation (PDF)](./Splunk-SOC-Lab.pdf)

---

---

## 📸 Key Detection Screenshots

### Successful Logon (Event ID 4624)
![Successful_Logon](./P1.PNG)


### 🔹 Failed Logon Detection (Event ID 4625)
![Failed Logon](Screenshots/P2.PNG)

### 🔹 Top 10 Event Codes
![Top 10 Event Codes](Screenshots/P10.PNG)

### 🔹 Security Monitoring Dashboard
![Dashboard](Screenshots/Dashboard.PNG)

---

## Project Objectives

- Simulate a brute-force attack
- Generate Windows Security Event Logs
- Analyze Event ID 4625 (Failed Logon)
- Detect suspicious login patterns using SPL
- Build a monitoring dashboard

---

## Lab Architecture

| Component | Technology |
|-----------|------------|
| Host Machine | Windows 11 |
| Target Server | Windows Server 2019 |
| Attacker Machine | Kali Linux |
| SIEM Tool | Splunk Enterprise |
| Log Collector | Splunk Universal Forwarder |

---

## Brute Force Attack Simulation

The attack was performed using Hydra from Kali Linux.

### Command Used

```bash
hydra -V -f -l administrator -P rockyou.txt rdp://192.168.232.131
```
## Attack Details

Targeted Windows Server RDP service

Generated multiple failed login attempts

Triggered Event ID 4625 logs

This attack was performed in a controlled lab environment for educational purposes only.

 ## Log Verification

Opened Event Viewer on Windows Server

Navigated to: Windows Logs → Security

Filtered Event ID 4625

Verified multiple failed login attempts

## SPL Queries Used
EventCode=4625
| sort -_time
| stats count by SourceName
| timechart span=1h count
EventCode=4740
EventCode=4720
EventCode=4728
EventCode=1102

## Dashboard :-

The dashboard visualizes:

Total failed login attempts

Top attacking IP addresses

Login trend over time

Account lockouts

Privilege escalation events

## Conclusion

This project demonstrates practical knowledge of SIEM architecture, log analysis, and brute-force detection using Splunk.

---

## Author

**Kavindra Patel**  
