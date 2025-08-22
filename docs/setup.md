# Lab Setup Instructions

## Requirements
- VirtualBox or VMware
- Ubuntu VM (Splunk server)
- Kali Linux VM (attacker)

## Steps
1. Install Splunk Enterprise on Ubuntu  
2. Install Splunk Universal Forwarder  
3. Configure forwarder to monitor:
   - `/var/log/auth.log` (SSH activity)
   - `/var/log/ufw.log` (firewall activity)
4. Start Splunk service and log into UI
5. Create indexes and verify logs are ingested
