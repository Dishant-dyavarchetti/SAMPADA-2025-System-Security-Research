# 🛡️  Cyber Security Research – SAMPADA 2025  

## 🔥 Overview  
This repository contains research and scripts developed to detect, mitigate, and counter **cyber threats** posed by adversaries in a **Windows environment**. The focus is on detecting **Initial Access, Persistence, and Privilege Escalation**, as well as implementing **detection mechanisms**.

## 📌 Phases of the Attack  

### **Phase 1: Initial Access 🚀**  
To gain access to the **victim machine**, we search for **vulnerable executables** using **PowerShell scripts**.  
- We identify **.exe files** with valid **authenticated signatures**.  
- A **C++ payload injector** is created that:  
  - Loads **Havoc C2-generated shellcode** into memory.  
  - Allocates the shellcode as **executable memory** and launches the payload.  
- A **shell script** compiles this into a **DLL** using **MinGW32** for easy execution on Windows systems.  
- A **Python script** is then used to:  
  - Load and execute the DLL.  
  - Create a **malicious PowerShell shortcut (LNK file)** to maintain access.

---

### **Phase 2: Persistence ⚡**  
Once **Initial Access** is achieved, the attacker must **survive system restarts and shutdowns**.  
#### **🔹 Scheduled Task Persistence**  
We use **Scheduled Tasks** to ensure the payload runs at every **user login** or **system reboot**:  
- First, **CMD is executed with SYSTEM privileges**.  
- Then, **regsvr32.exe is used to execute the DLL persistently**.

---

### **Phase 3: Privilege Escalation 🔓**  
To elevate privileges to **NT AUTHORITY\SYSTEM**, we identify available **privileges and group memberships**:  
#### **🔹 Exploiting SeImpersonatePrivilege (JuicyPotato & PrintSpoofer)**
- Checking privileges using:
  ```powershell
  whoami /priv

# Phase 4: Final Showdown - Attack Detection PowerShell Script

## Overview
This PowerShell script is designed to detect and verify various suspicious activities on a victim machine that may indicate malicious actions. The script includes multiple functions to detect:

1. **Suspicious Logins**
2. **Persistence Mechanisms**
3. **Agent Communication with Listener via DNS Queries (Havoc)**
4. **Privilege Escalation Attempts**

By running these functions, this script will help identify any attack behaviors performed in **Phase 1** and provide useful insights for further investigation.

---

## Features

### 1. **Detect Suspicious Logins**
The script checks for unusual or unauthorized login activity by:
- Monitoring login attempts
- Analyzing login times
- Cross-checking login sources (IP addresses, hostnames)

### 2. **Identify Persistence Mechanisms**
It detects persistence mechanisms commonly used by attackers to maintain access, such as:
- Startup scripts or registry entries
- Scheduled tasks
- Services or drivers that persist after reboots

### 3. **Agent Communication Detection (Havoc DNS Queries)**
This function scans for unusual DNS query patterns that may indicate an agent is communicating with a remote listener. The script can identify:
- High-frequency DNS queries to suspicious domains
- Queries related to known C2 (Command and Control) servers or tools

### 4. **Privilege Escalation Detection**
The script identifies signs of privilege escalation attempts, such as:
- Modifications to user privileges
- Use of elevated commands
- Unauthorized administrative group additions

---

## Usage

1. Clone this repository or download the script `Attack_Detection.ps1` to your machine.
2. Open PowerShell as an Administrator.
3. Execute the script with the following command:

   ```powershell
   .\Attack_Detection.ps1


---

### **📢 How to Use This README?**
- This file can be uploaded as `README.md` to a **GitHub repository**.
- It provides **clear documentation** for **research, detection, and mitigation**.
- It maintains **professional formatting** with **tables, code blocks, and sections**.

Would you like to add **more details on specific exploits**, or does this cover everything? 🚀
