
Mini SOC Lab project to simulate and detect brute force attacks using Kali Linux
# 🔐 Mini SOC Lab: Brute Force Attack Detection

## 📌 Project Overview
This project demonstrates how a brute-force attack can be simulated and detected using Kali Linux tools and system log analysis.

---

## 🎯 Objective
- Simulate a brute-force attack using Hydra
- Detect the attack using system logs
- Identify attacker IP and attack patterns

---

## 🛠 Tools Used
- Kali Linux
- Hydra
- SSH
- grep
- awk

---

## ⚙️ Steps Performed

### 1. Started SSH service on target machine
sudo service ssh start

### 2. Performed brute-force attack
hydra -l kali -P /usr/share/wordlists/rockyou.txt ssh://TARGET_IP

### 3. Checked authentication logs
cat /var/log/auth.log

### 4. Filtered failed login attempts
grep "Failed password" /var/log/auth.log

### 5. Counted total attempts
grep "Failed password" /var/log/auth.log | wc -l

### 6. Extracted attacker IP
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c

---

## 📊 Findings
- Multiple failed login attempts detected
- Attacker IP identified successfully
- Clear brute-force attack pattern observed

---

## 🧠 Skills Gained
- Log analysis
- Threat detection
- Basic SOC operations
- Linux command-line usage

## ⚠️ Disclaimer
This project was performed in a controlled lab environment for educational purposes only.
