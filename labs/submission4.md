# Lab 4 submission

## Task 1

I used the equivalent commands for Windows OS:

![4.1](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.1.png?raw=true)

![4.2](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.2.png?raw=true)

![4.3](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.3.png?raw=true)

![4.4](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.4.png?raw=true)

**Boot Performance Analysis:**

Last boot time: the system was last rebooted on February 20 2026, it had been running for 2 days, 20 hours, 24 minutes.

**Process Forensics:**

Top memory consumers:
1. browser
2. explorer
3. Memory Compression
4. MsMpEng

Top CPU consumers:
1. System
2. MsMpEng
3. 2 browser processes
4. dwm (Desktop Window Manager)

The browser processes and MsMpEng are among top both memory and CPU consumers.

**Service Dependencies:**

Workstation Service dependencies:
1. NSI – Running
2. MRxSmb20 – Running
3. Bowser – Running

**User Sessions:**

Logged on users:
1. Local accounts: СИСТЕМА, kuzzm
2. System accounts: LOCAL SERVICE, NETWORK SERVICE
3. Session-related: DWM-2, UMFD-0, UMFD-2
4. Virtual machine account: BE98CEF9...

**Memory Analysis:**

Total Physical Memory: 7.33 GB
Free Physical Memory: 1.5 GB
Total Virtual Memory: 13 GB

## Task 2

![4.5](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.5.png?raw=true)

![4.6](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.6.png?raw=true)

![4.7](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab4.7.png?raw=true)

**Insights on network paths discovered:**

The Test-NetConnection traceroute to github.com reveals a path from the local host (192.168.0.100) through its default gateway (192.168.0.1): the service uses multiple IP addresses.

**Analysis of DNS query/response patterns:**

The packet capture filtered on port 53 shows a DNS query from the local machine (192.168.0.100:59983) to the local DNS server (192.168.0.1:53). The query is for gewl-sclient.spotify.com with a record type of 65. The packet is logged multiple times as it passes through different network components. No response is captured.

**Comparison of reverse lookup results:**

- 8.8.4.4 is a public Google DNS server.
- 1.1.2.2 fails with an error indicating that no PTR record exists.

**Example DNS query:**

- Source: 192.168.0.100:59983
- Destination: 192.168.0.1:53
- Query: Type 65 (HTTPS) for gewl-sclient.spotify.com
- Transaction ID: 44852
