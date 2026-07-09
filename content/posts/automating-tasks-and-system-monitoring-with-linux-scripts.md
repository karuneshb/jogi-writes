---
createdAt: "2026-07-08T18:33:00.000Z"
updatedAt: "2026-07-09T06:48:00.000Z"
Status: "Done"
Reference: ""
Credits: ""
title: "Automating Tasks and System Monitoring with Linux Scripts"
---

---

# Script 1: Task Automation

Source Code:

```bash
#!/bin/bash

user=$(whoami)
#Takes the name of the current user for greeting
echo "Hi, $user"
echo "this is a system updater script..."
sleep 0.5
sudo apt-get update

echo "checking for updates done successfully"
sleep 0.5
sudo apt-get upgrade -y

echo "updates installed successfully"
```

Problem Solved: Automates updates to the system to save time.

Rationale: Manually entering the commands is time taking. This script helps with that. Prospectively, this could be executed right after the user is logged in to the system.

Screenshots:

![image.png](/images/image.png)

![image.png](/images/image.png)

---

# Script 2: System Status

Source Code:

```bash
#!/bin/bash

echo "Welcome! this script shows system usage..."
sleep 1

#CPU usage
echo -e "\nCPU usage:"
top -bn1 | grep "Cpu(s)" | awk '{print $2 "% user, " $4 "% system, " $8 "% idle"}'

#Memory usage
echo -e "\nMemory usage:"
free -h | grep "Mem" | awk '{print "Total: " $2 ", Used: " $3 ", Free: " $4}'

# Disk Space
echo -e "\nDisk Space:"
df -h | grep -v tmpfs

# Network Statistics
echo -e "\nNetwork Statistics:"
ifconfig | grep "RX packets" -A 1

```

Problem solved: Gives a quick overview of the system status and performance

Rationale: Easy monitoring and troubleshooting the system in case of any lags or crashes that may occur while testing or deploying an application.

Screenshot:

![image.png](/images/image.png)

---

# Script 3: Software Installer

Source Code:

```bash
#!/bin/bash

echo "Automatically installing Nginx server now..."

#Checks for updating the package list
sudo apt-get update

#Installs nginx server without asking for confirmation (y/N)
sudo apt-get install nginx -y

#Troubleshooting error/verifying installation
if [ $? -eq 0 ]; then
    echo "Nginx is installed successfully"
    echo "Starting the nginx server..."
    sudo systemctl start nginx
    sudo systemctl enable nginx
    echo "Nginx initiated successfully!"

else
    echo "Installation of nginx failed"
    exit 1
fi

sudo systemctl status nginx
```

Problem solved: This script simplifies the installation of the nginx server

Rationale: This script can be used to quickly install nginx in any ubuntu system (batch installations) or any application/server as a matter of fact can be installed by modifying this script.

Screenshot:

![image.png](/images/image.png)

---

This report was drafted on Notion ([www.notion.so](https://www.notion.so/))
