# Week 4 – Initial System Configuration & Security (SSH and Firewall Hardening)

## Overview
Week 4 focused on implementing foundational security controls on the Linux server with an emphasis on secure remote administration. All configuration tasks were performed remotely via SSH from the administrator’s workstation, in line with the assessment constraint. The primary objectives were to harden SSH access, restrict network exposure using a firewall, and enforce proper user privilege management.

---

## SSH Key-Based Authentication Configuration
Secure Shell (SSH) was configured to use public key authentication to eliminate reliance on password-based logins. A cryptographic key pair was generated on the administrator’s workstation, and the public key was securely deployed to the server. This ensures that only authorised clients possessing the private key can access the system.

Once key-based access was verified, password authentication was disabled to reduce exposure to brute-force and credential-based attacks.

This approach significantly strengthens remote access security while maintaining administrative usability.

**Evidence – SSH Key Pair Generation (Workstation)**

<img width="1639" height="856" alt="week4_public_key_workstation" src="https://github.com/user-attachments/assets/222bee84-39e1-48dc-b83a-590e01d093cc" />

---


## SSH Hardening and Root Access Restriction
To minimise the attack surface, SSH was hardened by restricting privileged access paths. Direct root login over SSH was disabled, requiring administrators to authenticate as a standard user and elevate privileges using `sudo` when necessary. This improves accountability and reduces the risk associated with direct root compromise.

SSH configuration changes were applied via the `/etc/ssh/sshd_config` file and validated by restarting the SSH service without interrupting remote access.

**Evidence**
<img width="1761" height="968" alt="week4_password_auth_disabled" src="https://github.com/user-attachments/assets/9b84e2a6-12b5-4170-abd1-3a1253b2f5e0" />

---

## User Management and Privilege Control
A dedicated non-root administrative user was created to enforce the principle of least privilege. This user was granted administrative capabilities through membership in the `sudo` group, allowing controlled privilege escalation when required.

All administrative actions were performed using this non-root account, ensuring that routine operations were not executed with unrestricted root privileges.

**Evidence -Non-root Administrative User Creation**

<img width="1297" height="815" alt="week4_user_creation" src="https://github.com/user-attachments/assets/0ca0346b-4e35-4b26-82ea-a7fee7f652f9" />

---

**Evidence – Sudo Privilege Assignment**

<img width="1285" height="807" alt="week4_sudo_assignment" src="https://github.com/user-attachments/assets/ace296f5-14e2-442a-9725-2cbcaaaa5cac" />

---

**Evidence – Privilege Escalation Using Sudo**

<img width="1280" height="803" alt="week4_sudo_usage" src="https://github.com/user-attachments/assets/76b886f3-b604-45c5-9c85-912fab6f2c8a" />

---

## Firewall Configuration with Restricted SSH Access
A host-based firewall was configured to control inbound network traffic. SSH access was explicitly permitted **only** from the administrator’s workstation IP address, while all other inbound SSH attempts were denied by default. This significantly limits the exposure of the SSH service to unauthorised sources.

The firewall ruleset was reviewed in full to confirm that only essential services were allowed and that default deny policies were enforced.

---

## Firewall Configuration with Restricted SSH Access

To further reduce the server’s network attack surface, a host-based firewall was configured using UFW (Uncomplicated Firewall). The firewall enforces a default-deny policy for inbound connections while allowing necessary outbound traffic for normal system operation.
SSH access was explicitly restricted to the administrator’s workstation IP address only. All other inbound SSH connection attempts are denied by default, ensuring that remote administrative access is limited to a single trusted source.

This configuration provides an additional security layer by blocking unauthorised network access before authentication mechanisms are reached, complementing the SSH hardening measures implemented earlier in this phase.

**Evidence – Firewall Ruleset Showing Restricted SSH Access**

<img width="1270" height="796" alt="firewall_restricted_ssh" src="https://github.com/user-attachments/assets/538065f5-6c0b-4bf6-a710-5ce224beb668" />


## Remote Administration via SSH
All configuration and management tasks during this phase were executed remotely over SSH from the administrator’s workstation. This demonstrates secure remote administration practices and confirms that local console access was not required for system management.

Successful SSH access using key-based authentication validated the correctness of the configuration and ensured that administrative access remained available after hardening measures were applied.

**Evidence – Successful SSH Login Using Key-Based Authentication**

<img width="1919" height="1063" alt="week4_ssh_key_login" src="https://github.com/user-attachments/assets/091383fb-ea09-46e2-8d36-73aea6ff6ac1" />

---

## Configuration Validation
After applying security configurations, service status and access behaviour were verified to ensure stability and correctness. SSH service availability was confirmed following configuration changes, and firewall rules were reviewed to validate correct enforcement.

This validation step ensured that security improvements did not introduce service disruption or administrative lockout.

**Evidence**

<img width="1280" height="808" alt="week4_ssh_service_status" src="https://github.com/user-attachments/assets/949032c2-00c7-44d6-b008-7a05b75b0f9a" />

---

## Security Rationale
The controls implemented in this phase establish a strong security baseline for the server. Key-based SSH authentication, restricted root access, controlled privilege escalation, and firewall-enforced network restrictions work together to reduce attack surface and prevent unauthorised access.

These measures form a foundational layer of defence that supports more advanced security mechanisms introduced in later stages.

---

## Reflection
Week 4 highlighted the importance of securing administrative access paths early in system deployment. Implementing SSH hardening and firewall restrictions demonstrated how small configuration changes can significantly improve security posture. Enforcing non-root administration also reinforced best practices for accountability and risk reduction, providing a solid foundation for subsequent security enhancements.
