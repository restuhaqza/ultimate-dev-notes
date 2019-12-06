# Hands on SNORT as Logger for ICMP Protocol

Roadmap using SNORT

Prequesites: 
- [x] Machine
- [x] OS (Ubuntu 16.04)
- [x] Network
- [x] IDS


How to be ....
```
[...Install Ubuntu 16.04]

#Install SNORT
sudo apt install snort

#Open access root
sudo su

#check snort as services application
service --status-all | grep snort

#edit file config
nano /etc/snort/rules/local.rules

#add this line detection ICMP protocol (in this case for detection DDOS attack)
alert icmp any any -> 45.77.33.25 any (msg: "Seseorang melakukan ping ke server"; sid: 1000001;)

#kill process SNORT
killall snort

#using local config
snort -c /etc/snort/rules/local.rules -l /var/log/snort/ -K ascii -D

#watch log
watch -n 2 tail /var/log/snort/alert
```
