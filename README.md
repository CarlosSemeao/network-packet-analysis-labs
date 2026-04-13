# Network Packet Analysis Labs

## Objective

This repository documents two short hands on labs built to strengthen my practical understanding of network traffic analysis using packet capture.

---

## Lab 1: SSH Traffic Analysis

### Scenario

Captured SSH traffic between macOS and a Fedora Linux VM.

### What I observed

- TCP connection established over port 22
- Continuous encrypted SSH packets
- No readable application data due to encryption

### Evidence

![SSH Analysis](screenshots/ssh-analysis.png)

![HTTP Analysis](screenshots/http-analysis.png)

---

## Lab 2: HTTP Traffic Analysis

### Scenario

Captured HTTP traffic from a local Python web server.

### What I observed

- Readable HTTP requests:
  - GET / HTTP/1.1
- Server responses:
  - 200 OK
  - 404 Not Found (favicon)
- Full visibility of application layer data

### Evidence

See screenshots folder:
- http-analysis.png

---

## Key Insight

- SSH traffic is encrypted and not readable at packet level
- HTTP traffic exposes readable requests and responses
- Packet capture allows direct validation of network behaviour

---

## Tools Used

- tshark (Wireshark CLI)
- Fedora Linux
- macOS
- OpenSSH
- Python HTTP server

---

## Lab 3: Tcpdump Packet Capture and Filtering

### Scenario

This lab focused on using `tcpdump` from the Linux command line to capture, read, filter, and inspect packet data without relying on a graphical interface.

The goal was to strengthen practical understanding of how network traffic can be observed directly from the terminal and filtered efficiently by interface, host, port, protocol, and TCP flags.

### Objective

- Capture network traffic from a selected interface
- Save packet captures to `.pcap` files
- Read packet captures from file
- Apply practical filters to isolate specific traffic
- Inspect packets in numeric, ASCII, and hexadecimal formats
- Understand how `tcpdump` supports troubleshooting and protocol analysis from the command line

### Concepts Practised

- Interface selection with `-i`
- Writing captures to file with `-w`
- Reading captures from file with `-r`
- Limiting packet count with `-c`
- Disabling name resolution with `-n` and `-nn`
- Filtering by host, source host, destination host
- Filtering by port, source port, destination port
- Filtering by protocol such as ICMP, TCP, and UDP
- Combining conditions with `and`, `or`, and `not`
- Filtering TCP flags such as RST
- Displaying packets in brief, ASCII, hexadecimal, and hex + ASCII formats

### Commands Practised

#### Basic capture on an interface

```bash
tcpdump -i ens5

---

## Conclusion

These labs demonstrate practical packet-level visibility of real network communication using both `tshark` and `tcpdump`.

Across SSH, HTTP, and command line packet filtering, the main lesson was clear: packet capture removes guesswork. It allows traffic to be validated directly, whether the goal is to confirm encrypted communication, inspect readable application data or isolate protocol behaviour using precise filters.

This work strengthened my understanding of Linux networking, troubleshooting, and packet analysis in a practical way.