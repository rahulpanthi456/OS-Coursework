# Week 6 – System Monitoring, Auditing, and Log Analysis

## Overview
Week 6 focused on monitoring system activity and analysing security-related logs to gain visibility into system behaviour. Building on the hardening and protection mechanisms implemented in previous weeks, this stage emphasised detection, verification, and accountability rather than prevention alone.

The objective was to understand how system logs, audit outputs, and service status information can be used to identify anomalies, validate security controls, and support incident investigation.

---

## Importance of Monitoring and Auditing
Preventive controls such as firewalls, SSH hardening, and intrusion prevention reduce attack surfaces, but they do not eliminate risk entirely. Monitoring and auditing provide the ability to observe what is happening on the system in real time or retrospectively.

This week reinforced the idea that:
- Security is incomplete without visibility
- Logs act as evidence during incident analysis
- Regular review helps detect misconfigurations or suspicious behaviour early

---

## System Log Review
Key system logs were examined to understand how Linux records authentication events, service activity, and administrative actions. Logs related to SSH access were reviewed to verify how login attempts, service restarts, and configuration checks are recorded.

Reviewing authentication logs demonstrated how:
- SSH service start events are logged
- Administrative actions using sudo are recorded
- Configuration validation commands leave an audit trail

**Evidence – SSH Authentication Log Review**

<img width="1289" height="811" alt="week6_auth_log_ssh" src="https://github.com/user-attachments/assets/00fbb624-f980-457b-af4e-22f7d6f5532f" />

---

## Security Tool Log Analysis
Security-related log files were reviewed to validate the operational state of previously deployed protective mechanisms. Examining these logs provides confirmation that security monitoring services are active and responding to system events.

The intrusion prevention logs demonstrated that:
- SSH monitoring rules are active
- Log scanning is functioning correctly
- The system is prepared to respond to suspicious access behaviour

**Evidence – Security Tool Log Output**

<img width="1286" height="808" alt="week6_fail2ban_log" src="https://github.com/user-attachments/assets/b2bf604b-5ae9-42d1-96f2-6d29fbcc29cd" />

---

## Service Status Verification
Service status checks were performed to confirm that critical monitoring and security services were running as expected. This ensures that logging and intrusion prevention mechanisms remain enforced at runtime.

**Evidence – Intrusion Prevention Service Status**

<img width="1294" height="817" alt="week6_fail2ban_status" src="https://github.com/user-attachments/assets/a8525a67-c621-409f-baf5-f550052a88e2" />

---

## SSH Service Monitoring
The SSH service status was verified to confirm continued availability following previous hardening measures. Monitoring service health ensures secure administrative access is maintained without introducing service disruption.

**Evidence – SSH Service Status**

<img width="1292" height="815" alt="week6_ssh_status" src="https://github.com/user-attachments/assets/9625fa73-a6a1-4e67-82a6-3e8dfd371227" />

---

## Security Rationale
Monitoring and auditing strengthen system security by providing awareness and traceability. Even well-hardened systems require oversight to ensure controls remain effective and that no unexpected behaviour goes unnoticed.

By integrating log analysis with previously implemented security measures, the system moves closer to a mature security model based on prevention, detection, and response.

---

## Reflection
Week 6 emphasised the operational side of security management. While earlier weeks focused on configuration and protection, this stage highlighted the importance of visibility and verification. Understanding system logs and service status outputs improved confidence in the system’s security posture and laid the groundwork for future incident response and optimisation.
