# Week 5 – Advanced Security Controls and Monitoring

Week 5 focused on implementing advanced security mechanisms and establishing monitoring capabilities to strengthen the server beyond basic hardening. Building on firewall configuration, SSH hardening, and intrusion prevention from earlier phases, this stage aimed to introduce access control enforcement, automated security maintenance, and verification mechanisms.

The objective of this phase was to ensure that security controls are not only configured, but actively enforced, monitored, and verifiable through automated checks and scripts.

---

## Mandatory Access Control Using AppArmor

AppArmor, a Mandatory Access Control (MAC) framework, is used by Ubuntu to limit application behavior and mitigate the effects of possible breaches. To make sure that security profiles are upheld on the system, AppArmor was activated and validated.

AppArmor profiles that were already in place were examined to make sure that services like SSH are restricted in accordance with established security rules. By stopping processes from accessing unapproved resources, this method lowers the attack surface.
Evidence

**Evidence**

<img width="1288" height="805" alt="week5_apparmor_status" src="https://github.com/user-attachments/assets/bd3f3d6f-f3de-460e-95be-77a0800e3aa2" />

---

## Automatic Security Updates Configuration

The unattended-upgrades mechanism was used to set up automatic security updates to lessen exposure to known vulnerabilities. This guarantees the automatic application of crucial security updates without the need for human intervention.

The configuration was checked to make sure that automatic updates are properly scheduled and that security repositories are enabled. By reducing patching delays, this measure enhances long-term system resilience.

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

<img width="1290" height="815" alt="week5_security_baseline_script" src="https://github.com/user-attachments/assets/1c2c3133-8cb6-420b-8453-09cafa775c7d" />

---

## Remote Monitoring Script

A remote monitoring script (`monitor-server.sh`) was developed on the workstation to collect live system performance metrics from the server over SSH. The script retrieves information such as CPU usage, memory utilisation, disk space, and system uptime.

This enables lightweight remote monitoring without requiring additional third-party tools and demonstrates secure remote administration practices.

**Evidence**

<img width="1274" height="799" alt="week5_monitor_server_execution" src="https://github.com/user-attachments/assets/56feabc4-1946-45fb-b02c-58e23636fe70" />

---

## Security Analysis

The implementation of access control, automated updates, intrusion detection, and verification scripts significantly strengthens the server’s security posture. These measures ensure that controls are continuously enforced, monitored, and auditable.

Automating verification and monitoring reduces reliance on manual checks and supports consistent security management practices.

---

## Reflection

Week 5 represented a shift from static hardening to active security management. Introducing access control enforcement, automated updates, and verification scripts highlighted the importance of maintaining security over time rather than relying solely on initial configuration. This phase established a foundation for continuous monitoring, auditing, and operational security.
