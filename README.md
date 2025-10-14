\# Web Application Vulnerability Assessment (DVWA)



\## Overview

This project demonstrates a full-scale web application vulnerability assessment using \*\*Damn Vulnerable Web Application (DVWA)\*\*, performed in an isolated Docker environment.  

It showcases practical skills in reconnaissance, vulnerability scanning, risk analysis, and remediation planning — core competencies for cybersecurity analysts and incident responders.



\*\*Author:\*\* Abhijay Nair  

\*\*Role:\*\* Cybersecurity Lead | GRC \& Threat Detection Specialist  

\*\*Tools Used:\*\* Docker, Nmap, OWASP ZAP, Burp Suite, PowerShell  



\## Objectives

\- Simulate a real-world web app vulnerability assessment safely.

\- Identify misconfigurations and security flaws.

\- Generate professional vulnerability reports with evidence.

\- Demonstrate GRC policy alignment (OWASP, NIST 800-53, ISO 27001 controls).



\## Lab Architecture

The DVWA application runs inside a Docker container bound to `127.0.0.1` for isolation.  

Scans and analysis are performed locally to prevent exposure.



Host (Windows)

└── Docker Container → DVWA

├── Port: 8080 (localhost only)

├── MySQL (internal)

└── Apache Web Server



\## Phases

1\. \*\*Setup \& Environment Hardening\*\*

2\. \*\*Reconnaissance with Nmap\*\*

3\. \*\*Dynamic Analysis with OWASP ZAP\*\*

4\. \*\*Manual Testing (Burp Suite)\*\*

5\. \*\*Reporting \& GRC Alignment\*\*



\## Results (to be updated)

\- Critical vulnerabilities identified.

\- Recommendations documented in `report/`.



\## Repository Structure

webapp-vuln-assessment/

├─ scans/

├─ report/

│ └─ screenshots/

├─ scripts/

└─ README.md



