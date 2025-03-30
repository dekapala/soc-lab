# SOC-LAB: Suricata IDS in Docker Environment

This project simulates a basic SOC (Security Operations Center) environment using Suricata as an IDS (Intrusion Detection System), deployed with Docker and Infrastructure as Code (IaC) principles via Docker Compose.

## Project Overview

- Deploys Suricata in IDS mode
- Includes a container to simulate HTTP traffic
- Uses a custom Docker network to isolate and monitor activity
- Stores alert logs in EVE JSON format for SOC-style analysis

## Architecture

soc-lab/ ├── docker-compose.yml ├── suricata/ │ ├── suricata.yaml │ └── custom.rules ├── logs/ └── README.md


## Technologies Used

- Docker / Docker Compose
- Suricata IDS
- Alpine Linux
- Custom rule-based detection
- Infrastructure as Code (IaC)

## Limitations on Windows

Due to the networking architecture of Docker Desktop on Windows:

- Suricata cannot fully capture traffic between containers using the default `eth0` interface
- Even using `any` as the listening interface, inter-container traffic may not be visible
- Outbound internet access may not work from Alpine-based containers without DNS resolution and routing
- This setup performs as expected on native Linux or WSL2 with extended network support

## Functional Components

- Suricata launches correctly in IDS mode
- Custom rules load successfully
- Infrastructure is reproducible and modular

## Sample Rule

```text
alert http any any -> any any (msg:"DVWA access detected"; sid:1000003;)
```


Next Steps and Recommendations
Run the same environment on Linux or WSL2 for full network visibility

Integrate EVE JSON output with ELK Stack for visualization

Add more traffic simulation (e.g., nmap, ICMP, vulnerability scans)

Extend with Zeek, Splunk, or Wireshark for deeper analysis

Author
Gabriel Palazzini – github.com/dekapala