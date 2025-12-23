
# Week 6 – System Monitoring, Auditing, and Log Analysis

## Overview
Week 6 focused on monitoring system activity and analysing security-related logs to gain visibility into system behaviour. Building on the hardening and protection mechanisms implemented in previous weeks, this stage emphasised detection, verification, and accountability rather than prevention alone.

The objective was to understand how system logs, audit outputs, and service status information can be used to identify anomalies, validate security controls, and support incident investigation.

---

## Importance of Monitoring and Auditing
Preventive controls such as firewalls, SSH hardening, and intrusion prevention reduce attack surfaces, but they do not eliminate risk entirely. Monitoring and auditing provide the ability to observe what is happening on the system in real time or retrospectively.

This week reinforced the idea that:
- Security is not complete without visibility
- Logs act as evidence during incident analysis
- Regular review helps detect misconfigurations or suspicious behaviour early

---

## System Log Review
Key system logs were examined to understand how Linux records authentication events, service activity, and security warnings. Logs related to SSH access and system services were particularly relevant, as SSH remains the primary administrative access method.

Reviewing log files demonstrated how:
- Successful and failed login attempts are recorded
- Service restarts and failures are tracked
- Security tools such as Fail2Ban generate meaningful log entries

These logs provide a reliable audit trail for administrative and security events.

---

## Security Tool Output Analysis
Outputs from previously installed security tools were reviewed to validate their operational status and effectiveness. This included confirming that intrusion prevention services were running and that security audits produced actionable feedback.

Analysing tool output reinforced the importance of not only deploying security mechanisms but also verifying that they are functioning as expected.

---

## Auditing as a Continuous Process
Rather than treating auditing as a one-time task, this week highlighted the need for continuous monitoring. Regular log inspection and audit review enable administrators to:
- Detect repeated access attempts
- Identify configuration drift
- Track the impact of security changes over time

This approach supports a proactive security posture rather than reactive response.

---

## Security Rationale
Monitoring and auditing strengthen system security by providing awareness and traceability. Even well-hardened systems require oversight to ensure controls remain effective and that no unexpected behaviour goes unnoticed.

By integrating log analysis with previously implemented hardening measures, the system moves closer to a mature security model based on prevention, detection, and response.

---

## Reflection
Week 6 emphasised the operational side of security management. While earlier weeks focused on configuration and protection, this stage highlighted the value of visibility and verification. Understanding system logs and audit outputs improved confidence in the system’s security posture and prepared the foundation for future incident response and optimisation.
