# Lab Environment

## Purpose

This project utilizes a strictly controlled, isolated laboratory environment designed to safely demonstrate the concepts of web application exploitation, detection engineering, and digital forensic investigation.

## Architecture

The lab consists of an attacker system and an intentionally vulnerable target system, integrated with security monitoring and forensic analysis tools.

![Lab Setup](../screenshots/01-lab-setup.png)
*Connectivity verification between the Kali Linux attacker system and the Metasploitable 2 target, establishing the isolated lab environment.*

- **Attacker System:** Kali Linux
- **Target System:** Metasploitable 2 running Damn Vulnerable Web Application (DVWA)
- **Monitoring & Evidence Sources:** Suricata IDS, Wireshark, Apache Access Logs, Autopsy

```text
Kali Linux
    |
    | controlled traffic
    v
Metasploitable 2 / DVWA
    |
    +-- Suricata IDS
    +-- Apache Logs
    +-- Wireshark
            |
            v
      Evidence Analysis
            |
            +-- Autopsy
            +-- Evidence Correlation
```

## Safety Boundaries

To adhere to ethical hacking and professional security principles, strict safety boundaries were maintained:

- **Isolated Lab:** All activity was conducted within a closed, local virtual environment.
- **Intentionally Vulnerable Target:** The target was DVWA, explicitly designed for security testing.
- **No Real-World Targets:** No external organizations, networks, or production systems were targeted.
- **No Production MOVEit Environment:** This lab did not involve a real MOVEit server.
- **No Real Credentials:** Only DVWA dummy test data was utilized and exposed during the simulation.
