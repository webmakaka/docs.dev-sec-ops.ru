---
layout: page
title: Dev->Sec<-Ops
permalink: /
---

# Dev->Sec<-Ops

<br/>

Привет!

Стал копать тему DevSecOps.

Если есть что обсудить или предложить, пишите!

<br/>

Из того, что показалось интересным:

<br/>

Есть книга с теорией, но без практики. [Vandana Verma Sehgal] Implementing DevSecOps Practices [ENG, 2023]. В ней можно посмотреть, что вообще может быть использовано по теме DevSecOps.

<br/>

SAST - Static application security testing - анализ исходников на угрозы безопасности

DAST - Dynamic application security testing - анализ запущенного приложения

SCA - Software Composition Analysis

<br/>

**Готовые шаблоны:**  
https://gitlab.com/gitlab-org/gitlab/-/tree/master/lib/gitlab/ci/templates/Security?ref_type=heads

<br/>

# 🔥 ▶️⏸️ [[Course][Techworld with Nana] DevSecOps Bootcamp [2024, ENG]](/courses/devsecops/nana-devsecops-bootcamp/)

<br/>

# 🔥 ✅ [[Course][Gourav Shah] Ultimate DevSecOps Bootcamp by School of Devops [ENG, 2021]](/courses/devsecops/ultimate-devsecops-bootcamp/)

<br/>

### Wazuh

Надо будет посмотреть что это такое.

https://www.youtube.com/watch?v=64VrdJuU_Q0

<br/>

А потом, м.б. нужно будет покопать Penetration Testing.

<br/>

<br/>

### OWASP (Open Web Application Security Project)

    • OWASP ZAP (Zed Attack Proxy): An open-source web application security scanner that helps find security vulnerabilities in your web applications during development and testing.
        ◦ Scenario: Using OWASP ZAP to perform automated security scans on a web application as part of the CI/CD pipeline to identify and remediate vulnerabilities before deployment.
    • OWASP Top 10: A standard awareness document for developers and web application security, representing a broad consensus about the most critical security risks to web applications.
        ◦ Scenario: Educating development teams about the OWASP Top 10 vulnerabilities (e.g., SQL Injection, Cross-Site Scripting) and implementing secure coding practices to mitigate these risks.
    • OWASP Mobile Top 10: A list of the top 10 security risks for mobile applications.
        ◦ Scenario: Using the OWASP Mobile Top 10 as a guideline to conduct security assessments on a new mobile banking application.
    • OWASP Cheatsheet: A collection of concise, technical guidelines on specific security issues written by the OWASP community.
        ◦ Scenario: Referencing the OWASP Cheatsheet for best practices on implementing secure password storage in an application.

<br/>

### CIS (Center for Internet Security)

    • CIS Benchmarks: Consensus-developed secure configuration guidelines for hardening operating systems, servers, cloud environments, and software.
        ◦ Scenario: Using CIS Benchmarks to configure security settings for AWS cloud infrastructure, ensuring that instances are securely configured according to industry standards.
        ◦ Reference: <a href="https://www.cisecurity.org/cis-benchmarks">CIS Benchmarks</a>
    • CIS Controls: A set of best practices for securing IT systems and data against the most pervasive attacks.
        ◦ Scenario: Implementing CIS Controls to establish a robust security posture for an organization, including measures such as regular vulnerability assessments and secure configuration management.
        ◦ Reference: <a href="https://www.cisecurity.org/controls">CIS Controls</a>

<br/>

### Other Terms

    • CVEs (Common Vulnerabilities and Exposures): A list of publicly disclosed computer security flaws.
        ◦ Scenario: Regularly monitoring CVE databases for new vulnerabilities affecting software components used in your applications and applying patches as needed.
        ◦ Reference: <a href="https://www.cve.org/">CVE</a>
    • CVSS (Common Vulnerability Scoring System): A free and open industry standard for assessing the severity of computer system security vulnerabilities.
        ◦ Scenario: Using CVSS scores to prioritize remediation efforts based on the severity of discovered vulnerabilities.
        ◦ Reference: <a href="https://nvd.nist.gov/vuln-metrics/cvss">CVSS</a>
    • CWE (Common Weakness Enumeration): A list of software weaknesses.
        ◦ Scenario: Using the CWE list to identify common coding errors and implement secure coding practices to avoid them.
        ◦ Reference:  <a href="https://cwe.mitre.org/">CWE</a>
    • CISA (Cybersecurity and Infrastructure Security Agency): A standalone United States federal agency under the Department of Homeland Security that works to improve cybersecurity across all levels of government.
        ◦ Scenario: Leveraging CISA alerts and guidelines to stay informed about the latest cybersecurity threats and best practices for mitigating them.
        ◦ Reference: <a href="https://www.cisa.gov/">CISA</a>
