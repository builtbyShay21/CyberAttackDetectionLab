# Cyber Attack Detection & Incident Response Lab

A cybersecurity portfolio project demonstrating practical experience with web application exploitation, network security monitoring, digital forensics, and incident response.

**Core Technologies & Concepts Demonstrated:**
- **DVWA** (Controlled SQL injection testing)
- **Suricata IDS** (Detection engineering)
- **Wireshark** (Network traffic analysis)
- **Apache Logs** (Server log analysis)
- **Autopsy** (Digital forensics & evidence correlation)
- **MITRE ATT&CK** (TTP mapping)
- **Incident Response** (NIST-aligned planning)

## Project Objective

The objective of this project is to simulate a web application compromise (SQL injection) in an isolated environment, and subsequently perform a comprehensive technical investigation to detect, analyze, and respond to the incident. 

*Note: This repository contains reconstructed technical documentation and evidence originating from an isolated, controlled lab environment. The theoretical case study for the threat model was based on the 2023 MOVEit Transfer breach, but this lab specifically focuses on demonstrating fundamental concepts against DVWA, not recreating the MOVEit exploit.*

## Lab Architecture

The lab utilized a controlled, isolated network to simulate both the attacker and the victim, alongside security monitoring controls.

![Lab Setup](screenshots/01-lab-setup.png)
*Connectivity verification between the Kali Linux attacker system and the Metasploitable 2 target, establishing the isolated lab environment.*

```mermaid
graph TD
    Kali[Kali Linux<br/>Attacker System] -->|Controlled attack traffic| Target[Metasploitable 2 / DVWA<br/>Vulnerable Target]
    Target --> Suricata[Suricata IDS]
    Target --> Logs[Apache Access Logs]
    Target --> Wireshark[Wireshark Packet Capture]
    
    Suricata --> Forensics[Forensic Investigation]
    Logs --> Forensics
    Wireshark --> Forensics
    
    Forensics --> Autopsy[Autopsy]
    Forensics --> Correlation[Evidence Correlation]
    Forensics --> MITRE[MITRE ATT&CK Mapping]
    Forensics --> IR[Incident Response]
```

## Security Workflow

The project follows a structured lifecycle from initial compromise to remediation:

1. **Attack Simulation**
2. **Detection Engineering**
3. **Network / Log Analysis**
4. **Digital Forensics**
5. **MITRE ATT&CK Mapping**
6. **Incident Response**

## Objectives

- Understand and simulate web application vulnerabilities in a safe, controlled manner.
- Develop custom intrusion detection rules to identify malicious activity.
- Correlate forensic evidence across network captures and server logs.
- Map observed behaviors and theoretical case-study techniques to the MITRE ATT&CK framework.
- Formulate an incident response workflow aligned with NIST concepts.

## Technologies Used

- **Operating Systems:** Kali Linux, Metasploitable 2
- **Vulnerable Application:** Damn Vulnerable Web App (DVWA)
- **Attack Tools:** sqlmap, manual SQL injection techniques
- **Detection & Monitoring:** Suricata IDS
- **Network & Log Analysis:** Wireshark, Apache Access Logs
- **Digital Forensics:** Autopsy
- **Frameworks:** MITRE ATT&CK, NIST Incident Response Lifecycle

## Attack Simulation Overview

To generate detectable traffic and forensic artifacts, a controlled attack simulation was conducted against the DVWA endpoint. This phase involved:
- Manual SQL injection testing to identify vulnerabilities.
- Vulnerability validation and exploitation using `sqlmap`.
- Database enumeration to map backend structures.
- Controlled extraction of DVWA dummy records to simulate data exfiltration.

![SQL Injection Test](screenshots/02-sqli-test.png)
*Manual execution of a SQL injection payload against the DVWA target, extracting dummy user records to simulate a data breach.*

## Detection Engineering

A critical component of the lab was configuring defensive mechanisms to identify the simulated attacks. This involved deploying Suricata IDS and developing a custom detection rule designed to trigger on SQL injection indicators within HTTP traffic destined for the vulnerable DVWA endpoint. 

*(Note: The original Suricata rule file is no longer available as a raw text artifact, but its exact syntax has been successfully recovered from the original lab evidence.)*

![Suricata Rule](screenshots/05-suricata-rule.png)
*Custom Suricata IDS rule developed to detect SQL injection indicators targeting the vulnerable DVWA endpoint.*

![Suricata Alert](screenshots/06-suricata-alert.png)
*Suricata IDS alerts generated in response to the controlled SQL injection simulation, demonstrating successful network-based detection.*

## Network and Log Analysis

