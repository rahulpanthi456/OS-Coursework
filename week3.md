
# Week 3 – Firewall Configuration and SSH Hardening


## Overview
Week 3 focused on actively hardening the server by restricting network access and strengthening remote authentication controls. A host-based firewall was configured to limit exposed services, and SSH settings were reviewed with the aim of reducing common attack vectors such as brute-force password attacks and unauthorized access.

---

## Firewall Activation and Rule Definition
The Uncomplicated Firewall (UFW) was enabled to enforce network-level access control. Before activation, SSH access was explicitly allowed to prevent accidental lockout.

The firewall was configured to:
- Allow incoming SSH connections
- Deny all other unsolicited inbound traffic by default
- Allow all outbound traffic

This ensures that only explicitly permitted services are reachable while maintaining system usability.

**(Evidence: `ufw status verbose` after activation)**

<img width="1284" height="815" alt="week3_ufw_active" src="https://github.com/user-attachments/assets/8e03caa6-40b7-4aa5-ad4f-3e03602013ca" />

---

## Verification of Open Ports
After enabling the firewall, active listening services were rechecked using `ss -tuln`. The output confirmed that SSH remained accessible on port 22 and that no additional services were unintentionally exposed.

This validation step confirms that firewall rules are functioning as intended and that access is tightly controlled.

**(Evidence: listening services screenshot)**

<img width="1291" height="807" alt="week3_listening_services" src="https://github.com/user-attachments/assets/93fb8a07-6f12-4c76-9fea-b5886319d806" />

---

## SSH Authentication Review
The SSH daemon configuration file (`/etc/ssh/sshd_config`) was reviewed to assess authentication mechanisms. Password authentication and PAM integration were identified as active, while insecure options such as empty passwords were disabled.

This configuration provides a functional baseline but highlights opportunities for further hardening, such as disabling password-based login and enforcing SSH key authentication in future stages.

**(Evidence: sshd_config review screenshot)**

<img width="1287" height="810" alt="week3_ssh_config_review" src="https://github.com/user-attachments/assets/0afe23d0-4646-4236-b0a8-002687e71f77" />

---

## Service Reliability and Status Confirmation
The SSH service was checked using `systemctl status ssh` to ensure it remained active after firewall changes. The service was confirmed to be running and listening on both IPv4 and IPv6 interfaces.

Ensuring service availability after security changes is critical to avoid self-inflicted denial of service.

**(Evidence: SSH service status screenshot)**

<img width="1290" height="804" alt="week3_ssh_status" src="https://github.com/user-attachments/assets/743f2bb2-ebe3-4e61-ba64-cbe2210082d9" />

---

## Security Rationale
Firewall enforcement significantly reduces the system’s attack surface by limiting exposed entry points. Combined with SSH configuration review, this creates a layered defense model where network filtering and authentication controls work together.

This approach aligns with the principle of least privilege by allowing only what is required for administration.

---

## Reflection
Week 3 marked the transition from system inspection to active security enforcement. Enabling the firewall and validating SSH access demonstrated how defensive controls can be applied without disrupting functionality. These changes establish a strong foundation for future enhancements such as SSH key-only authentication, intrusion detection, and automated monitoring.
