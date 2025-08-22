# Detection Queries (SPL)

### Brute Force Detection
index=main "Failed password"
| rex "Failed password for (invalid user )?(?<user>\S+) from (?<SRC>\S+)"
| stats count by SRC, user
| where count > 5

### Port Scan Detection
index=main "UFW BLOCK"
| stats count by SRC, DST
| where count > 20

### DoS Detection
index=main "UFW BLOCK"
| stats count by SRC, DST
| where count > 100
