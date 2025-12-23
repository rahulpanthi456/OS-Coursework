
# Week 1 – System Planning and Verification

## 1. Objective
The objective of Week 1 was to deploy a headless Ubuntu Server virtual machine and verify its baseline configuration using command-line tools. This initial setup establishes a stable foundation for secure remote administration, system hardening, monitoring, and performance evaluation in subsequent weeks of the coursework.

---

## 2. System Architecture and Planning
A virtualised server environment was selected to replicate real-world server deployment practices while maintaining isolation from the host operating system. The server was installed using **Ubuntu Server 24.04 LTS** within Oracle VirtualBox and configured without a graphical user interface to reduce resource overhead and minimise the attack surface.

The server was designed to be accessed remotely using SSH, reflecting standard industry practices for Linux server administration.

---

## 3. Installation Summary
Ubuntu Server was installed using the default installation profile with the entire virtual disk allocated to the system and managed using Logical Volume Management (LVM). This approach provides flexibility 
for future disk expansion while maintaining a simple and professional storage layout suitable for a virtualised environment.

Networking was configured using DHCP on a host-only network interface, ensuring secure communication between the server and the workstation while preventing direct exposure to external networks.

---

## 4. System Verification
Following installation, a series of command-line inspection tools were used to verify the system state and confirm successful deployment.

The `uname -a` command was used to validate the running Linux kernel and system architecture. Operating system version details were confirmed using `lsb_release -a`. Memory usage and swap availability were examined with `free -h`, while 
disk usage and mounted filesystems were inspected using `df -h` to confirm correct logical volume configuration.

Network connectivity was verified using `ip addr show`, confirming that the server had been assigned an IPv4 address via DHCP on the primary network interface, enabling secure remote administration.

---

## 5. Evidence
Figure 1 presents the combined output of the system verification commands executed on the Ubuntu Server. These results confirm that the system is operational, correctly configured, and ready for remote access 
and further security configuration.

![System verification commands output](images/week1_system_overview.png)
<img width="1290" height="804" alt="week1_system_information" src="https://github.com/user-attachments/assets/efeb2991-2aa3-459e-be53-3f52660c2f9d" />


---

## 6. Conclusion
Week 1 successfully established a clean and stable Ubuntu Server environment suitable for coursework progression. The system was deployed in a headless configuration, verified using standard Linux command-line tools,
and prepared for secure remote administration. This verified baseline will be used as the foundation for implementing security controls, monitoring solutions, and performance analysis in the following weeks.


