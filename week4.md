# Week 4 – SSH Hardening and Intrusion Prevention


## Overview
Week 4 focused on strengthening remote access security by hardening the SSH service and introducing basic intrusion prevention mechanisms. Building on the firewall configuration completed in Week 3, this week aimed to reduce the risk of brute-force attacks, privilege abuse, and unauthorized access.

---

## SSH Hardening Strategy
The Secure Shell (SSH) service was identified as the primary administrative access point to the server. As a result, several configuration decisions were planned to minimise exposure while preserving administrative usability.

The hardening approach focused on:
- Restricting high-risk authentication methods
- Limiting privileged access paths
- Enforcing safer default behaviours

The SSH configuration file (`/etc/ssh/sshd_config`) was reviewed to identify insecure or permissive defaults prior to applying changes.

**Evidence**

<img width="1284" height="802" alt="week4_ssh_hardening_config" src="https://github.com/user-attachments/assets/947fbd8b-821d-4774-943e-f1fdf8b10985" />

---

## Root Login Restriction
Direct root login via SSH represents a significant security risk, as it exposes a highly privileged account to remote attack. The configuration was reviewed to ensure that root login is restricted and that administrative actions are performed through a standard user account with sudo privileges.

This approach improves accountability and reduces the impact of credential compromise.

**Evidence**
<img width="1282" height="810" alt="week4_root_login_disabled" src="https://github.com/user-attachments/assets/009a41bd-1f1a-4834-b5ae-b1d9e6c5543c" />


---

## Authentication Method Review
Password-based authentication was identified as a potential attack vector due to its susceptibility to brute-force and credential stuffing attacks. Public key authentication was verified as available, providing a more secure alternative for remote access.

Password authentication was assessed with the intention of disabling it in favour of key-based authentication once secure access was confirmed.

**Evidence**
<img width="1288" height="811" alt="week4_password_auth_disabled" src="https://github.com/user-attachments/assets/c65e57a9-86dc-4dd6-9c7f-4c30da70a15c" />

---

## Intrusion Prevention Planning
To mitigate repeated unauthorized login attempts, intrusion prevention was considered as an additional defensive layer. Rate-limiting and automatic banning of suspicious IP addresses were identified as effective countermeasures against brute-force attacks targeting SSH.

This layered defence approach complements firewall rules and authentication controls by actively responding to malicious behaviour.

**Evidence**
<img width="1293" height="806" alt="week4_fail2ban_install" src="https://github.com/user-attachments/assets/c37f3052-14b5-4435-a0b3-0a79a58f8856" />


---

## Service Continuity and Validation
After reviewing planned hardening changes, the SSH service status was consistently monitored to ensure availability was maintained. This step ensures that security improvements do not introduce accidental service disruption or administrative lockout.

---

## Security Rationale
Hardening SSH reduces the system’s exposure to common attack techniques while preserving secure administrative access. By combining firewall enforcement, restricted authentication methods, and intrusion prevention planning, the server moves closer to a defence-in-depth security model.

**Evidence**
<img width="1284" height="810" alt="week4_fail2ban_status" src="https://github.com/user-attachments/assets/8c81201b-6466-4548-9b7b-2b25249befbb" />


---

## Reflection
Week 4 represented a shift from basic protection to proactive risk reduction. Reviewing SSH configuration and planning intrusion prevention highlighted the importance of securing essential services without compromising system accessibility. These measures provide a foundation for advanced security controls and monitoring in later stages.
