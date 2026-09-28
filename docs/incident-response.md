# Incident Response Workflow

Based on the forensic findings and aligned with NIST incident response concepts, a proposed response workflow was planned to address the simulated scenario:

![Incident Response Playbook](../screenshots/11-incident-response.png)
*Overview of the incident response playbook developed to address the simulated web application scenario based on NIST guidelines.*

## 1. Detection
Identifying the anomalous activity via IDS alerts and unusual entries in the Apache HTTP access logs.

## 2. Validation
Confirming the observed request matched the simulated SQL injection activity by correlating the IDS alerts with server logs and network packet captures to eliminate false positives.

## 3. Evidence Preservation
Securing logs and packet captures for analysis to ensure data integrity before any remediation actions occur.

## 4. Exposure Assessment
Assessing which database records may have been exposed or accessed by querying logs and analyzing database interactions during the SQL injection simulation.

## 5. Containment
Proposing actions to block the attacker's IP address at the firewall and temporarily restrict access to the vulnerable web endpoint to halt the simulated activity.

## 6. Remediation
Identifying application patching requirements, such as input sanitization or parameterized queries, to address the SQL injection flaw.

## 7. Credential Review
Evaluating potentially exposed authentication data by checking if the accessed database records contained session tokens, and recommending credential resets for affected dummy users.

## 8. Recovery
Defining steps to safely restore the application to normal operations after proposed remediation actions are applied.

## 9. Monitoring
Implementing enhanced detection rules to monitor the vulnerable endpoint for recurring patterns.

## 10. Lessons Learned
Conducting a post-incident review to document findings, evaluate the effectiveness of the detection mechanisms, and identify areas for improvement in response procedures.
