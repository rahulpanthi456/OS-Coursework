# Week 6 – Performance Evaluation and Analysis

## Overview
This week focused on evaluating the performance of the Linux server under different workload conditions. Unlike earlier weeks that emphasised security hardening, monitoring, and auditing, this phase concentrated on analysing how system resources behave during normal operation and under stress. The objective was to measure CPU usage, memory consumption, disk I/O activity, network performance, system latency, and service response times. These measurements were used to identify bottlenecks and to assess the effectiveness of optimisation actions using quantitative evidence.

---

## Testing Methodology
Performance testing was conducted using a structured four-stage methodology. Baseline testing was first performed to establish normal system behaviour in an idle state. Load testing was then carried out using stress-generation tools to simulate high CPU and memory demand. The results of baseline and load testing were compared to identify performance bottlenecks. Finally, optimisation actions were applied and post-optimisation testing was conducted to evaluate improvements using before-and-after measurements.

---

## Tools Used
The following tools were used to collect and analyse performance data:
- `top` and `htop` for CPU and memory utilisation
- `free -h` for detailed memory statistics
- `iostat` for disk I/O performance
- `df -h` for disk usage
- `ping` for network latency
- `stress-ng` for CPU and memory load testing

---

## Baseline Performance Results
Baseline measurements were captured while the system was idle with no artificial workload applied. These results represent the system’s normal operating state and serve as a reference point for comparison.

**Evidence – Baseline CPU and Memory Usage**

<img width="1294" height="813" alt="week6_baseline_top" src="https://github.com/user-attachments/assets/0a7ba8bc-12ef-40ef-b6e5-95aab7d282c0" />

---

**Evidence – Baseline Memory Statistics**
<img width="1294" height="807" alt="week6_baseline_free" src="https://github.com/user-attachments/assets/6aab5c0d-6780-465c-ae25-479aaa3c6b76" />

---

**Evidence – Baseline Disk I/O**

<img width="1293" height="821" alt="week6_baseline_iostat" src="https://github.com/user-attachments/assets/50cf223d-f17e-4406-b1d4-9ca3caaa91e9" />

---

### Baseline Performance Data

| Metric | Result |
|------|-------|
| CPU usage | Low, mostly idle |
| Memory usage | Stable with sufficient free memory |
| Disk I/O | Minimal activity |
| Network latency | Low and consistent |
| Service response time | Immediate |

---

## Load Testing and Stress Results
To evaluate performance under pressure, CPU and memory stress was generated using `stress-ng`. The workload was sustained for a fixed duration while system metrics were monitored.

**Evidence – CPU Usage Under Load**
<img width="1315" height="855" alt="week6_cpu_load" src="https://github.com/user-attachments/assets/ca5f15d2-86aa-46e1-b62f-7b1096c46dc0" />

---

**Evidence – Memory Usage Under Load**
<img width="1779" height="999" alt="week6_memory_load" src="https://github.com/user-attachments/assets/92f67950-cc71-4cd8-9cbc-50d2cc5a6a54" />

---

### Load Test Observations
During load testing, CPU utilisation increased significantly across available cores. Memory consumption rose steadily, and moderate disk I/O activity was observed due to background processes. Network latency increased slightly, and SSH response times showed minor delays, although the system remained stable and responsive.

### Load Performance Data

| Metric | Result |
|------|-------|
| CPU usage | High under load |
| Memory usage | Increased significantly |
| Disk I/O | Moderate increase |
| Network latency | Slight increase |
| Service response time | Minor delay |

---

## Bottleneck Identification
By comparing baseline and load testing results, CPU utilisation was identified as the primary bottleneck during stress conditions. Memory usage also increased notably, indicating potential pressure under sustained workloads. Disk I/O and network performance remained within acceptable limits and did not present critical constraints.

---

## Optimisation Actions
Two optimisation actions were implemented to improve system performance:

1. **Reduced Background Services**  
   Non-essential services were disabled to free CPU and memory resources.

2. **Adjusted System Swappiness**  
   The Linux swappiness value was reduced to limit excessive swapping and improve memory efficiency during high load.

**Evidence – Swappiness Configuration (Before and After)**

<img width="1290" height="812" alt="week6_swappiness_before" src="https://github.com/user-attachments/assets/9efe0f9e-8bc4-4e35-8c38-9f6b0b584372" />

---

<img width="1290" height="810" alt="week6_swappiness_after" src="https://github.com/user-attachments/assets/815c9b7b-70fc-4c73-a4b6-9fd2bffce830" />

---

## Post-Optimisation Performance Results
After applying the optimisation actions, performance testing was repeated under similar load conditions.

**Evidence – Post-Optimisation Memory Behaviour**

<img width="1463" height="972" alt="week6_post_optimisation" src="https://github.com/user-attachments/assets/95d5bb22-47d6-4b10-b330-9144ae52171a" />

---

### Post-Optimisation Observations
CPU usage remained high during stress testing but stabilised more quickly after load completion. Memory usage showed improved efficiency with reduced swapping behaviour. System responsiveness improved, and SSH response times were more consistent compared to pre-optimisation results.

### Before and After Comparison

| Metric | Before Optimisation | After Optimisation |
|------|-------------------|------------------|
| CPU recovery time | Slower | Faster |
| Memory efficiency | Moderate | Improved |
| System responsiveness | Slight delay | Improved |
| Service response time | Minor delay | Near-immediate |

---

## Network Performance Analysis
Network performance was analysed using ICMP latency testing. Ping results showed low latency during baseline testing and only a minor increase during load testing. No packet loss was observed, indicating stable network throughput and reliability.

**Evidence – Network Latency Test**

<img width="1282" height="811" alt="week6_ping" src="https://github.com/user-attachments/assets/02e4dac1-ad92-40e1-ace2-160bcd9608f0" />


---

## Reflection
This week highlighted the importance of evaluating system performance alongside security controls. While previous weeks focused on prevention and monitoring, performance analysis provided insight into how the system behaves under stress and where improvements can be made. Identifying CPU and memory bottlenecks and applying targeted optimisations improved system stability and responsiveness. This phase reinforced the need for continuous performance evaluation as part of effective system administration.
