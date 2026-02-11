# Full Security Simulation – SOC & Incident Response Lab

## 📖 Overview
This project documents a **full end-to-end security simulation** carried out as part of the **Bincom Academy Final Practical Test**.  
The objective was to design, attack, defend, and monitor a small-scale enterprise environment using real-world cybersecurity tools and workflows.

The lab demonstrates offensive security techniques, defensive controls, centralized logging, and incident response — reflecting how a real Security Operations Center (SOC) operates.

---

## 🎯 Objectives
- Deploy vulnerable services in a cloud environment
- Simulate external attacks and reconnaissance
- Implement defensive security controls
- Monitor and analyze security events centrally
- Produce a structured incident response report

---

## 🧪 Environment Architecture
The simulation was built using a **three-tier enterprise architecture**:

- **Attacker Machine**
  - Kali Linux
  - Tools: Nmap, Metasploit

- **Victim Server**
  - Ubuntu Linux (AWS EC2)
  - Services:
    - DVWA (Damn Vulnerable Web Application)
    - Cowrie SSH Honeypot
    - Apache Web Server
    - OpenSSH

- **Monitoring Server**
  - Ubuntu Linux (AWS EC2)
  - ELK Stack:
    - Elasticsearch
    - Logstash
    - Kibana
    - Filebeat

All systems were deployed on **AWS EC2** to simulate an internet-exposed enterprise environment.

---

## 🛠 Tools & Technologies Used
- Kali Linux
- Ubuntu Linux
- DVWA
- Cowrie SSH Honeypot
- Nmap
- Metasploit Framework
- ModSecurity (Web Application Firewall)
- Elasticsearch
- Logstash
- Kibana
- Filebeat
- AWS EC2

---

## 🔍 Attack Simulations
- Network reconnaissance using **Nmap**
- Web application exploitation:
  - SQL Injection
  - Cross-Site Scripting (XSS)
- SSH attack simulation using **Metasploit** against a honeypot

---

## 🛡 Defensive Controls
- Web Application Firewall (ModSecurity) deployed on Apache
- Malicious web requests blocked successfully
- Attack attempts logged and forwarded to the ELK Stack

---

## 📊 Monitoring & Logging
- Centralized log collection using Filebeat
- Log parsing and indexing via Logstash
- Security event visualization and analysis in Kibana
- Verified visibility of:
  - Web attacks
  - SSH brute-force attempts
  - WAF blocking events

---

## 📑 Documentation
Detailed step-by-step implementation, screenshots, logs, dashboards, and the full incident response report are provided in:

📂 **`DOCUMENTATION.md`**

---

## 🧠 Key Takeaways
- Internet-exposed vulnerable services attract immediate attacks
- Centralized logging is critical for attack detection and analysis
- Layered security controls significantly reduce attack impact
- Honeypots provide valuable attacker intelligence without system risk

---

## 🏁 Conclusion
This project demonstrates practical skills in **offensive security, defensive engineering, monitoring, and incident response**, closely mirroring real-world SOC operations and enterprise security workflows.

---

## 👤 Author
**Johnson Mathew**  
Cybersecurity Trainee | SOC & Cloud Security Enthusiast  
