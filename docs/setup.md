# Lab Setup Instructions

## Requirements
- VirtualBox or VMware
- Ubuntu VM (Splunk server)
- Kali Linux VM (attacker)

## Steps
1. Install Splunk Enterprise on Ubuntu
2. Install Splunk Universal Forwarder
3. Configure forwarder to monitor:
   - /var/log/auth.log (SSH activity)
   - /var/log/ufw.log (firewall activity)
4. Start Splunk service and log into UI
   - Splunk Web: http://<ubuntu-vm-ip>:8000
5. Configure networking so Kali can reach Ubuntu
   - Find Ubuntu VM IP using `ip a`
6. Enable UFW and logging on Ubuntu
   - `sudo ufw enable && sudo ufw logging on`
7. Create Splunk indexes and verify logs are ingested
