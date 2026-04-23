# SOC Analyst Home Lab – Attack Detection & Analysis

## Objective

The SOC Analyst Home Lab project aimed to build a realistic security monitoring environment for simulating and detecting cyber attacks. The lab was designed using an Ubuntu Server hosting Wazuh as the SIEM platform, a Windows 10 endpoint for telemetry generation, and a Kali Linux machine for attack simulation.

The primary objective was to generate real attack scenarios and analyze logs to detect malicious behavior using a structured SOC workflow.

---

## Skills Learned

- Practical experience with SIEM monitoring and alert analysis using Wazuh  
- Ability to analyze Windows event logs and Sysmon telemetry  
- Detection and investigation of multi-stage cyber attacks  
- Understanding of attacker techniques using MITRE ATT&CK  
- Hands-on experience with log correlation and threat hunting  
- Incident analysis and reporting  

---

## Tools Used

- Wazuh (Installed on Ubuntu Server) – SIEM for log collection and detection  
- Sysmon – Endpoint monitoring and logging  
- Kali Linux – Attacker machine  
- Windows 10 VM – Target system  
- Hydra – Brute force attack simulation  
- PowerShell – Execution and persistence techniques  

---

## Lab Architecture

The lab environment consists of:

- Ubuntu Server (Wazuh SIEM)
- Windows 10 VM (Target + Sysmon Agent)
- Kali Linux (Attacker)
