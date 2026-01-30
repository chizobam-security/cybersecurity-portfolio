# Local cyber security lab set up
## Installing kali linux OS on a VMware
step 1: Go Broadcom support page and create an account
login and click on my downloads  and search for vmware workstation
click on the latest version, for windows, click on the release date, and click on the download arrow
complete the aditional check and wait to be redirected
click on the download arrow again and download it
If you downloaded a pre-configured machine, extract it into permanent folder on your SSD
Open VMware Workstation: On the home screen, click "Open a Virtual Machine", locate your file and open it

### challenge faced
After installing kali linux on vmware workstation pro but my cursor is "stuck" in a transparent state inside kali VM.  when I  Press Ctrl + Alt to release the mouse, it becomes visible but if click again inside the VM, it disappears again. "Accelerate 3D graphics" is unchecked.  I have tried disabling the hardware by adding "KWIN_FORCE_SW_CURSOR=1" to the etc/environment file, that didn't work. I have also tried to reinstall VMware tools using "sudo apt update
sudo apt install --reinstall xserver-xorg-video-vmware open-vm-tools-desktop -y" command but got an error: package "xserver-xorg-video-vmware"  has no installation candidate.
I also tried installing a new kali using ISO file (instead of pre-configured machine) but still the same issue.
This and many other solutions recommended by different chatbot i tried but no success untill I Change Hardware Compatibility on the VMware and upgrade it to 16x.

Installing debian server and installing cowrie honeypot
I download a lightweight Debian 12 "netinst" ISO (amd64) small CDs from the official site https://www.debian.org/distrib/netinst
I create a new VM on the VMware workstation and import the ISO, configured the hardware and start the machine
I used the graphical intsall to install the OS
### challenge faced
My goal is to install cowrie honeypot on my debian server.

I have installed dependencies (sudo apt update && sudo apt install git python3-venv libssl-dev libffi-dev build-essential authbind -y)

Cloned and setup cowrie (git clone http://github.com/cowrie/cowrie 
cd cowrie
python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install --upgrade pip
pip install -r requirements.txt)

Next, I configure cowrie (cp etc/cowrie.cfg.dist etc/cowrie.cfg) 
I now want to  start cowrie(bin/cowrie start) but got an error message: no such file or directory.
I had to Install Cowrie itself into the venv(pip install -e .), verify that cowrie now exist(which cowrie), start it(cowrie  start), then confirm(cowrie status)



