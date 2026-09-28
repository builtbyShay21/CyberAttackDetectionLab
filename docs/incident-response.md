# Incident Response Workflow

Based on the findings from the forensic investigation, a structured incident response workflow was developed. This process utilizes NIST-aligned incident response concepts adapted for a web-application compromise scenario.

![Incident Response Playbook](../screenshots/11-incident-response.png)
*Overview of the incident response playbook developed to address the simulated web application compromise based on NIST guidelines.*

## 1. Detection
The initial identification of anomalous activity, triggered by Suricata IDS alerts indicating potential SQL injection payloads targeting a specific web endpoint, corroborated by unusual patterns in the Apache HTTP access logs.

## 2. Validation
The process of confirming that the detected activity represents a genuine security incident. This involves analyzing the IDS alerts and correlating them with server logs and network packet captures to eliminate false positives and confirm successful exploitation.

## 3. Evidence Preservation
Securing all relevant artifacts to ensure data integrity for forensic analysis. This includes isolating packet captures (PCAPs), creating secure copies of the Apache access logs, and capturing system states before any destructive remediation actions occur.

## 4. Exposure Assessment
Determining the scope and impact of the verified compromise. This involves querying logs and analyzing database interactions to ascertain exactly which dummy records or database tables were enumerated or extracted during the SQL injection simulation.

## 5. Containment
Taking immediate steps to prevent further damage or data exfiltration. In a web-application context, this typically involves blocking the identified attacker IP address at the firewall and temporarily restricting access to or disabling the vulnerable web endpoint.

## 6. Remediation
Addressing the root cause of the vulnerability. This requires analyzing the application's source code and applying input sanitization, parameterized queries, or software patches to eliminate the SQL injection flaw.

## 7. Credential Review
Evaluating the potential compromise of authentication data. This involves identifying if the extracted database records contained password hashes or session tokens, and subsequently initiating a credential reset for any affected dummy users.

## 8. Recovery
Carefully restoring the application and associated services to normal operational status. This step occurs only after remediation is verified and involves monitoring the restored services closely for any signs of recurring malicious activity.

## 9. Monitoring
Implementing enhanced visibility and detection mechanisms to prevent future incidents. This includes tuning Suricata IDS rules based on the observed attack patterns and configuring aggressive alerting for the previously targeted web endpoints.

## 10. Lessons Learned
Conducting a post-incident review to document findings, evaluate the effectiveness of the response workflow, and identify areas for improvement in security policies, detection engineering, and incident handling procedures.
