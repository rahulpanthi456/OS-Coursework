
# Week 2 – User Access Control and Secure Remote Access


## Overview
The focus of Week 2 was to configure secure user access and establish controlled remote administration using SSH. This involved validating user privileges, reviewing authentication mechanisms, and verifying which services were exposed on the system. 
These steps form the foundation for securing administrative access before introducing advanced hardening measures.

---

## User Identity and Privilege Verification
The default user account was verified using `whoami` and `id` to confirm the active session context and group memberships. The `sudo -l` command was then used to confirm that the user has full administrative privileges, allowing controlled execution of system-level commands.

This ensures that administrative tasks can be performed securely without enabling direct root login, which reduces attack surface.

**Evidence**

<img width="1287" height="800" alt="week2_sudo_privileges" src="https://github.com/user-attachments/assets/e27dd9f1-9990-4b3d-ac6f-4ac73ddd304f" />

---


## SSH Service Configuration and Status
Secure Shell (SSH) was reviewed as the primary method for remote server management. Initially, the SSH service was confirmed to be installed but inactive. The service was then enabled and started using systemd.

The `systemctl status ssh` command confirmed that the OpenBSD Secure Shell service is active and listening on the default port (22), enabling encrypted remote access.

**Evidence**

<img width="1287" height="808" alt="week2_ssh_status" src="https://github.com/user-attachments/assets/e456ab00-0b49-4ebf-95cd-8991ad15246e" />

---

## SSH Configuration Review
The SSH daemon configuration file (`/etc/ssh/sshd_config`) was reviewed to understand current authentication and access control settings. Password authentication was enabled, PAM authentication was active, and insecure options such as empty passwords were disabled.

This review provides visibility into default SSH security posture and prepares the system for future hardening steps such as disabling password authentication and enforcing key-based access.

**Evidence**

<img width="1292" height="806" alt="week2_ssh_config_review" src="https://github.com/user-attachments/assets/a125561c-f122-47a4-b9f1-5548d2b4ff33" />

---

## Network Services and Open Ports
Active listening services were inspected using `ss -tuln`. The output confirmed that only essential services, including SSH and local system services, were listening for connections.

No unnecessary external-facing services were exposed, reducing the server’s attack surface at this early stage.

**Evidence**

<img width="1289" height="808" alt="week2_listening_services" src="https://github.com/user-attachments/assets/632ce837-504e-4d85-9213-ef9b583cf7fe" />

---

## Firewall Status
The Uncomplicated Firewall (UFW) status was checked using `ufw status verbose`. At this stage, the firewall was inactive. This was intentionally left unchanged to ensure connectivity during early configuration and testing.

Firewall rules will be applied in later weeks once service requirements are fully defined.

**Evidence**

<img width="1285" height="804" alt="week2_ufw_status" src="https://github.com/user-attachments/assets/ebae268c-09f2-442d-a438-9bc053024c3a" />

---

## System Update State
The system’s update status was verified using `apt list --upgradable`. No pending package updates were found, confirming that the system is fully up to date following installation.

Maintaining an up-to-date system is a critical baseline security practice and reduces exposure to known vulnerabilities.

**Evidence**

<img width="1289" height="806" alt="week2_upgradable_packages" src="https://github.com/user-attachments/assets/b201589a-c67f-42b0-9fc4-6cf548b77a0d" />

---

## Reflection
Week 2 established a secure administrative baseline by confirming user privileges, enabling secure remote access, and validating exposed services. Reviewing SSH configuration and network state provided clarity on default security settings and highlighted areas for future hardening. 
These steps ensure the system is prepared for firewall enforcement, authentication hardening, and intrusion detection in subsequent weeks.
