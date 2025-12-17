# 🛡️ Securex: Real-time SOC Detection of Brute Force Attack

Securex is an on-premises SOC lab project that demonstrates **real-time detection of brute-force authentication attacks** on a Windows endpoint. The project simulates an attack scenarios, collects Windows Security Event logs, forwards them to **Elastic SIEM**, and generates **actionable alerts** for SOC analysts. It highlights an end-to-end SOC workflow including attack simulation, log ingestion, threat detection, alert monitoring, and initial incident response, closely aligning with **real-world Tier-1 SOC operations**.
---
Demonstration Of Project

https://github.com/user-attachments/assets/a5f9313a-6395-4c26-9dda-483de2e9317d

---
## 📘 Project Overview

Securex continuously monitors Windows Security Event Logs for repeated failed login attempts, correlates them with threat intelligence, and raises alerts for potential brute-force attacks. The system ensures rapid detection and response by integrating monitoring, visualization, and automated alerting.

### 🎯 **Key Objectives:**

* **Real-time Monitoring:** Ingest and analyze authentication logs continuously to detect suspicious login behavior immediately.
* **Threat Intelligence Integration:** Utilize updated lists of known malicious IPs for enhanced detection accuracy.
* **Automated Incident Response:** Send actionable alerts to SOC analysts via automated workflows, reducing manual effort.
* **Centralized Visibility:** Provide unified dashboards in Kibana for forensic investigation and trend analysis of detected threats.

---

## 🧩 Components and Setup

The project utilizes a virtualized environment with core components:

| Component | Operating System | Role | Key Tools/Services |
| :--- | :--- | :--- | :--- |
| **VMware Workstation** | Host OS | Virtualization Platform | **VMware Workstation** |
| **Windows Endpoint** | Windows | Target System | **Windows Security Event Logs** |
| **Attacker Machine** | Windows | Brute-Force Attack Execution | **Powershell** |
| **Log Collection Agent** | Windows| Log Forwarding | **Elastic Agent, Winlogbeat** |
| **SIEM Storage Engine** | Linux | Log Storage and Indexing | **Elasticsearch** |
| **SOC Dashboard** | Linux | Visualization and Monitoring | **Kibana** |
| **Detection Engine** | Linux | Threat Detection and Alerting | **Elastic Security (SIEM)** |


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
   * Simulated repeated failed login attempts using **PowerShell**.
   * Generated continuous authentication failure events to mimic a brute-force attacks.

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

