# SOC Analyst Home Lab – Attack Detection & Analysis

## Objective

The SOC Analyst Home Lab project aimed to build a realistic security monitoring environment for simulating and detecting cyber attacks. The primary objective was to generate attack telemetry from a controlled attacker machine and analyze logs using a SIEM platform to detect malicious activities in real time.

This project focuses on understanding attacker behavior, log analysis, and incident investigation using a structured SOC workflow.

---

## Skills Learned

- Practical experience with SIEM monitoring and alert analysis using Wazuh  
- Ability to analyze Windows event logs and Sysmon telemetry  
- Detection and investigation of multi-stage cyber attacks  
- Understanding of attacker techniques mapped to MITRE ATT&CK  
- Hands-on experience with log correlation and threat hunting  
- Improved incident analysis and reporting skills  

---

## Tools Used

- Wazuh – SIEM platform for log collection, detection, and alerting  
- Sysmon – Endpoint logging for detailed system activity  
- Kali Linux – Attacker machine for simulating attacks  
- Windows 10 VM – Target system  
- Hydra – Brute force attack simulation  
- PowerShell – Execution and persistence techniques  

---

## Steps

### 1. Lab Setup

A virtualized environment was created consisting of:
- Wazuh server (Ubuntu)
- Windows 10 endpoint with Sysmon installed
- Kali Linux attacker machine

*Ref 1: Lab Architecture Diagram*  
(architecture screenshot)

---

### 2. Brute Force Attack (Initial Access)

A brute force attack was launched from Kali Linux targeting the Windows RDP service using Hydra.

**Detection:**
- Multiple failed login attempts detected in Wazuh  
- Event ID 4625 triggered repeatedly  
- Source IP identified as attacker machine  

*Ref 2: Brute Force Detection in Wazuh*  
(screenshot showing failed login alerts)

---

### 3. PowerShell Attack (Execution)

A base64-encoded PowerShell command was executed on the Windows machine to simulate obfuscated malicious activity.

**Detection:**
- PowerShell process execution logged  
- Encoded command flagged by Wazuh  
- Suspicious parent-child process relationship identified  

*Ref 3: PowerShell Encoded Command Detection*  
(screenshot showing encoded PowerShell alert)

---

### 4. Persistence Mechanism

A scheduled task was created to maintain persistence on the compromised system.

**Detection:**
- Task creation event captured  
- Suspicious recurring execution pattern identified  

*Ref 4: Scheduled Task Detection*  
(screenshot showing persistence alert)

---

### 5. Lateral Movement / Privilege Escalation

Simulated attacker behavior included:
- Creating a new user account  
- Adding the user to the administrators group  
- Executing commands via PowerShell  

**Detection:**
- User account creation logged  
- Privilege escalation activity detected  
- Suspicious command execution identified  

*Ref 5: Admin Activity & Lateral Movement Detection*  
(screenshot showing user creation / admin activity)

---

### 6. Attack Timeline Correlation

All events were correlated within Wazuh to reconstruct the full attack chain:

- Initial Access → Brute force  
- Execution → PowerShell encoded command  
- Persistence → Scheduled task  
- Lateral Movement → Admin activity  

*Ref 6: Wazuh Dashboard Overview*  
(screenshot showing multiple alerts timeline)

---

## MITRE ATT&CK Mapping

- T1110 – Brute Force  
- T1059.001 – PowerShell  
- T1053 – Scheduled Task  
- T1021 – Remote Services  
- T1136 – Create Account  

---

## Conclusion

This project demonstrates the ability to simulate real-world attack scenarios and detect them using a SIEM platform. It highlights key SOC analyst skills including log analysis, threat detection, and incident investigation.

The lab provides a strong foundation for understanding how attackers operate and how defensive mechanisms can be implemented to detect and respond to threats effectively.
