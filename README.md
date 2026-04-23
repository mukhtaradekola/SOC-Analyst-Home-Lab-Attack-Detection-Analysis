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

                ┌───────────────────────┐
                │ Kali Linux (Attacker) │
                │   IP: 192.168.x.x     │
                └──────────┬────────────┘
                           │
                           │ Attack Traffic
                           ▼
                ┌───────────────────────┐
                │  Windows 10 (Target)  │
                │  Sysmon + Wazuh Agent │
                │  IP: 192.168.x.x      │
                └──────────┬────────────┘
                           │
                           │ Log Forwarding
                           ▼
                ┌──────────────────────────┐
                │Ubuntu Server (Wazuh SIEM)│
                │Wazuh Manager + Dashboard │
                │ IP: 192.168.x.x          │
                └──────────────────────────┘


---

## Steps

### 1. Lab Setup

- Installed Ubuntu Server on VirtualBox  
- Installed and configured Wazuh SIEM on Ubuntu Server  
- Installed Wazuh agent on Windows 10 machine  
- Installed Sysmon for detailed logging  
- Configured network communication between all VMs  

*Ref 1: Lab Architecture Diagram*  
(Add screenshot here)

---

### 2. Brute Force Attack (Initial Access)

A brute force attack was launched from Kali Linux targeting the Windows RDP service using Hydra.

### Brute Force Attack (Hydra)

```bash
sudo apt install hydra -y

 hydra -l mayor -P /usr/share/wordlists/rockyou.txt.gz rdp://192.168.x.x
```

**Detection:**
- Multiple failed login attempts detected  
- Event ID 4625 generated  
- Attacker IP successfully identified  

*Ref 2: Brute Force Detection in Wazuh*  
(Add screenshot here)

---

### 3. PowerShell Attack (Execution)

A Base64 encoded PowerShell command was executed to simulate obfuscated attacker behavior.

### PowerShell Encoded Execution

```powershell
TO generate encoded output
$Text = "Start-Process notepad"
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
$Encoded = [Convert]::ToBase64String($Bytes)
$Encoded

Execution of encoded output for attack simulation

powershell.exe -EncodedCommand UwB0AGEAcgB0AC0AUABYAG8AYWBIAHMAcwAgAG4AbwB0AGUACABHAGQA
```


**Detection:**
- PowerShell execution detected  
- Encoded command flagged  
- Suspicious process chain identified  

*Ref 3: PowerShell Detection*  
(Add screenshot here)

---

### 4. Persistence (Scheduled Task)

A scheduled task was created to simulate persistence on the compromised system.

**Detection:**
- Task creation activity logged  
- Repeated execution pattern identified  

*Ref 4: Persistence Detection*  
(Add screenshot here)

---

### 5. Lateral Movement / Privilege Escalation

Simulated attacker actions:

- Created a new user account  
- Added user to Administrators group  
- Executed commands via PowerShell

#### Creation a New User Account

```cmd
net user attacker P@ssw0rd! /add
```

#### Add User to Administrators Group
```cmd
net localgroup administrators attacker /add
```
**Detection:**
- User creation logged  
- Privilege escalation detected  
- Suspicious command execution observed  

*Ref 5: Lateral Movement Detection*  
(Add screenshot here)

---

### 6. Attack Timeline Correlation

All attack stages were correlated in Wazuh:

- Initial Access → Brute Force  
- Execution → PowerShell  
- Persistence → Scheduled Task  
- Lateral Movement → Admin Activity  

*Ref 6: Wazuh Dashboard Overview*  
(Add screenshot here)

---

## MITRE ATT&CK Mapping

- T1110 – Brute Force  
- T1059.001 – PowerShell  
- T1053 – Scheduled Task  
- T1021 – Remote Services  
- T1136 – Create Account  

---

## Conclusion

This project demonstrates the ability to simulate real-world cyber attacks and detect them using a SIEM platform deployed on Ubuntu Server.

It highlights key SOC analyst skills including:

- Threat detection  
- Log analysis  
- Incident investigation  
- Attack correlation  

This lab provides a strong foundation for real-world SOC operations and cybersecurity defense strategies.
