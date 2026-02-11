# Full Security Simulation – Detailed Documentation

## Project Information

* **Program:** Bincom Academy – Cybersecurity
* **Assessment:** Final Practical Test
* **Student Name:** Johnson Mathew
* **Date:** 29 January 2026
---
## 1. Introduction

This document provides a **detailed, step-by-step documentation** of a full end-to-end security simulation conducted in a cloud-based environment. The project demonstrates how a small-scale enterprise infrastructure can be **attacked, defended, monitored, and investigated** using industry-standard cybersecurity tools.

The focus of this simulation is not only exploitation, but also **detection, visibility, and incident response**, mirroring real-world Security Operations Center (SOC) workflows.
---
## 2. Test Objective

The primary objective of this practical test was to:

* Build a vulnerable enterprise-like environment
* Simulate external reconnaissance and attacks
* Implement defensive security controls
* Monitor activities using centralized logging
* Produce a structured incident response report
---
## 3. Network Architecture & Design

### 3.1 Network Overview

The environment was designed using a **three-tier architecture**:

* **Attacker Machine:**
  * Kali Linux (External attacker)

* **Victim Server:**
  * Ubuntu Linux (AWS EC2)
  * Hosts vulnerable services and honeypot

* **Monitoring Server:**
  * Ubuntu Linux (AWS EC2)
  * Runs centralized logging and monitoring tools

All systems were deployed on **AWS EC2** to simulate an internet-exposed enterprise environment.

### 3.2 Network Diagram

📸 **Screenshot:** <img width="1280" height="853" alt="image" src="https://github.com/user-attachments/assets/aead0578-3561-4d03-988d-af6536be29b6" />

* Network diagram showing: Kali Linux → Victim Server → ELK Monitoring Server
---
## 4. Environment Setup

### 4.1 Attacker Machine (Kali Linux)

* **Operating System:** Kali Linux
* **Purpose:** Simulate external attacks and reconnaissance
* **Tools Used:**
  * Nmap
  * Metasploit Framework
  
### 4.2 Victim Server (Ubuntu EC2)

* **Operating System:** Ubuntu Linux
* **Platform:** AWS EC2
* **Installed Services:**
  * DVWA (Damn Vulnerable Web Application)
  * Cowrie SSH Honeypot
  * Apache Web Server
  * OpenSSH

This server represents a vulnerable enterprise system exposed to the internet.
---
### 4.3 Monitoring Server (ELK Stack)

* **Operating System:** Ubuntu Linux
* **Platform:** AWS EC2
* **Purpose:** Centralized security monitoring
* **Installed Components:**

  * Elasticsearch
  * Logstash
  * Kibana
  * Filebeat
---
## 5. Vulnerable Services Deployment

### 5.1 DVWA Deployment

DVWA was deployed on the victim server to simulate common web application vulnerabilities.

**Deployment Status:**

* DVWA installed successfully
* Web interface accessible
* Admin login completed
* Database created and configured
* Security level adjusted for testing

**Confirmed Vulnerabilities:**

* SQL Injection
* Cross-Site Scripting (XSS)

📸 **Screenshots:** <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/b9b96e4c-6ee7-4c32-bb6b-40e212a2c856" />
DVWA dashboard
---
### 5.2 Cowrie Honeypot Deployment

A Cowrie SSH honeypot was deployed to capture malicious SSH activity.

**Configuration Details:**

* Cowrie service running
* SSH interaction enabled
* Listening on TCP port **2222**
* Logs generated for all connections

📸 **Screenshot:** <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/521bf187-955f-45a8-bc3c-8d77423273b8" />

* Cowrie service status
* Listening port verification
---
## 6. Reconnaissance & Attack Simulation

### 6.1 Nmap Reconnaissance

An Nmap scan was executed from the Kali Linux attacker machine to identify exposed services.

**Command Used:**

```bash
nmap -sV 13.58.221.255
```

**Scan Results:**

| Port | State | Service | Version         |
| ---- | ----- | ------- | --------------- |
| 21   | open  | ftp     | unknown         |
| 22   | open  | ssh     | OpenSSH 8.9p1   |
| 80   | open  | http    | Apache 2.4.52   |
| 2222 | open  | ssh     | Cowrie Honeypot |

📸 **Screenshot:** Nmap scan output <img width="1280" height="606" alt="image" src="https://github.com/user-attachments/assets/c2692f07-581d-4504-89c7-96a92b056800" />

