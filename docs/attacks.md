# Attack Simulation

### SSH Brute Force (Hydra)
```bash
hydra -l test -P /usr/share/wordlists/rockyou.txt ssh://<Ubuntu-IP>
```
### Port Scanning (Nmap)
```bash
nmap -sS -p- <Ubuntu-IP>
```
### Network Enumeration / Port Probing
```bash
nmap -A <ubuntu-vm-ip>
```
