# Cybersecurity Lab Setup: Kali Linux & Cowrie Honeypot
This repository documents the technical setup of a local cybersecurity laboratory environment. The lab consists of an Attacker Machine (Kali Linux) and a Victim/Honeypot Machine (Cowrie on Debian 12), both running on VMware Workstation Pro. It also documents key challenges encountered and how they were resolved.
## 1. Attacker Environment: Kali Linux
### Installation Process
1. **Installing VMware Workstation Pro (Host Setup)**

**Steps**
- Visit the Broadcom Support Portal.
- Create an account and log in.
- Navigate to My Downloads.
- Search for VMware Workstation.
- Select the latest version for Windows.
- Click the release date, complete the additional checks, and download the installer.
- Install VMware Workstation Pro on the host system.

2. **VM Deployment**: Downloaded the pre-configured Kali VMware Image (.7z).
- Extracted the archive to a folder on your system.
- Used the "Open a Virtual Machine" feature in VMware to import the .vmx file.

### Critical Troubleshooting: The "Invisible Cursor" Bug
**Issue**: Upon launching Kali, the cursor became "stuck" in a transparent state. It was visible when "ungrabbed" (Ctrl+Alt) but disappeared immediately upon clicking into the VM.
**Attempted Fixes (Failed):**

- Disabling **Accelerate 3D Graphics**.
- Forcing software cursors via ```etc/environment (KWIN_FORCE_SW_CURSOR=1)```.
- Reinstalling ```open-vm-tools-desktop``` (Failed due to missing ```xserver-xorg-video-vmware``` package candidates).
- Fresh installation via ISO instead of pre-configured image.

**The Solution**: The issue was caused by outdated hardware compatibility in the pre-configured image.
**Fix**: Right-click VM > Manage > Change Hardware Compatibility.

**Action**: Upgraded the compatibility version to 16.x.

**Result**: Cursor visibility and mouse integration were restored immediately.

2. ## Victim Environment: Cowrie Honeypot
**Server Setup**
- OS: Debian 12 "netinst" ISO (amd64).
- Resource Allocation: Configured as a lightweight VM to minimize overhead.
- Installation: Performed a standard Graphical Install.

**Cowrie Installation & Configuration**
1. Dependencies: ```sudo apt update && sudo apt install git python3-venv libssl-dev libffi-dev build-essential authbind -y```
2. Environment Setup:
 ```git clone http://github.com/cowrie/cowrie```
```cd cowrie```
```python3 -m venv cowrie-env```
```source cowrie-env/bin/activate```
```pip install --upgrade pip```
```pip install -r requirements.txt```
3. Configuration: ```cp etc/cowrie.cfg.dist etc/cowrie.cfg```
   






