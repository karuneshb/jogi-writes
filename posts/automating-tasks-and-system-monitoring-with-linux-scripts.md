---
createdAt: "2026-07-08T18:33:00.000Z"
updatedAt: "2026-07-08T18:34:00.000Z"
Status: "Done"
Credits and Reference: ""
Dave Prowse: ""
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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/ece2c03e-2c2f-4779-950b-c6d8a160b5f5/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4666G2QYXPK%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T040951Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIBPu7OOxtldpIo91FKgG8XpvFe%2FAF1V2D%2F7H4pgsY8r9AiEA1ug5o7vJ7bRXFdgnL4zElVtZJtC24dPmcYp4OLbtjp0qiAQIlf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDNxcUG8%2BcdXNtct0dircA15jMejKYhBj2kAOoXn5liortallZLSebXDrMiv0MIfXNLeEcT2UWPvV9yi0SG3F6easWT07maSN5Zy7y7YFsirJnXpJNPSNez%2Bnf6sWsti4ug3zv86DqrCG52jtj4MHo%2Bihwi%2BJjwtPWi62szFKYTc%2FkjL5eWc%2BFylJRH%2FphCZK%2FuOtW85HnUu7apH7gt9R4XfYz47yIU965LAcf2xa1zMmDxP10k51Qxks4aXy4D1W5Z1bZ9Kal6dFiIu34oPOXQhXoGdzinsDloKagBAHB0cf%2FkuDjMLmvqqSmvO7X0IaaeJjyoiPFZ4RzeY4rt9%2BvgO86aaa1pYYlA19p5Rysx4BAHo7y81vscpPU2NzCIrPAQkGGHgCQHIB%2FcKMb0fnymvwXyetPT9cBil47fkWU4HF5rtpd9%2FKDaajaXPIXAIGArXR%2FtIlBSt7xO4hpt4ZHfISI4t1LugqJWyzn%2BpCNO18tKjz7GnuESw8hevuzefeWN%2FZc%2FYx5kz7GtTpDzSN7EbDFMHoK5BaZEX%2F4uijOe17WXoRMkadEl7WRlNy6lWij2e4Rau5MpI1NGYgb0dooieeiCdmdtLFbePTOcNY8ubUrb%2F95kOTzqaA%2Fm0%2BSffBYK%2BvW6NANbZiXN4NMKC2vNIGOqUBhDIpJ8l0ErIk63FrjtTbW1YqF8khzdax6GCvwWGRTpaMMrwmMZ3q23L27Kbeh%2FZKWShytFyKgs6y%2FDoSu5VhmY%2Fa16iOHNUYnQ0HkPyeI1HcpKEfmRdDfMt%2FPcnBZDA4onjYBEciEWKBNd13eS4QJ%2BUQYzHAGSluRJWjE2A5k2R4FCXgZzIc0KB6xUca5ZoC%2FIGf3eJ7he68mVsjITqHOLMrH%2FOE&X-Amz-Signature=792b3f34dba9faf9351e10310005fe0349f58a202bd12c5408f449d23108902b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/2709997c-3eac-45e3-8347-5fd5266a1a56/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4666G2QYXPK%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T040951Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIBPu7OOxtldpIo91FKgG8XpvFe%2FAF1V2D%2F7H4pgsY8r9AiEA1ug5o7vJ7bRXFdgnL4zElVtZJtC24dPmcYp4OLbtjp0qiAQIlf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDNxcUG8%2BcdXNtct0dircA15jMejKYhBj2kAOoXn5liortallZLSebXDrMiv0MIfXNLeEcT2UWPvV9yi0SG3F6easWT07maSN5Zy7y7YFsirJnXpJNPSNez%2Bnf6sWsti4ug3zv86DqrCG52jtj4MHo%2Bihwi%2BJjwtPWi62szFKYTc%2FkjL5eWc%2BFylJRH%2FphCZK%2FuOtW85HnUu7apH7gt9R4XfYz47yIU965LAcf2xa1zMmDxP10k51Qxks4aXy4D1W5Z1bZ9Kal6dFiIu34oPOXQhXoGdzinsDloKagBAHB0cf%2FkuDjMLmvqqSmvO7X0IaaeJjyoiPFZ4RzeY4rt9%2BvgO86aaa1pYYlA19p5Rysx4BAHo7y81vscpPU2NzCIrPAQkGGHgCQHIB%2FcKMb0fnymvwXyetPT9cBil47fkWU4HF5rtpd9%2FKDaajaXPIXAIGArXR%2FtIlBSt7xO4hpt4ZHfISI4t1LugqJWyzn%2BpCNO18tKjz7GnuESw8hevuzefeWN%2FZc%2FYx5kz7GtTpDzSN7EbDFMHoK5BaZEX%2F4uijOe17WXoRMkadEl7WRlNy6lWij2e4Rau5MpI1NGYgb0dooieeiCdmdtLFbePTOcNY8ubUrb%2F95kOTzqaA%2Fm0%2BSffBYK%2BvW6NANbZiXN4NMKC2vNIGOqUBhDIpJ8l0ErIk63FrjtTbW1YqF8khzdax6GCvwWGRTpaMMrwmMZ3q23L27Kbeh%2FZKWShytFyKgs6y%2FDoSu5VhmY%2Fa16iOHNUYnQ0HkPyeI1HcpKEfmRdDfMt%2FPcnBZDA4onjYBEciEWKBNd13eS4QJ%2BUQYzHAGSluRJWjE2A5k2R4FCXgZzIc0KB6xUca5ZoC%2FIGf3eJ7he68mVsjITqHOLMrH%2FOE&X-Amz-Signature=f9cb63df9aee7c19ad9af1b28092cef1e3cc838c1e930d520ebb587c403478c3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/f512098e-7060-445c-9d77-5b23434bb1f0/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4666G2QYXPK%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T040951Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIBPu7OOxtldpIo91FKgG8XpvFe%2FAF1V2D%2F7H4pgsY8r9AiEA1ug5o7vJ7bRXFdgnL4zElVtZJtC24dPmcYp4OLbtjp0qiAQIlf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDNxcUG8%2BcdXNtct0dircA15jMejKYhBj2kAOoXn5liortallZLSebXDrMiv0MIfXNLeEcT2UWPvV9yi0SG3F6easWT07maSN5Zy7y7YFsirJnXpJNPSNez%2Bnf6sWsti4ug3zv86DqrCG52jtj4MHo%2Bihwi%2BJjwtPWi62szFKYTc%2FkjL5eWc%2BFylJRH%2FphCZK%2FuOtW85HnUu7apH7gt9R4XfYz47yIU965LAcf2xa1zMmDxP10k51Qxks4aXy4D1W5Z1bZ9Kal6dFiIu34oPOXQhXoGdzinsDloKagBAHB0cf%2FkuDjMLmvqqSmvO7X0IaaeJjyoiPFZ4RzeY4rt9%2BvgO86aaa1pYYlA19p5Rysx4BAHo7y81vscpPU2NzCIrPAQkGGHgCQHIB%2FcKMb0fnymvwXyetPT9cBil47fkWU4HF5rtpd9%2FKDaajaXPIXAIGArXR%2FtIlBSt7xO4hpt4ZHfISI4t1LugqJWyzn%2BpCNO18tKjz7GnuESw8hevuzefeWN%2FZc%2FYx5kz7GtTpDzSN7EbDFMHoK5BaZEX%2F4uijOe17WXoRMkadEl7WRlNy6lWij2e4Rau5MpI1NGYgb0dooieeiCdmdtLFbePTOcNY8ubUrb%2F95kOTzqaA%2Fm0%2BSffBYK%2BvW6NANbZiXN4NMKC2vNIGOqUBhDIpJ8l0ErIk63FrjtTbW1YqF8khzdax6GCvwWGRTpaMMrwmMZ3q23L27Kbeh%2FZKWShytFyKgs6y%2FDoSu5VhmY%2Fa16iOHNUYnQ0HkPyeI1HcpKEfmRdDfMt%2FPcnBZDA4onjYBEciEWKBNd13eS4QJ%2BUQYzHAGSluRJWjE2A5k2R4FCXgZzIc0KB6xUca5ZoC%2FIGf3eJ7he68mVsjITqHOLMrH%2FOE&X-Amz-Signature=eeef8a88e383ba1e69534b066649ba73fd784a98f8bb4aa8b419d116a7d93229&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/24891e17-216e-4ccb-8bf8-c1e427a1af8d/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4666G2QYXPK%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T040951Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIBPu7OOxtldpIo91FKgG8XpvFe%2FAF1V2D%2F7H4pgsY8r9AiEA1ug5o7vJ7bRXFdgnL4zElVtZJtC24dPmcYp4OLbtjp0qiAQIlf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDNxcUG8%2BcdXNtct0dircA15jMejKYhBj2kAOoXn5liortallZLSebXDrMiv0MIfXNLeEcT2UWPvV9yi0SG3F6easWT07maSN5Zy7y7YFsirJnXpJNPSNez%2Bnf6sWsti4ug3zv86DqrCG52jtj4MHo%2Bihwi%2BJjwtPWi62szFKYTc%2FkjL5eWc%2BFylJRH%2FphCZK%2FuOtW85HnUu7apH7gt9R4XfYz47yIU965LAcf2xa1zMmDxP10k51Qxks4aXy4D1W5Z1bZ9Kal6dFiIu34oPOXQhXoGdzinsDloKagBAHB0cf%2FkuDjMLmvqqSmvO7X0IaaeJjyoiPFZ4RzeY4rt9%2BvgO86aaa1pYYlA19p5Rysx4BAHo7y81vscpPU2NzCIrPAQkGGHgCQHIB%2FcKMb0fnymvwXyetPT9cBil47fkWU4HF5rtpd9%2FKDaajaXPIXAIGArXR%2FtIlBSt7xO4hpt4ZHfISI4t1LugqJWyzn%2BpCNO18tKjz7GnuESw8hevuzefeWN%2FZc%2FYx5kz7GtTpDzSN7EbDFMHoK5BaZEX%2F4uijOe17WXoRMkadEl7WRlNy6lWij2e4Rau5MpI1NGYgb0dooieeiCdmdtLFbePTOcNY8ubUrb%2F95kOTzqaA%2Fm0%2BSffBYK%2BvW6NANbZiXN4NMKC2vNIGOqUBhDIpJ8l0ErIk63FrjtTbW1YqF8khzdax6GCvwWGRTpaMMrwmMZ3q23L27Kbeh%2FZKWShytFyKgs6y%2FDoSu5VhmY%2Fa16iOHNUYnQ0HkPyeI1HcpKEfmRdDfMt%2FPcnBZDA4onjYBEciEWKBNd13eS4QJ%2BUQYzHAGSluRJWjE2A5k2R4FCXgZzIc0KB6xUca5ZoC%2FIGf3eJ7he68mVsjITqHOLMrH%2FOE&X-Amz-Signature=147cba577f98577a7d01c30094a84e29cb7ee511b0ef6e0565279367ce87a608&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

---

This report was drafted on Notion ([www.notion.so](https://www.notion.so/))
