# 🔐 Mini SOC Lab: Brute Force Attack Detection

## ⚙️ Steps Performed (Final – Tested & Working)

---

### 1. Setup Metasploitable2 in VMware
- Downloaded Metasploitable2
- Extracted the zip file
- Opened using VMware (File → Open → Metasploitable.vmx)
- Powered on the machine

---

### 2. Login to Metasploitable
username: msfadmin  
password: msfadmin  

---

### 3. Switch to root user
```bash
sudo su

4. Generate SSH keys (Fix error)
ssh-keygen -A
5. Start SSH service (Working method)
/ect/init.d/ssh start
6. Verify SSH is running
netstat -tulnp | grep 22
7. Get target IP
ip a

Example:
192.168.81.140

8. Switch to Kali Linux
9. Check connectivity
ping -c 4 192.168.81.140
10. Scan SSH port
nmap -p 22 192.168.81.140
11. Create custom password list
echo "msfadmin" > target_pass.txt
12. Perform brute-force attack
hydra -l msfadmin -P target_pass.txt ssh://192.168.81.140 -t 4 -vV
13. Check logs
cat /var/log/auth.log
14. Filter failed attempts
grep "Failed password" /var/log/auth.log
15. Count attempts
grep "Failed password" /var/log/auth.log | wc -l
16. Extract attacker IP
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c

Example Output:
2642 192.168.81.137

Findings
Detected multiple failed login attempts
Identified attacker IP successfully
Observed brute-force attack pattern
🧠 Skills Gained
Log Analysis
Threat Detection
Basic SOC Operations
Linux Command-Line
⚠️ Disclaimer

NOTE: This project was performed in a controlled lab environment for educational purposes only.
