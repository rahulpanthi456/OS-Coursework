# Week 5 – Advanced Security Controls and Monitoring

Week 5 focused on implementing advanced security mechanisms and establishing monitoring capabilities to strengthen the server beyond basic hardening. Building on firewall configuration, SSH hardening, and intrusion prevention from earlier phases, this stage aimed to introduce access control enforcement, automated security maintenance, and verification mechanisms.

The objective of this phase was to ensure that security controls are not only configured, but actively enforced, monitored, and verifiable through automated checks and scripts.

---

## Mandatory Access Control Using AppArmor

Ubuntu uses AppArmor as its Mandatory Access Control (MAC) framework to restrict application behaviour and limit the impact of potential compromises. AppArmor was enabled and verified to ensure that security profiles are enforced on the system.

Existing AppArmor profiles were reviewed to confirm that services such as SSH are confined according to predefined security policies. This approach reduces the attack surface by preventing processes from accessing unauthorised resources.

**Evidence**

<img width="1288" height="805" alt="week5_apparmor_status" src="https://github.com/user-attachments/assets/bd3f3d6f-f3de-460e-95be-77a0800e3aa2" />

---

## Automatic Security Updates Configuration

To reduce exposure to known vulnerabilities, automatic security updates were configured using the unattended-upgrades mechanism. This ensures that critical security patches are applied automatically without manual intervention.

The configuration was verified to confirm that security repositories are enabled and that automatic updates are scheduled correctly. This measure improves long-term system resilience by minimising patching delays.

**Evidence**

<img width="1284" height="804" alt="week5_unattended_upgrades_status" src="https://github.com/user-attachments/assets/6c49cc31-2105-479c-8d67-80587ca6d2aa" />

---

## Enhanced Intrusion Detection with Fail2Ban

Fail2Ban was configured beyond basic installation to actively monitor authentication logs and respond to suspicious behaviour. SSH-related jails were reviewed to confirm appropriate values for retry limits, ban duration, and detection windows.

Log output and service status checks confirmed that Fail2Ban is actively monitoring SSH access attempts and enforcing intrusion prevention rules.

**Evidence**

<img width="1289" height="804" alt="week5_fail2ban_status" src="https://github.com/user-attachments/assets/0302e70f-f9c8-4119-ba11-9a6207cb6e1d" />

---

## Security Baseline Verification Script

A security baseline verification script (`security-baseline.sh`) was created and deployed on the server. This script automates the verification of security controls implemented during Phases 4 and 5, including:

- Firewall status
- SSH hardening settings
- Fail2Ban service state
- AppArmor enforcement
- Automatic update configuration

Each command in the script is documented with line-by-line comments to explain its purpose. The script can be executed remotely via SSH to validate the system’s security posture at any time.

**Evidence**
*(Screenshot showing execution of security-baseline.sh via SSH)*

---

## Remote Monitoring Script

A remote monitoring script (`monitor-server.sh`) was developed on the workstation to collect live system performance metrics from the server over SSH. The script retrieves information such as CPU usage, memory utilisation, disk space, and system uptime.

This enables lightweight remote monitoring without requiring additional third-party tools and demonstrates secure remote administration practices.

**Evidence**
*(Screenshot showing execution of monitor-server.sh and collected metrics)*

---

## Security Analysis

The implementation of access control, automated updates, intrusion detection, and verification scripts significantly strengthens the server’s security posture. These measures ensure that controls are continuously enforced, monitored, and auditable.

Automating verification and monitoring reduces reliance on manual checks and supports consistent security management practices.

---

## Reflection

Week 5 represented a shift from static hardening to active security management. Introducing access control enforcement, automated updates, and verification scripts highlighted the importance of maintaining security over time rather than relying solely on initial configuration. This phase established a foundation for continuous monitoring, auditing, and operational security.
