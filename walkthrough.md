# SOC Lab Demonstration

## 1. Lab Architecture  
This diagram shows the flow of logs in the SOC lab setup. Logs are collected from the Ubuntu VM by the Splunk Universal Forwarder and ingested into Splunk Enterprise. Attacks are simulated from Kali Linux.  

(<img width="600" alt="image" src="https://github.com/user-attachments/assets/e5b04649-4185-4101-bc3a-793c5e4a9e37"/>

---

## 2. Splunk Dashboards  

### SSH / Brute Force Dashboard  
This dashboard visualizes authentication logs from `/var/log/auth.log`. It highlights failed and successful SSH login attempts and is useful to detect brute force patterns.  

<img width="800"  alt="redacted-image (1)" src="https://github.com/user-attachments/assets/7bb2318b-5d00-415e-8c58-8f0ddc1ba2f3"/>


### Network Activity Dashboard  
This dashboard visualizes firewall logs from `/var/log/ufw.log`. It helps identify port scans and abnormal network activity.  

<img width="800" alt="redacted-image" src="https://github.com/user-attachments/assets/c5be44eb-9832-49a7-947c-6a408410597e"/>


---

## 3. Attack Simulations  

### Hydra Brute Force Attack  
Hydra was used from Kali Linux to attempt multiple SSH logins on the Ubuntu VM. This generates repeated failed login attempts visible in Splunk.  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/582ecc1f-15cc-4102-93fb-a36b57479dcb"/>

### Nmap Port Scan  
Nmap was used from Kali Linux to scan open ports on the Ubuntu VM. This activity generates UFW logs, showing repeated connection attempts across many ports.  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/3b22333b-0e79-45a7-9f36-359a797cda91"/>

---

## 4. Detection & Alerts  

### Brute Force Alert  
This alert detects repeated failed SSH login attempts from the same source IP within a short time frame, indicating a brute force attack.  

**Splunk Query:**  
```spl
index=main "Failed password" 
| rex "Failed password for (invalid user )?(?<user>\S+) from (?<SRC>\S+)" 
| stats count by SRC user 
| where count > 5
```
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/68eade5a-bd4e-4c94-b851-54dac9c830af"/>

### Port Scan Alert  
This alert identifies potential port scanning activity by detecting multiple unique destination ports accessed by the same source IP in a short time. 

**Splunk Query:**  
```spl
index=main SRC=* DST=* 
| stats dc(DST_PORT) as unique_ports by SRC 
| where unique_ports > 10
```
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/ecbbb238-47fb-46b1-918a-797ae21301d0"/>


