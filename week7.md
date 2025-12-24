
# Week 7 – Security Audit and System Evaluation

## 1. Objective
The objective of Week 7 was to conduct a comprehensive security audit of the Ubuntu Server environment and evaluate its overall system configuration. This phase focuses on identifying security weaknesses, applying remediation measures, and assessing residual risks using industry-standard security auditing and network scanning tools.

---

## 2. Infrastructure Security Assessment
The system under evaluation is a headless Ubuntu Server 24.04 LTS virtual machine hosted on a Windows workstation using Oracle VirtualBox. The server is administered remotely via SSH over a host-only network, ensuring isolation from external networks while maintaining secure management access.

The infrastructure was designed with a minimal attack surface, no graphical interface, and limited exposed services. This assessment evaluates the effectiveness of these design choices through automated security auditing, network scanning, access control verification, and service inspection.

---

## 3. Lynis Security Audit Results

### 3.1 Initial Lynis Audit (Pre-Remediation)
An initial security audit was conducted using Lynis to assess the baseline security posture of the system. The scan identified multiple warnings and suggestions related to system hardening, service configuration, and security best practices.

The initial hardening index score reflected a partially secured system, typical of a default server installation.

**Screenshot evidence of the initial Lynis scan output and hardening index is provided.**

<img width="1282" height="805" alt="week7_lynis_before" src="https://github.com/user-attachments/assets/4dacdaa2-44eb-4c31-a737-2d9a97f9f208" />

---

### 3.2 Remediation Actions
Based on the Lynis recommendations, selected remediation actions were applied to improve system security. These actions focused on practical and relevant hardening measures suitable for the coursework environment, including:

- Strengthening SSH configuration
- Ensuring firewall enforcement
- Verifying system update policies
- Disabling or confirming the absence of unnecessary services

Not all Lynis suggestions were implemented, as some recommendations were either not applicable to a virtualised lab environment or could introduce unnecessary complexity beyond the scope of this coursework.

---

### 3.3 Follow-Up Lynis Audit (Post-Remediation)
After remediation, a second Lynis scan was performed to evaluate the impact of the applied security controls. The follow-up audit showed an improvement in the hardening index score, confirming that the remediation steps had a positive effect on the system’s security posture.

**Screenshot evidence of the post-remediation Lynis scan and updated hardening index is provided.**

<img width="1276" height="803" alt="week7_Lynis_after" src="https://github.com/user-attachments/assets/fbe3da27-eda8-4e51-9a0a-3b466d0b46a3" />

---

### 3.4 Lynis Score Comparison
A comparison of the Lynis hardening index before and after remediation demonstrates measurable security improvement.

| Audit Stage        | Hardening Index |
|-------------------|-----------------|
| Pre-Remediation   | 60              |
| Post-Remediation  | 61              |


This comparison confirms that targeted security improvements were successfully implemented.

---

## 4. Network Security Assessment (nmap)

A network security assessment was conducted using `nmap` to identify open ports and exposed services on the Ubuntu Server.

The scan results showed that only essential ports required for system operation were open. No unexpected or unnecessary network services were detected.

**Screenshot evidence of the nmap scan output is provided.**

<img width="1288" height="814" alt="week7_nmap_scan" src="https://github.com/user-attachments/assets/c189fdeb-90f2-4773-8d76-ad937a793d30" />

---

### Interpretation of Results
- Open ports were limited to services explicitly required for remote administration.
- The absence of additional open ports reduces the system’s external attack surface.
- Network exposure is appropriate for a host-only, non-internet-facing environment.

---

## 5. SSH Access Control Verification
SSH access control was reviewed to ensure secure remote administration practices were in place. The verification focused on authentication methods, privilege restrictions, and configuration hardening.

Key observations include:
- SSH is the only remote access service enabled.
- Root login over SSH is restricted.
- Access is limited to authorised users.

These controls reduce the risk of unauthorised access while maintaining necessary administrative functionality.

**Screenshot evidence of SSH configuration verification is provided.**

<img width="1282" height="810" alt="week7_ssh_config" src="https://github.com/user-attachments/assets/fb5cbe51-f98a-4e08-ba9b-f56ad333ff94" />

---

## 6. Service Audit and Justification
A service audit was conducted to identify all active system services. Only essential services required for system operation and remote management were found to be running.

### Service Inventory
- **SSH** – Required for secure remote administration.
- **System logging services** – Required for monitoring and auditability.
- **Core system services** – Required for operating system functionality.

No unnecessary or unused services were identified. Limiting running services reduces potential attack vectors and aligns with the principle of least privilege.

**Screenshot evidence of running services is provided.**

<img width="1283" height="806" alt="week7_running_services" src="https://github.com/user-attachments/assets/aba0ceeb-1492-4807-a9d7-141c92f40361" />

Security-focused services such as auditd and fail2ban are intentionally enabled to support system auditing and protection against brute-force attacks, while Postfix is configured in local-only mode to support security alerting without exposing additional network services.


---

## 7. System Configuration Review
A review of the overall system configuration confirmed that:
- Firewall controls are enabled and enforced.
- Security updates are configured to ensure the system remains up to date.
- Logging mechanisms are active to support monitoring and incident analysis.

The system configuration demonstrates a consistent and layered security approach, combining access control, service minimisation, and system hardening.

---

## 8. Remaining Risks and Limitations
Despite the applied security controls, some residual risks remain. These include:
- Dependence on SSH key management practices, where compromised private keys could still present a security risk if not adequately protected.
- Potential vulnerabilities introduced by future package updates.
- Limitations inherent to a virtualised environment.

These risks are considered acceptable within the scope of a controlled coursework environment and can be further mitigated in future iterations through additional hardening measures such as enforced key-based authentication and enhanced monitoring.

---

## 9. Conclusion
Week 7 successfully evaluated the security posture of the Ubuntu Server system through structured auditing and analysis. Lynis and nmap were used to identify weaknesses and validate remediation efforts, resulting in an improved security configuration. Access controls, service exposure, and system configuration were verified and justified. While some residual risks remain, the system demonstrates a strong and appropriate security posture for its intended purpose.
