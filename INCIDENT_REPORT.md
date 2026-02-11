# Security Incident Report  
**Project:** Full Security Simulation – DVWA Environment  
**Environment:** Local Lab + Cloud Monitoring Stack  
**Date of Simulation:** January 2026  
**Reported By:** Johnson Mathew  

---
## 1. Executive Summary

On the date of simulation, multiple malicious activities were intentionally executed against a vulnerable web application (DVWA) hosted within a controlled lab environment.  

The objective of this exercise was to simulate real-world attack scenarios, detect malicious behavior through centralized logging, and document the response process in a structured incident report format.

During the simulation, brute-force login attempts, web exploitation, and unauthorized access attempts were identified and successfully monitored through log analysis tools. No production systems were affected as this was a controlled security lab.

---
## 2. Incident Overview

| Field | Details |
|-------|----------|
| Incident Type | Unauthorized Access Attempt / Web Application Attack |
| Severity Level | Medium (Controlled Lab Environment) |
| Target System | DVWA (Deliberately Vulnerable Web Application) |
| Detection Method | ELK Stack Log Monitoring & Manual Log Analysis |
| Status | Contained (Lab Simulation Completed) |
---
## 3. Attack Timeline

| Time | Event Description |
|------|------------------|
| T1 | Initial reconnaissance using Nmap |
| T2 | Identification of open ports (22, 80, etc.) |
| T3 | Brute-force attempt against SSH service |
| T4 | Web-based exploitation attempts on DVWA |
| T5 | Logs generated and forwarded to centralized monitoring |
| T6 | Suspicious activity identified in Kibana dashboard |
| T7 | Incident documented and environment reviewed |
---
## 4. Technical Details

### 4.1 Reconnaissance

Network scanning was conducted to enumerate open ports and exposed services.  
Open services identified included:

- Port 22 – SSH
- Port 80 – HTTP (Apache Web Server)

This confirmed the attack surface for further testing.
---
### 4.2 Exploitation Attempts

The following attack simulations were executed:

- SSH brute-force simulation
- Web application vulnerability testing on DVWA
- Login abuse attempts

These actions generated authentication failure logs and suspicious access patterns within the system logs.
---
### 4.3 Detection & Monitoring

Log data was:

- Collected from the target system
- Forwarded to the ELK Stack
- Indexed in Elasticsearch
- Visualized in Kibana

Indicators of suspicious behavior included:

- Multiple failed login attempts
- Repeated HTTP requests from a single source
- Abnormal authentication patterns

These were successfully identified via Kibana dashboards.
---
## 5. Impact Assessment

Since this was a controlled lab environment:

- No real user data was exposed
- No production systems were affected
- No persistent backdoor access remained

However, the simulation demonstrates how similar attacks could compromise a poorly secured production environment.
---
## 6. Root Cause Analysis

The vulnerabilities exploited were intentionally enabled within DVWA for educational purposes.

Key weaknesses observed:

- Weak authentication controls
- Lack of brute-force protection
- Insufficient rate limiting
- Default insecure configurations
---
## 7. Containment & Remediation

The following defensive measures were implemented or recommended:

- Strengthened password policies
- Rate limiting for login endpoints
- Log monitoring for abnormal authentication attempts
- Web Application Firewall (WAF) deployment
- Continuous log analysis using SIEM tools
---
## 8. Lessons Learned

- Visibility is critical for detection.
- Centralized logging significantly improves response capability.
- Even simple brute-force attacks generate detectable patterns.
- Monitoring must be continuous, not reactive.
---
## 9. Conclusion

This incident simulation demonstrates the full lifecycle of a cybersecurity event:

Reconnaissance → Exploitation → Detection → Analysis → Documentation → Remediation

The project reflects practical SOC-level workflow and demonstrates readiness to operate within a Security Operations or Blue Team environment.
---

**End of Report**
