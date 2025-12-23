# Week 5 – System Auditing and Security Assessment

Week 5 focused on assessing the overall security posture of the Linux server using automated auditing tools. After implementing firewall rules, SSH hardening, and intrusion prevention in earlier weeks, this stage aimed to validate those controls, identify weaknesses, and establish a measurable security baseline.

The primary tool used for this assessment was **Lynis**, a widely adopted security auditing and compliance checking utility for Linux systems.

---

## Lynis Installation and Verification

Lynis was installed using the system package manager to ensure the system could perform a structured security audit. Once installed, the tool’s availability and version were verified to confirm successful installation.

**Evidence**  

<img width="1287" height="803" alt="week5_lynis_installed" src="https://github.com/user-attachments/assets/88504bb8-9e87-4fc3-a381-d379a08b729d" />

---

## System Security Audit Execution

A full system audit was conducted using the `lynis audit system` command. This audit analysed key areas such as authentication methods, firewall rules, system services, logging configuration, and general system hardening practices.

The audit produced a summary including the number of tests performed, enabled plugins, and an overall hardening index score, providing a clear snapshot of the system’s current security state.

**Evidence**

<img width="1285" height="804" alt="week5_lynis_audit" src="https://github.com/user-attachments/assets/d409850c-a973-4bc6-b4db-ee3f741065e5" />

---

## SSH Service Status Validation

To ensure that security auditing did not disrupt essential services, the SSH service status was checked after the audit. This confirmed that the SSH daemon remained active, enabled, and listening correctly for remote administration.

This step helps demonstrate that security improvements and assessments were carried out without causing service interruption or administrative lockout.

**Evidence**  

<img width="1288" height="809" alt="week5_ssh_status" src="https://github.com/user-attachments/assets/d674baf6-e02c-40e8-ace8-218f10f0e518" />

---

## Intrusion Prevention Status Check

As intrusion prevention was introduced earlier using Fail2Ban, its operational status was reviewed during this week to ensure it remained active during system auditing. Confirming Fail2Ban’s status reinforces that defensive controls remain enforced alongside auditing activities.

**Evidence**  

<img width="1284" height="811" alt="week5_fail2ban_status" src="https://github.com/user-attachments/assets/02dc4c27-a8a6-48b2-a658-141045631f5e" />

---

## Security Analysis 

The Lynis audit highlighted that core defensive measures such as firewall enforcement, SSH service configuration, and intrusion prevention were functioning as expected. The hardening index provides a measurable indicator of the system’s current security maturity, while also identifying recommendations for further improvement, such as additional malware scanning or configuration tuning.

This audit-driven approach supports informed decision-making and ensures that security controls are not only implemented but continuously evaluated.

---

## Reflection

Week 5 marked a transition from implementation to evaluation. Running a full system audit reinforced the importance of validating security controls rather than assuming effectiveness. The insights provided by Lynis establish a clear baseline for future improvements and demonstrate a structured, professional approach to system security management.
