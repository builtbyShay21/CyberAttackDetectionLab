# MITRE ATT&CK Mapping

The MITRE ATT&CK framework was utilized to translate observed and researched attacker behaviors into standardized defensive terminology. This ensures a consistent understanding of adversary tactics and techniques for detection and response planning.

It is important to distinguish between the techniques analyzed theoretically during the case-study research of the 2023 MOVEit Transfer breach and the behaviors practically represented within the controlled DVWA lab simulation.

![MOVEit TTP Mapping](../screenshots/MOVEit%20Transfer%20Data%20Breach%202023%20-%20TTP%20Mapping.svg)
*Theoretical mapping of the MOVEit Transfer (CVE-2023-34362) breach techniques to the MITRE ATT&CK framework for the case-study analysis.*

| Technique ID | Technique | Context |
| :--- | :--- | :--- |
| **T1190** | Exploit Public-Facing Application | Both (Case-study analysis of the MOVEit breach & Behaviour conceptually represented within the controlled lab via DVWA SQLi) |
| **T1505.003** | Web Shell | Case-study analysis of the MOVEit breach |
| **T1036** | Masquerading | Case-study analysis of the MOVEit breach |
| **T1082** | System Information Discovery | Case-study analysis of the MOVEit breach |
| **T1083** | File and Directory Discovery | Case-study analysis of the MOVEit breach |
| **T1213** | Data from Information Repositories | Both (Case-study analysis of the MOVEit breach & Behaviour conceptually represented within the controlled lab via DVWA database enumeration) |
| **T1005** | Data from Local System | Case-study analysis of the MOVEit breach |
| **T1041** | Exfiltration Over C2 Channel | Case-study analysis of the MOVEit breach |

*Note: Not all techniques listed above were executed against the DVWA environment. The table clarifies the scope of the theoretical analysis versus the practical demonstration.*
