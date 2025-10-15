# Web Application Vulnerability Assessment Report

**Project:** DVWA (Damn Vulnerable Web Application)  
**Target URL:** `http://host.docker.internal:8080`  
**Scan Tool:** OWASP ZAP 2.16.1 (by Checkmarx)  
**Report Generated:** Wed, 15 Oct 2025 18:04:27  

---

## 1. Executive Summary

<details>
<summary>Click to expand</summary>

This report summarizes an automated vulnerability assessment conducted against the DVWA instance. The scan focused on **security misconfigurations, headers, cookies, and potential web-based vulnerabilities**.

| Risk Level    | Number of Alerts |
|---------------|----------------|
| High          | 0              |
| Medium        | 2              |
| Low           | 7              |
| Informational | 5              |
| False Positives | 0            |

> **Note:** DVWA is intentionally vulnerable for testing and educational purposes. Some findings are expected.

</details>

---

## 2. Key Vulnerabilities & Recommendations

<details>
<summary>Click to expand</summary>

### Medium-Risk Findings

<details>
<summary>1. Content Security Policy (CSP) Header Not Set</summary>

- **Impact:** Risk of XSS and data injection attacks.  
- **Affected URLs:** `/`, `/login.php`, `/sitemap.xml`  
- **Recommendation:** Implement a strict CSP header:

```http
Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self'; img-src 'self' data:;
References:

OWASP CSP Cheat Sheet

MDN CSP Guide

</details> <details> <summary>2. Missing Anti-clickjacking Header</summary>
Impact: Pages may be embedded in malicious frames.

Affected URLs: /, /login.php

Recommendation: Add one of the following headers:

http
Copy code
X-Frame-Options: DENY
or

http
Copy code
Content-Security-Policy: frame-ancestors 'none';
Reference: MDN X-Frame-Options

</details>
Low-Risk Findings
Issue	Recommendation
Cookie No HttpOnly Flag	Set HttpOnly on all session cookies.
Cookie without SameSite Attribute	Set SameSite=Lax or Strict.
In Page Banner Information Leak	Hide server version info (ServerTokens Prod in Apache).
Insufficient Site Isolation (Spectre)	Add Cross-Origin-Resource-Policy: same-origin.
Permissions Policy Header Not Set	Restrict features: Permissions-Policy: geolocation=(), microphone=().
Server Leaks Version Information	Suppress server info in HTTP headers.
X-Content-Type-Options Header Missing	Add X-Content-Type-Options: nosniff.

Informational Alerts
Authentication Request Identified – login POST detected.

Session Management Response Identified – PHPSESSID cookie recognized.

Non-Storable / Cacheable Content – caching headers are present.

</details>
3. Security Hardening Recommendations
<details> <summary>Click to expand</summary>
Recommended Security Headers
http
Copy code
Content-Security-Policy: default-src 'self';
X-Frame-Options: DENY;
X-Content-Type-Options: nosniff;
Referrer-Policy: no-referrer;
Permissions-Policy: geolocation=(), microphone=();
Cross-Origin-Resource-Policy: same-origin;
Cookies & Session Management
Use Secure, HttpOnly, SameSite=Strict for all cookies.

Rotate session IDs after login and invalidate on logout.

Server & Version Information
Hide Apache version & OS:

apache
Copy code
ServerTokens Prod
ServerSignature Off
</details>
4. Tools & References
<details> <summary>Click to expand</summary>
OWASP ZAP: https://www.zaproxy.org

OWASP Secure Headers Guide: https://owasp.org/www-project-secure-headers

CSP Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html

MDN Security Headers: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers

</details>
5. Conclusion
<details> <summary>Click to expand</summary>
No high-risk vulnerabilities were found. Medium- and low-risk findings are primarily related to security headers, cookie configurations, and server information leaks.

Implementing the recommendations above will strengthen the application’s security posture and demonstrate a professional approach to vulnerability management.

</details> ```
