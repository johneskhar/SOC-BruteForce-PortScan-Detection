# SOC Lab Project: Detecting Brute Force & Port Scans with Splunk

## Objective
This project simulates common cyberattacks (SSH brute force & port scans) in a controlled lab environment and detects them using **Splunk SIEM**.  
It demonstrates skills in log collection, threat simulation, detection engineering, and SOC analysis.

## Lab Setup
- **Splunk Enterprise** on Ubuntu VM (log ingestion & SIEM)
- **Splunk Universal Forwarder** to collect system logs
- **Kali Linux VM** to simulate attacks
- Logs collected: `/var/log/auth.log`, `/var/log/ufw.log`

## Lab Architecture
The following diagram shows how the SOC lab environment is structured:
<img width="600" alt="image" src="https://github.com/user-attachments/assets/6ac65b6b-23ce-4b24-a258-4174c49c12bf" />

## Attack Simulations
- **SSH Brute Force** → Hydra
- **Port Scanning** → Nmap

## Detection Queries
- **SSH Brute Force**
  ```spl
  index=main "Failed password"
  | rex "Failed password for (invalid user )?(?<user>\S+) from (?<SRC>\S+)"
  | stats count by SRC, user
  | where count > 5
  ```

- **Port Scan**
  ```spl
  index=main "UFW BLOCK"
  | stats count by SRC, DST
  | where count > 20
  ```
## Results
- ✅ SSH brute force attempts detected in Splunk dashboard
- ✅ Nmap port scans triggered custom alerts

## Future Improvements
- Add more attack simulations (DoS, reverse shell detection, malware)
- Integrate with another SIEM (ELK, Graylog)
- Automate alerting via email/webhook
