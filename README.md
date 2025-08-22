# SOC Lab Project: Detecting Brute Force & Port Scans with Splunk

## Objective
This project simulates common cyberattacks (SSH brute force & port scans) in a controlled lab environment and detects them using **Splunk SIEM**. It demonstrates skills in log collection, threat simulation, detection engineering, and SOC analysis.

## Lab Setup
- **Splunk Enterprise** on Ubuntu VM (logs ingestion & SIEM)
- **Splunk Universal Forwarder** to collect system logs
- **Kali Linux VM** to simulate attacks
- Logs collected: `/var/log/auth.log`, `/var/log/ufw.log`

## Attacks Simulated
- **SSH Brute Force** → Hydra
- **Port Scanning** → Nmap
