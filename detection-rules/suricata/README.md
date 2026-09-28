# Suricata Detection Rules

This directory contains `local.rules`, a custom Suricata IDS rule utilized during the lab simulation.

**Note:** The original raw rule file was no longer available. The rule contained in `local.rules` was accurately recovered syntax-for-syntax from the original lab screenshot evidence, which can be viewed here: [05-suricata-rule.png](../../screenshots/05-suricata-rule.png).

This rule was designed specifically to identify the SQL injection activity (and exact URIs) used in the controlled DVWA lab simulation. It should be treated strictly as a lab-specific detection rule used for demonstrating network security monitoring concepts, rather than a production-ready generic SQL injection signature.
