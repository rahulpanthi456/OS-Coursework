# Week 1 – System Planning and Distribution Selection

## 1. Objective
The objective of Week 1 was to plan and deploy a secure, headless Linux server environment and verify its baseline configuration using command-line tools. This phase focuses on system planning, operating system selection, and architectural justification, establishing a stable and verifiable foundation for secure remote administration, system hardening, monitoring, and performance analysis in subsequent weeks.

---

## 2. System Architecture and Planning
A dual-system architecture was designed to reflect real-world Linux server administration practices. The environment consists of a host workstation and a headless Linux server virtual machine, connected via a controlled virtual network to enable secure remote management while maintaining isolation from external networks.

<img width="693" height="167" alt="System-architecture-planning" src="https://github.com/user-attachments/assets/f91cf55d-00ef-4fe0-8465-d16019761d28" />

---

### System Components
- **Host Workstation**
  - Used for system administration, SSH access, documentation, and monitoring.
  - Runs Oracle VirtualBox as the virtualisation platform.

- **Guest Server**
  - Ubuntu Server 24.04 LTS installed without a graphical user interface.
  - Operated entirely through the command line via SSH.

### Network Architecture
- A **Host-only network adapter** was used.
- This allows communication between the host and server VM while preventing direct exposure to external networks.
- SSH is used for secure remote administration.

*A system architecture diagram illustrating the host workstation, Ubuntu Server VM, network connection, and SSH access is included in the journal.*

---

## 3. Distribution Selection Justification
Ubuntu Server 24.04 LTS was selected as the server operating system after considering alternative Linux distributions such as Debian and Rocky Linux.

- **Ubuntu Server LTS**
  - Long-term support with five years of security updates.
  - Extensive documentation and strong community support.
  - Widely used in enterprise and cloud environments.
  - Large software repositories suitable for security tools, monitoring utilities, and performance testing.

- **Debian**
  - Highly stable but slower release cycle.
  - Less up-to-date packages compared to Ubuntu LTS.

- **Rocky Linux**
  - Enterprise-focused and stable.
  - More complex for beginners and less suitable for rapid experimentation within coursework constraints.

Ubuntu Server 24.04 LTS was therefore selected as it provides a strong balance between stability, security, modern software availability, and industry relevance.

---

## 4. Workstation Configuration Decision
The workstation was selected as the primary management platform to provide a stable environment for virtualisation, SSH-based server administration, and coursework documentation.

- Oracle VirtualBox was selected as the virtualisation platform because it is free, widely supported, and suitable for running Linux server virtual machines.
- The workstation provides a controlled environment for SSH-based administration, reducing the need for a graphical interface on the server and aligning with professional server management practices.

This separation of workstation and server roles mirrors real-world system administration workflows.

---

## 5. Network Configuration
The Ubuntu Server virtual machine was configured with the following VirtualBox network settings:

- **Adapter Type:** Host-only Adapter
- **IP Assignment:** DHCP
- **Purpose:** Secure communication between host and server without external exposure

Using a host-only network reduces the attack surface during initial deployment while still enabling full remote administration through SSH. This configuration is appropriate for a development and learning environment where security and isolation are prioritised.

---

## 6. System Verification Using CLI Tools
After installation, system specifications and configuration were verified using standard Linux command-line tools:

- `uname -a` was used to confirm the running Linux kernel and system architecture.
- `lsb_release -a` verified the installed Ubuntu Server version.
- `free -h` confirmed available memory and swap configuration.
- `df -h` verified disk usage and logical volume management.
- `ip addr` confirmed network interface configuration and IPv4 assignment.

**Evidence**

<img width="1290" height="804" alt="week1_system_information" src="https://github.com/user-attachments/assets/e6d5d412-10c6-405a-881f-e8946f28b9cb" />

---

## 7. Conclusion
Week 1 successfully completed the planning and deployment phase of the coursework. A headless Ubuntu Server virtual machine was installed, justified against alternative distributions, and verified using standard CLI tools. The system architecture, workstation choice, and network configuration were all designed to reflect real-world server administration practices. This verified baseline provides a secure and stable foundation for system hardening, monitoring, and performance evaluation in subsequent weeks.