Following the attack simulation, network traffic and server logs were analyzed to trace the attacker's actions. This involved examining:
- **Wireshark Packet Captures:** Inspecting HTTP payloads for SQL syntax and automated tool signatures.
- **Apache Access Logs:** Reviewing web server requests to identify targeted endpoints and suspicious request patterns.

![Wireshark Analysis](screenshots/07-wireshark-analysis.png)
*Wireshark inspection of HTTP traffic associated with the controlled SQL injection simulation, providing network-level evidence that complements the Suricata IDS alerts and Apache server logs.*

## Digital Forensics

Evidence from multiple sources was consolidated and investigated using digital forensics principles, supported by tools such as Autopsy. The investigation correlated key indicators to build a timeline of the attack, including:
- Source (Attacker) IP addresses
- Destination (Victim) IP addresses
- Requested HTTP endpoints and URIs
- HTTP activity (GET/POST methods, status codes)
- SQL injection indicators in parameters
- Timestamps (where available across logs and network captures)

![Autopsy Analysis](screenshots/09-autopsy-analysis.png)
*Digital forensic investigation in Autopsy, correlating Apache access logs to identify HTTP requests containing SQL injection indicators.*

## MITRE ATT&CK Mapping

The lab and associated research involved mapping adversary behaviors to the MITRE ATT&CK framework. It is important to distinguish between the techniques analyzed theoretically versus those demonstrated practically:

**Techniques analyzed as part of the MOVEit breach case study:**
- T1190 - Exploit Public-Facing Application
- T1505.003 - Web Shell
- T1036 - Masquerading
- T1082 - System Information Discovery
- T1083 - File and Directory Discovery
- T1213 - Data from Information Repositories
- T1005 - Data from Local System
- T1041 - Exfiltration Over C2 Channel

**Behaviors practically demonstrated in the DVWA lab:**
- Exploitation of a web application vulnerability (SQL Injection).
- Automated database enumeration and data extraction.

## Incident Response

Based on the forensic findings and aligned with NIST incident response concepts, a response workflow was developed to address the simulated compromise:

![Incident Response Workflow](screenshots/11-incident-response.png)
*Overview of the incident response playbook developed to address the simulated web application compromise based on NIST guidelines.*

1. **Detection:** Identifying the attack via IDS alerts and log anomalies.
2. **Validation:** Confirming the SQL injection was successful and not a false positive.
3. **Evidence Preservation:** Securing logs and packet captures for analysis.
4. **Exposure Assessment:** Determining what database records were accessed.
5. **Containment:** Blocking the attacker's IP and taking the vulnerable application offline.
6. **Remediation:** Patching the SQL injection vulnerability in the application code.
7. **Credential Review/Reset:** Invalidating potentially compromised sessions or credentials.
8. **Recovery:** Restoring the application to normal operations.
9. **Monitoring:** Implementing enhanced detection rules to prevent recurrence.
10. **Lessons Learned:** Updating security policies and training based on the incident.

## Documentation

| Phase | Description |
|---|---|
| [Lab Setup](docs/lab-setup.md) | Architecture and isolation boundaries of the controlled environment. |
| [Attack Simulation](docs/attack-simulation.md) | Controlled SQL injection testing against the DVWA target. |
| [Detection Engineering](docs/detection-analysis.md) | Suricata IDS rule development and alert analysis. |
| [Digital Forensics](docs/forensic-investigation.md) | Correlation of Apache logs and PCAP evidence using Autopsy. |
| [MITRE ATT&CK](docs/mitre-attack.md) | TTP mapping of the MOVEit breach case study. |
| [Incident Response](docs/incident-response.md) | NIST-aligned response workflow for a web application compromise. |

## Skills Demonstrated

- Network intrusion detection
- Suricata IDS rule analysis
- Network traffic analysis with Wireshark
- Web attack analysis (SQL injection testing in a controlled lab)
- Apache access-log analysis
- Digital forensics with Autopsy
- Evidence correlation across multiple security sources
- MITRE ATT&CK mapping
- Incident response planning

## Ethical and Safety Scope

All practical activities documented in this repository were performed in an isolated, locally hosted virtual environment (Kali Linux attacking Metasploitable 2) as part of an authorized university assignment. No external systems, networks, or real-world applications were targeted or compromised. This project serves purely as an educational portfolio piece demonstrating defensive security methodologies.

## Limitations

This repository is a post-event reconstruction of documentation from a completed academic lab. The original Kali Linux virtual machine and raw forensic artifacts (such as original packet captures and server logs) are no longer available. The documentation relies on the original final report, and no artifacts or evidence have been fabricated.