---
### 6.2 DVWA Exploitation

Controlled exploitation was performed using DVWA modules.

**SQL Injection:**

* Navigated to SQL Injection module
* Submitted test payloads
* Vulnerability confirmed via database responses

**XSS (Reflected):**

* Injected test script into input field
* Script executed successfully

Apache access logs captured all attack requests and forwarded them to ELK.

📸 **Screenshots:**
* DVWA attack execution: <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/2d7b6509-289e-4655-a26b-d6fa81129390" />

* Corresponding Kibana logs: <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/f1cd408f-2aaf-4974-80fe-7ce9cebf6b96" />

---
### 6.3 SSH Attack Simulation (Metasploit)

Metasploit was used to simulate SSH attacks against the Cowrie honeypot.

**Steps Performed:**

* Launched Metasploit Framework
* Loaded SSH login scanner module
* Targeted victim server on port 2222

Cowrie safely recorded all attack attempts without real system compromise.

📸 **Screenshot:** Metasploit terminal output <img width="1280" height="606" alt="image" src="https://github.com/user-attachments/assets/cd54a713-40ab-4e13-b913-ebfece22b318" />

---
## 7. Centralized Logging & Monitoring (ELK Stack)

### 7.1 ELK Stack Deployment

* Elasticsearch installed and running
* Kibana accessible on port 5601
* Logstash listening on port 5044

📸 **Screenshot:** Kibana service status and port listening <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/1cc09bd8-f352-4ae3-8e4f-651e48f1ae99" />

---
### 7.2 Filebeat Configuration

Filebeat was installed on the victim server to forward logs.

**Log Sources Configured:**

* Apache access logs (DVWA activity)
* Cowrie honeypot logs (SSH attacks)

📸 **Screenshot:** Filebeat running status <img width="1280" height="728" alt="image" src="https://github.com/user-attachments/assets/040a9745-af4a-493a-a1fc-73d346174b97" />

---
### 7.3 Logstash Pipeline Configuration

Logstash was configured to:

* Receive logs from Filebeat
* Parse and structure log data
* Forward logs to Elasticsearch

📸 **Screenshot:** Logstash pipeline configuration <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/09abbcb9-7c35-4593-bc93-347741e50f20" />

---
### 7.4 Log Verification in Kibana

After configuration:

* Log indices created successfully
* Logs visible in Kibana Discover
* Events timestamped and searchable

📸 **Screenshot:** Kibana Discover dashboard <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/a176486f-dcb9-4781-8428-24faa7e4c443" />

---
## 8. Defensive Controls Implementation

### 8.1 ModSecurity WAF Deployment

ModSecurity was installed and integrated with Apache to protect DVWA.

**Configuration:**

* WAF engine enabled
* Blocking mode activated
* Default rule set applied
---
### 8.2 Attack Blocking Validation
After enabling ModSecurity, SQL Injection attacks were reattempted.

**Result:**

* Requests blocked
* HTTP 403 Forbidden returned
* Events logged and forwarded to ELK

📸 **Screenshots:**
* 403 Forbidden response <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/7172749f-22fc-4535-be09-c60ef6080565" />

* Kibana ModSecurity logs <img width="1280" height="674" alt="image" src="https://github.com/user-attachments/assets/2b3913b0-e8a4-411a-9ff9-d1c6f6456721" />
---

---
## Key Skills Demonstrated

- Network Scanning and Enumeration (Nmap)
- Vulnerability Identification and Exploitation (DVWA, Metasploit)
- SSH Brute-force Simulation and Credential Access
- Honeypot Deployment and Attack Monitoring (Cowrie)
- Log Collection and Centralization
- SIEM Monitoring and Log Analysis (ELK Stack)
- Web Application Firewall (WAF) Configuration and Testing
- Incident Detection, Investigation, and Documentation
- Cloud Deployment and Security Configuration (AWS)

---
## Conclusion

This project demonstrates a full end-to-end security workflow, including environment setup, offensive testing, defensive monitoring, and incident response documentation.  

Rather than focusing solely on exploitation, this simulation emphasizes visibility, detection, and response — reflecting real-world Security Operations Center (SOC) operations.

Through this project, practical experience was gained in attack simulation, log analysis, threat detection, and security hardening within both local and cloud-based environments.

This hands-on implementation strengthens foundational cybersecurity skills and demonstrates readiness for SOC, Blue Team, or Junior Security Analyst roles.
