# 🛡️ Securex: Real-time SOC Detection of Brute Force Attack
**Securex** is a Security Operations Center (SOC)–oriented lab project designed to demonstrate **real-time detection of brute-force authentication attacks** against a Windows system using **Elastic SIEM**. The project simulates repeated failed login attempts, collects Windows security telemetry, correlates authentication failures, and generates actionable alerts for SOC investigation.
This project focuses on **detection, alerting, and analysis**, replicating how enterprise SOC teams identify credential-based attacks using log-driven security analytics.

---
# 🎬 Demonstration
<p align="center">
  <a href="https://github.com/user-attachments/assets/a5f9313a-6395-4c26-9dda-483de2e9317d" target="_blank">
    <img src="https://img.icons8.com/color/96/video.png" alt="Watch Demo" />
    <br>
    <strong>Click to watch the demonstration video</strong>
  </a>
</p>

---
## 📘 Project Overview
Brute-force attacks are a common initial access technique used by attackers to compromise systems by repeatedly guessing credentials. Securex addresses this threat by monitoring **Windows Security Event Logs**, forwarding them to a centralized SIEM platform, and applying **behavior-based detection rules**.
The project is implemented in a **VMware Workstation environment** and demonstrates an end-to-end SOC workflow including:
* Attack simulation
* Log collection and ingestion
* Detection rule evaluation
* Alert visualization
* Incident investigation

### 🎯 **Key Objectives:**
* **Simulate a real-world brute-force authentication attack:** Simulates repeated failed login attempts to replicate realistic brute-force credential-guessing behavior.
* **Enable and generate Windows authentication security logs:** Configures Windows auditing to log failed authentications as Event ID 4625.
* **Forward logs to a centralized SIEM platform:** Forwards Windows security logs in real time to Elastic SIEM.
* **Detect brute-force behavior using SIEM correlation rules:** Correlates multiple failed logins within defined thresholds to identify brute-force activity.
* **Generate real-time SOC alerts:** Automatically generates contextual alerts for detected brute-force authentication attempts.
* **Analyze incidents using dashboards and timelines:** Investigates alerts using Kibana dashboards and event timelines for incident analysis.

---
## 🧩 Components and Virtual Machines
### 🖥️ **Virtual Machines (VMware Workstation):**
| VM Name | Operating System | Role | 
| :--- | :--- | :--- |
| **Windows Target VM** | Windows Server | Victim system generating authentication logs |
| **SIEM Server VM** | Ubuntu 22.04LTS | Centralized log ingestion, detection, alerting |
| **Attacker VM** | Kali Linux | Brute-force attack simulation |

### 🔧 **Tools and Roles per Component:**
| Component | Tools/Services | Purpose |
| :--- | :--- | :--- |
| **Windows Target VM** | Windows Security Auditing | Generates failed logon events |
| **Windows Target VM** | Event Viewer | Validates authentication failures | 
| **Windows Target VM** | Winlogbeat / Elastic Agent | Forwards logs to SIEM | 
| **SIEM Server VM** | Elasticsearch| Log storage and indexing | 
| **SIEM Server VM** | Kibana (SIEM) | Alert visualization and investigation | 
| **SIEM Server VM** | Detection Rules | Brute-force behavior detection | 
| **Analyst System** | Web Browser | SOC monitoring | 

### 🖧 **Network Architecture Diagram:**
<p align="center">
<img src="https://github.com/himadri2324/Securex-soc/blob/main/Network%20Architecture%20Diagram.png?raw=true"
  alt="Securex Network Architecture Diagram" width="750"/>
  </p>
VMware-Based SOC Network Architecture Diagram

### 🏗️ **Architecture Flow Diagram:**
<p align="center">
  <img src="https://github.com/himadri2324/Securex-soc/blob/main/Architecture-%20diagram.png?raw=true" 
       alt="Securex SOC Architecture Diagram" width="750"/>
</p>
End-to-end SOC detection flow for brute-force authentication attacks

### ⚙️ **Detailed Setup Steps**
1.  **Environment Preparation:**
    * Install **VMware Workstation**
    * Create Windows and Ubuntu virtual machines
    * Configure NAT-based networking
2.  **Windows Security Logging:**
    * Enable **Audit Logon Events**
    * Generate failed login attempts
    * Validate Event ID **4625** using Event Viewer
3.  **Log Collection Configuration:**
    * Install Winlogbeat / Elastic Agent on Windows
    * Configure output to Elasticsearch
    * Verify log ingestion in Kibana
4.  **SIEM Setup:**
    *  Install Elasticsearch and Kibana on Linux
    *  Enable SIEM features
    *  Configure brute-force detection rules
5. **Attack Simulation:**
    * Perform repeated failed authentication attempts
    * Simulate credential guessing behavior
6.  **Alert Monitoring:**
    *  Observe alert generation in Kibana SIEM
    *  Analyze event correlation and timelines
7. **Documentation & Demonstration**
    * Record live SOC workflow using OBS Studio
    * Capture alerts and dashboards  

---
## 🚨 Detection and Response
### 🔍 **Detection**
* **Authentication Failures Occur:** Multiple unsuccessful login attempts are made against the Windows system.
* **Security Events Generated:** Windows logs each failed attempt as Event ID 4625.
* **Log Forwarding:** Winlogbeat / Elastic Agent forwards logs to Elasticsearch in real time.
* **Correlation & Rule Evaluation:** SIEM detection rules analyze event frequency and patterns.
* **Behavior-Based Detection:** Repeated failures within a defined time window are identified as brute-force activity.
* **Alert Generation:** SIEM generates a brute-force authentication alert.
* **SOC Investigation:** Analyst reviews the alert, event timeline, affected accounts, and source IPs.

### 🛠️ **Automated Response**
Upon triggering an alert:
* **Automatic Alert Creation:** SIEM triggers alerts without manual intervention.
* **Threat Classification:** Alerts are categorized as brute-force credential access attempts.
* **SOC Visibility:** Alerts are displayed on SIEM dashboards for investigation.
* **Mitigation Recommendation:** Based on severity, recommended actions include IP blocking, account lockout enforcement, or policy hardening.
> **Result:** Securex successfully detects brute-force authentication attacks by correlating Windows security logs in real time, generating contextual SOC alerts and demonstrating an end-to-end SIEM detection workflow.

### 🧠 **MITRE ATT&CK Mapping**
| Tactic | Technique | ID | 
| :--- | :--- | :--- |
| Credential Access | **Brute Force** | T1110 |
| Credential Access | **Password Guessing** | T1110.001 |

---
## 🚀 Future Enhancements
* **Implement SOAR-Based Account Lockout:** Integrating SOAR automation can automatically lock compromised accounts after repeated failed logins, reducing attacker dwell time and minimizing manual SOC intervention.
* **Integrate Firewall or IP Blocking:** Firewall integration can enable automatic blocking of malicious source IP addresses detected during brute-force attempts, preventing further attack attempts at the network perimeter.
* **Add Email or Messaging Alerts:** Configuring email or messaging notifications ensures SOC analysts receive immediate alerts, improving response time and enabling faster incident acknowledgment outside the SIEM console.
* **Extend Detection to Successful Brute-Force Logins:** Detection logic can be enhanced to identify successful logins following multiple failures, indicating potential credential compromise and higher-risk security incidents.

---
## 🔚 Conclusion
Securex demonstrates a realistic SOC detection use case by combining Windows security logging, SIEM analytics, and behavioral detection. The project reflects enterprise-grade monitoring practices and is well-suited for showcasing blue-team, SOC analyst, and SIEM engineering skills.
