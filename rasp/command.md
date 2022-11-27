# Raspberry Pi Basic Command

- Update Raspberry OS (Don't use it with your umbrel)
~~~
sudo apt-get update 
sudo apt-get upgrade
~~~
- Access Raspberry Pi Configuration (Don't use it with your umbrel)
~~~
sudo raspi-config
~~~
- Network Configuration Details
~~~
ifconfig
~~~
- Restart Your Raspberry Pi
~~~
sudo reboot
~~~
- Power Off Raspberry Pi
~~~
sudo shutdown -h now
~~~
- List Files and Directories
~~~
ls
~~~
- Find a File
~~~
find / -name filename
~~~
- Check Current Directory
~~~
pwd
~~~
- Download a File
~~~
wget URL
~~~
- Install a Program
~~~
sudo apt-get install programname
~~~
- Run a Script
~~~
chmod a+x filename.sh
./filename.sh
~~~
- Elevated Permission
~~~
sudo su
~~~
- Change File Ownership
~~~
sudo chown pi:root filename
~~~
- Extract Files
~~~
unzip filename
~~~
- Extract TAR Files
~~~
tar -cvzf filename.tar.gz
~~~
Remove a Package
~~~
sudo apt-get remove packagename
~~~
- Scan the Local Network
~~~
sudo apt-get install nmap
nmap -sn 192.168.1.0/24
~~~
- Find the IP Address of Raspberry Pi
~~~
hostname -I
~~~
- View Background Tasks
~~~
htop
~~~
- Check Raspberry OS Version
~~~
cat /proc/version
~~~
- Check Hardware Information
~~~
lscpu
cat /proc/meminfo
cat /proc/partitions
~~~
