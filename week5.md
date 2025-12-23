# Week 5 – System Monitoring, Auditing, and Security Validation

## Overview
Week 5 focused on monitoring, auditing, and validating the security posture of the server following the hardening measures implemented in previous weeks. The objective was to assess system activity, verify security configurations, and establish visibility into potential risks and system behaviour.

This week marks a transition from configuration-based security to **continuous security awareness**, ensuring that defensive controls remain effective over time.

---

## Security Audit Execution
A system-wide security audit was conducted to evaluate the effectiveness of the applied configurations. Auditing tools were used to inspect system permissions, service exposure, authentication settings, and general hardening status.

The audit provided a structured assessment of the server’s security state and highlighted areas that were correctly secured as well as optional recommendations for further improvement.

---

## Service and Configuration Validation
Critical services such as SSH and Fail2Ban were reviewed to ensure they remained active and correctly configured after hardening changes. Service status checks confirmed that security controls were operational without disrupting administrative access.

This validation step ensures that security measures do not negatively impact system availability or maintainability.

---

## User Privilege and Access Review
User permissions were reviewed to confirm that administrative access is restricted to authorised users only. The use of sudo privileges was verified, reinforcing the principle of least privilege and preventing unnecessary elevation of access.

This step improves accountability and reduces the impact of potential credential compromise.

---

## Monitoring Active Services and Network Exposure
Active listening services were examined to ensure that only essential ports were exposed. Network monitoring commands were used to identify open ports and verify that firewall and intrusion prevention rules were functioning as intended.

Reducing the system’s attack surface strengthens its resilience against external threats.

---

## Security Rationale
Monitoring and auditing provide ongoing assurance that security controls remain effective beyond initial setup. By validating service status, user permissions, and system exposure, the server aligns more closely with a defence-in-depth security strategy.

These practices support early detection of misconfiguration, unauthorised changes, and emerging risks.

---

## Reflection
Week 5 highlighted the importance of continuous monitoring in maintaining system security. While configuration hardening establishes a secure baseline, auditing and validation ensure that this baseline is preserved over time. This week reinforced the role of monitoring as an essential component of real-world system administration and security management.
