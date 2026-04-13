# Tcpdump Lab Notes

## Context

This lab focused on using tcpdump as a low level packet capture tool from the Linux command line. Unlike tshark, tcpdump forces interaction at a more raw level, requiring precise filtering and interpretation of traffic.

---

## Key Observations

### 1. SSH Traffic Behaviour

- Continuous TCP packets exchanged over port 22
- Payload not readable due to encryption
- Frequent small packets (~36 bytes) indicate interactive session (keystrokes)

Insight:
SSH hides application data but still exposes communication patterns.

---

### 2. TCP Flow Characteristics

- Repeated pattern:
  - PSH, ACK → data sent
  - ACK → acknowledgement
- Large bursts of data followed by acknowledgements

Insight:
TCP guarantees delivery through acknowledgements and sequencing.

---

### 3. Importance of `-nn`

- Without `-nn`:
  - Hostnames and services are resolved (e.g. fedora.ssh)
- With `-nn`:
  - Raw IPs and ports are shown

Insight:
Numeric output removes ambiguity and speeds up analysis.

---

### 4. Filtering Power

Examples used:

- `tcp port 22` → isolate SSH
- `icmp` → isolate ping traffic
- `src host` → isolate traffic origin

Insight:
Filtering is the difference between noise and signal.

---

### 5. Packet Size Patterns

- Small packets (~36 bytes): interactive traffic
- Large packets (>1000 bytes): bulk data transfer

Insight:
Packet size gives clues about behaviour even when encrypted.

---

## Operational Takeaways

- Packet capture allows validation of real traffic not assumptions
- Encryption hides content but not behaviour
- tcpdump is lightweight and effective for remote troubleshooting
- Filtering is essential for isolating meaningful data

---

## Strategic Value

Understanding packet level traffic provides:

- Visibility into network behaviour
- Ability to troubleshoot connectivity issues
- Detection of abnormal traffic patterns
- Foundation for security analysis

This moves from tool usage into protocol awareness.