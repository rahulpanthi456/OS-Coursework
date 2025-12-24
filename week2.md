# Week 2 – Security Planning and Performance Testing Methodology

## Overview
Week 2 focused on designing a security baseline and defining a structured performance testing methodology before implementing active security controls. Rather than applying hardening measures immediately, this phase concentrated on planning how system performance and security would be measured, monitored, and evaluated in later stages of the coursework. Establishing this foundation ensures that future changes can be assessed objectively and consistently.

---

## Performance Testing Plan

The performance testing approach is designed to evaluate system behaviour under different workloads while maintaining remote administration via SSH. Testing will be conducted in multiple stages to allow meaningful comparison.

### Testing Phases
1. **Baseline Testing**  
   Measure system performance under normal, idle conditions to establish a reference point.
2. **Load Testing**  
   Apply controlled workloads to stress CPU, memory, disk, and network resources.
3. **Post-Hardening Testing**  
   Re-run performance tests after security controls are applied to assess their impact.
4. **Optimisation Testing**  
   Evaluate performance improvements after tuning and configuration adjustments.

### Metrics to Be Collected
- CPU usage (% utilisation, load average)
- Memory usage (RAM and swap)
- Disk I/O throughput and latency
- Network throughput and latency
- System responsiveness and service response times

### Monitoring Tools
- `top` and `htop` for CPU and memory usage
- `free -h` and `vmstat` for memory behaviour
- `iostat` and `iotop` for disk I/O analysis
- `iperf3` and `ping` for network performance
- SSH-based command execution timing for responsiveness

All monitoring and testing will be conducted remotely via SSH to comply with administrative constraints.

---

## Security Configuration Checklist

The following checklist defines the planned security baseline for the system. These controls will be implemented and validated in later weeks.

| Security Area | Planned Control |
|---------------|-----------------|
| SSH Hardening | Disable root login, enforce key-based authentication, restrict authentication methods |
| Firewall Configuration | Enable host-based firewall, deny all inbound traffic by default, allow SSH only from trusted workstation |
| Mandatory Access Control | Enable and maintain AppArmor in enforcing mode |
| Automatic Updates | Enable unattended security updates |
| User Privilege Management | Use non-root administrative user with sudo access |
| Network Security | Minimise exposed services and restrict open ports |

---

## Threat Model

A preliminary threat model was developed to identify key risks and corresponding mitigation strategies.

| Threat | Description | Mitigation Strategy |
|------|-------------|---------------------|
| Brute-force SSH attacks | Repeated login attempts targeting SSH credentials | Enforce SSH key authentication, disable password login, restrict SSH by IP |
| Privilege escalation abuse | Compromise of a privileged account leading to full system control | Use non-root users, restrict sudo access, log administrative actions |
| Unauthorised network access | Exposure of unnecessary services to the network | Firewall default deny policy, regular port auditing |
| Outdated software vulnerabilities | Exploitation of known vulnerabilities in unpatched software | Automatic security updates and regular patch verification |

---

## Baseline System Observation (Evidence)

### Evidence 1 – User Identity and Privilege Verification

```bash
echo "Verifying active user and privilege level"
whoami
id
sudo -l
```

**Screenshot:** `week2_sudo_privileges.png`  

<img width="1266" height="796" alt="week2_sudo_privileges" src="https://github.com/user-attachments/assets/1e773ec0-24ef-4de2-9a33-3058e7bd85cc" />

---

### Evidence 2 – SSH Service Status Verification

```bash
echo "Checking SSH service status"
sudo systemctl status ssh
```

**Screenshot:** `week2_ssh_status.png`  

<img width="1274" height="797" alt="week2_ssh_status" src="https://github.com/user-attachments/assets/c7bffa3e-579f-447c-b721-e4b91bc54e05" />

---

### Evidence 3 – SSH Configuration Review (Pre-Hardening)

```bash
echo "Reviewing SSH configuration settings"
sudo grep -E "PasswordAuthentication|PermitRootLogin|UsePAM" /etc/ssh/sshd_config
```

**Screenshot:** `week2_ssh_config_review.png`  

<img width="1313" height="848" alt="week2_ssh_config_review" src="https://github.com/user-attachments/assets/e683e876-9085-47ce-8109-0a0aeef0ecc9" />

---

### Evidence 4 – Network Services and Open Ports

```bash
echo "Listing active listening network services"
ss -tuln
```

**Screenshot:** `week2_listening_services.png`  

<img width="1277" height="800" alt="week2_listening_services" src="https://github.com/user-attachments/assets/ec3fbf4b-5ee2-46b6-b0f0-9ad57f1e491e" />

---

### Evidence 5 – Firewall Status (Planning Stage)

```bash
echo "Checking firewall status (pre-enforcement)"
sudo ufw status verbose
```

**Screenshot:** `week2_ufw_status.png`  

<img width="1290" height="809" alt="week2_ufw_status" src="https://github.com/user-attachments/assets/ab7bfb35-013d-4560-ba41-3f076b34052d" />

---

### Evidence 6 – System Update State

```bash
echo "Checking system update status"
apt list --upgradable
```

**Screenshot:** `week2_upgradable_packages.png`  

<img width="1278" height="807" alt="week2_upgradable_packages" src="https://github.com/user-attachments/assets/670523c2-f15c-4135-828b-fd3c0954798d" />


---

## Reflection
Week 2 established a critical planning foundation by defining how performance would be measured and how security controls would be structured and evaluated. Developing a testing methodology, security checklist, and threat model before implementation ensures that later configuration changes can be assessed objectively. This preparation supports accurate performance analysis and informed security decision-making in subsequent weeks.
