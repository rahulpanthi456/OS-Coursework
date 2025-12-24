# Week 3 – Application Selection for Performance Testing

## Overview
Week 3 focused on selecting appropriate applications for performance evaluation in later phases of the coursework. The objective was to identify applications that represent different workload types so that CPU, memory, disk I/O, and network behaviour can be meaningfully analysed under controlled conditions. This planning stage ensures that performance testing conducted in subsequent weeks is structured, repeatable, and aligned with realistic server usage scenarios.

## Application Selection Matrix

| Application        | Workload Type        | Primary Resource | Justification |
|--------------------|----------------------|------------------|---------------|
| stress-ng          | CPU-intensive        | CPU              | Selected to generate controlled CPU load, enabling analysis of processor utilisation, scheduling behaviour, and system responsiveness under stress. |
| stress-ng          | Memory-intensive     | RAM              | Used to apply memory pressure and observe RAM usage, caching behaviour, and potential swap activity. |
| fio                | I/O-intensive        | Disk I/O         | Chosen to benchmark disk read/write performance and identify I/O bottlenecks and latency issues. |
| iperf3             | Network-intensive    | Network          | Used to generate network traffic and measure bandwidth, throughput, and latency between systems. |
| openssh-server     | Server application   | CPU, Network     | Represents a real-world server service, providing a baseline workload during normal remote administration. |

## Installation Documentation (SSH-Based)

All applications were installed remotely via SSH in compliance with the administrative constraint.

### Update Package Index
```bash
sudo apt update
```
**Screenshot: week3_apt_update.png**

<img width="1284" height="799" alt="week3_apt_update" src="https://github.com/user-attachments/assets/78a08bda-1973-4cb6-a17e-be706b728667" />

---

### Install CPU and Memory Stress Tool
```bash
sudo apt install stress-ng -y
```
**Screenshot: week3_stressng_install.png**

<img width="1267" height="794" alt="week3_stressng_install" src="https://github.com/user-attachments/assets/64241f14-7417-4e1f-b5d3-1fc467d890be" />

---

### Install Disk I/O Benchmark Tool
```bash
sudo apt install fio -y
```
**Screenshot: week3_fio_install.png**

<img width="1281" height="800" alt="week3_fio_install" src="https://github.com/user-attachments/assets/62d2f054-07eb-4acd-b935-663eba8b5de9" />

---

### Install Network Performance Tool
```bash
sudo apt install iperf3 -y
```
**Screenshot: week3_iperf3_install.png**

<img width="1279" height="802" alt="week3_iperf3_install" src="https://github.com/user-attachments/assets/27f5fc44-6f82-4457-98d7-8996b68e7ea1" />

<img width="1285" height="794" alt="week3_iperf3_verify" src="https://github.com/user-attachments/assets/9d08d388-c0d4-4a7b-ad24-9b0e17dbc71f" />

---

### Verify SSH Server Availability
```bash
sudo systemctl status ssh
```
**Screenshot: week3_ssh_status.png**

<img width="1275" height="797" alt="week3_ssh_status" src="https://github.com/user-attachments/assets/74802f28-d5d0-4e33-abbc-97aae80d077c" />

---

## Expected Resource Profiles

### stress-ng (CPU-intensive)
High CPU utilisation across one or more cores with minimal memory, disk, and network usage. This workload is suitable for identifying CPU saturation and scheduling effects.

### stress-ng (Memory-intensive)
Increased RAM consumption with possible swap activity under constrained memory conditions. This workload supports analysis of memory pressure and memory management behaviour.

### fio (Disk I/O-intensive)
High disk read/write throughput with increased I/O wait times under load. This workload enables identification of disk performance bottlenecks and latency limitations.

### iperf3 (Network-intensive)
High network bandwidth usage during testing with increased packet transmission and reception. This workload allows measurement of throughput and latency.

### OpenSSH Server
Low to moderate CPU usage with continuous network activity during administrative sessions. This represents a realistic baseline server workload.

## Monitoring Strategy

The following monitoring tools will be used during later performance testing phases:
CPU usage will be monitored using top and htop.  
Memory usage will be observed using free -h and vmstat.  
Disk I/O performance will be measured using iostat and iotop.  
Network performance will be evaluated using iperf3 and ping.  
System responsiveness will be assessed using load averages and command execution times.

Metrics will be captured during baseline testing, load testing, and post-optimisation to enable direct comparison and identification of performance bottlenecks.

## Reflection
This week established a structured foundation for performance testing by selecting applications that generate diverse system workloads. Defining expected behaviour and monitoring strategies in advance ensures that future performance evaluations are consistent, measurable, and meaningful. This preparation supports effective analysis and optimisation in later stages of the coursework.
