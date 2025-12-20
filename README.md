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
* **Simulate a real-world brute-force authentication attack:** This project simulates repeated failed login attempts to mimic real-world brute-force attacks, allowing SOC tools to analyze credential-guessing behavior in a controlled lab environment.
* **Enable and generate Windows authentication security logs:** Windows Security Auditing is enabled to log authentication failures as Event ID 4625, capturing usernames, source IPs, timestamps, and failure reasons for accurate threat analysis.
* **Forward logs to a centralized SIEM platform:** Winlogbeat or Elastic Agent forwards Windows security logs in real time to Elastic SIEM, ensuring centralized visibility, efficient log correlation, and scalable SOC-level monitoring.
* **Detect brute-force behavior using SIEM correlation rules:** Elastic SIEM applies threshold-based detection rules to correlate multiple failed login attempts within a defined time window, identifying brute-force behavior beyond normal user login errors.
* **Generate real-time SOC alerts:** When detection thresholds are met, the SIEM automatically generates real-time alerts containing severity, risk context, affected accounts, and timelines for rapid SOC decision-making.
* **Analyze incidents using dashboards and timelines:** SOC analysts investigate alerts using Kibana dashboards and timelines to review correlated events, analyze attack patterns, and determine the scope and impact of the incident. 

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

### 🖧 **VMware Network Topology:**

### 🏗️ **Architecture Flow Diagram:**


### ⚙️ **Detailed Setup Steps**
1.  **Elastic Stack Deployment (Ubuntu 22.04 LTS):**
    * Installed and configured **Elasticsearch** for log storage and indexing.
    * Installed **Kibana** for visualization, SOC dashboards, and alert monitoring.
    * Enabled **Elastic Security (SIEM)** features in Kibana.
2.  **Log Collection Setup (Windows Endpoint):**
    * Configured Windows **Advanced Security Auditing** to log authentication failures.
    * Installed **Elastic Agent / Winlogbeat** to forward logs to Elasticsearch.
    * Verified successful log ingestion in Kibana.
3.  **SOC Monitoring Configuration:**
    * Enabled Elastic Security detection rules for failed login attempts.
    * Prepared SOC dashboards for real-time alert visibility. 
4.  **Attack Simulation (Windows-Powershell):**
    *  Simulated repeated failed login attempts using **PowerShell**.
    *  Generated continuous authentication failure events to mimic a brute-force attacks.

---
## 🚨 Detection and Response
### 🔍 **Detection**
* **Log Ingestion:** Windows Security Event Logs capture repeated failed login attempts.
* **Kibana Dashboard:** Authentication failure logs are visualized for correlation and analysis.
* **Detection Rule:** Elastic Security triggers an alert when failed login attempts exceed a defined threshold within a short time window (e.g., 5 failed attempts in 2 minutes).

### 🛠️ **Automated Response**
Upon triggering an alert:
* **Alert Generation:** Security alert appears in Elastic Security alerts panel.
* **Alert Analysis:** SOC analyst reviews source IP, affected host, timestamps, and event count.
* **Mitigation Recommendation:** Based on severity, recommended actions include IP blocking, account lockout enforcement, or policy hardening.
> **Result:** Securex successfully detects a brute-force authentication attack in real time and provides actionable alerts, demonstrating effective SOC monitoring and incident validation.

---
## 🚀 Future Enhancements
* **Automated IP Blocking:** Implement a response action that communicates with the host firewall to automatically block the malicious IP address upon detection.
* **Multi-Source Intelligence:** Expand the detection capabilities by integrating commercial threat feeds and internal "honeypot" data to catch more sophisticated attack vectors.
* **Executive Dashboards:** Develop high-level Kibana visualizations to track attack trends, top targeted hosts, and the overall health of the automated response system.
* **SOAR Integration:** Automate response actions, notifications, and remediation workflows.
