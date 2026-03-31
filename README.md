# Active Directory SOC Lab

## Objective

The objective of this project was to build a hands-on cybersecurity lab to simulate real-world attack scenarios and analyze their detection using a SIEM. The lab focuses on understanding how attacks generate telemetry in a Windows Active Directory environment and how those events can be detected and investigated.

---

## Skills Learned

- SIEM implementation and log analysis using Splunk  
- Endpoint monitoring and telemetry collection with Sysmon  
- Active Directory setup and domain management  
- Attack simulation using MITRE ATT&CK (Atomic Red Team)  
- Detection of suspicious activity using Windows Event Logs  
- Basic incident investigation and log correlation  

---

## Tools Used

- **Virtualization:** Oracle VM VirtualBox  
- **SIEM:** Splunk Enterprise  
- **Endpoint Monitoring:** Sysmon  
- **Attack Simulation:** Atomic Red Team  
- **Operating Systems:**  
  - Windows Server 2022 (Domain Controller)  
  - Windows 10 (Target Machine)  
  - Kali Linux (Attacker Machine)  

---

## Lab Setup

The lab consists of a virtualized environment with the following components:

- Domain Controller configured using Active Directory  
- Windows 10 machine joined to the domain  
- Kali Linux machine used for attack simulation  
- Internal NAT network (192.168.10.0/24) for communication  
- Sysmon installed on the endpoint for telemetry  
- Logs forwarded to Splunk using Universal Forwarder  
<img width="790" height="566" alt="AD_HBL drawio" src="https://github.com/user-attachments/assets/f98fb5a9-332d-4f8f-8b6e-8ad7807e8c8b" />

---

## Attack Simulation

### 1. Create Local Account (T1136.001)

- Used Atomic Red Team to simulate creation of a local account
<img width="1057" height="675" alt="Screenshot 2026-03-13 033820" src="https://github.com/user-attachments/assets/3faef4b8-439c-46b2-9d83-0d6b02dbc776" />

- Generated Windows Security Event Logs (Event ID 4720)  
<img width="997" height="482" alt="Screenshot 2026-03-13 034145" src="https://github.com/user-attachments/assets/b4354868-31cc-4fb2-8e5a-8f3ed28e5722" />

---

### 2. PowerShell Execution (T1059.001)

- Simulated suspicious PowerShell activity  
- Observed process creation and command execution logs via Sysmon  

---

### 3. RDP Brute Force Attempt

- Simulated credential attacks using tools like Hydra/Crowbar
<img width="1712" height="678" alt="Screenshot 2026-03-13 003110" src="https://github.com/user-attachments/assets/dd99aa48-69c8-493b-af2b-7eb7ce20cda9" />
  
- Generated failed login events (Event ID 4625)  
<img width="1027" height="563" alt="Screenshot 2026-03-13 001444" src="https://github.com/user-attachments/assets/df3f7c21-cfe3-4000-b0f7-821cfd996675" />

---

## Detection & Analysis

### Splunk Queries Used

**Account Creation Detection**
