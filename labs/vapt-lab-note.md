# Vulnerability Assessment & Penetration Testing Lab
## Project Overview
This project demonstrates a full-cycle vulnerability management process, including environment setup, automated scanning, manual exploitation, and remediation.

### Tools Used:

**Kali Linux**: Primary attacking OS.

**Docker**: To host the Damn Vulnerable Web App (DVWA).

**OpenVAS (GVM)**: For automated vulnerability scanning.

**Metasploit Framework**: For validating and exploiting found vulnerabilities.

### Lab Setup & Configurations
1. Target Environment (DVWA)
To ensure a clean and repeatable environment, I deployed DVWA using Docker:

Update your Machine ```sudo apt update && sudo apt upgrade -y```
Install Docker ```sudo apt install docker.io -y```
Run DVWA:```sudo docker run --rm -it -p 80:80 vulnerables/web-dvwa```
Access DVWA in Browser: Open browser and type ```http://localhost``` and login with ```admin/password```

**After logging in**:

Click **Setup / Reset DB** in the left menu

Scroll down

Click **Create / Reset Database**

Once you see **Database has been created**, DVWA is ready


