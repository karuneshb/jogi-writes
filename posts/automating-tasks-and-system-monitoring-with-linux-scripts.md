---
createdAt: "2026-07-08T18:33:00.000Z"
updatedAt: "2026-07-08T18:34:00.000Z"
Status: "Done"
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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/ece2c03e-2c2f-4779-950b-c6d8a160b5f5/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SZBTFDEC%2F20260708%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260708T164200Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMD%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIQCB3qquT2w5UzbVJMxdqezxZEMFdfxXS%2BAYne7lSZdGlQIgT9DrmlEFxhxcUrGydLUWpCJKCGEoDvpfIydk5M5cC2gqiAQIiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDLHcz3JxM7Exsg7ZhircAzC%2FuxPhaqlC1cGKkf8BVOEPkneAEdD4rTU%2BG72JPET46LXxWkLEh2IEEHh5hE%2F6%2FaOTTl5uMUzICwP7Y3Qw2ob1plGXDJZb6VgRLDqMy2Vxs6fzrxh9GXQjr6IF42nZ7sgNZ6W571F%2BYX%2BhfU4FpmBKQIcTN41ODEVMV4jnEIgYC1Db9o6bVWvObSzuoWLpkHIFylO%2Fvsn7a2AEojS3hxQ84bK%2BJA8cwx5W7fADZchvuIVdLT%2Fko0af9iE7Y1Ao85KR%2FeCG84%2FnYQlGo5Vc8NRXfjAUC32220z6Q0EwR6w5s8%2BG%2BkjOk30t%2BMwq%2BlljC0cJSk2sM2BTIpU4%2B%2BFgkscKqxEE63d5d36fFAl94hSsK1Kqau2SOux58MX9%2FuNGD%2B7gfMvNbeRIHKFqwWDfEXvkw4MhuAHaAAU08vwTuGlfqT5JLg3u1HPhNnRn3Ztp54SxSP9jsFlO2Uk1nXz4c8XwZfTF7cMAxXCKhSjrkBQ%2BO8Gc9m1PWMWTTaiqhovEX%2BR6GhZP5KJhwTkGsijyD6s0AZXfbQLclgT3q4kg1XpxvqOyPe3ZXcS%2BO8NMlxzCnx%2BrR96GyOenuelYe2W2Rb8SLwB5rVjPJUMeAZP8B0Hwk%2BBOwN7nhbgNLAaIMIDcudIGOqUB5vAHx6K5gkbLie3R8ImSrJ2RK6Fwvz6TSaqNLHhU9yv%2F2%2FwfrFbBUNxcQ7NgMK%2FFaw93RQR%2Fnqgm4H6f%2FbaL9WuyERP32p8aHbjLiJ4DolWONYhgbRzIdGIdD21UAPZN0G2bCSOPv5%2FeKIzcCxACLCFb3ZQI4WVWHSlnZEokd8XKrPsC2oAYKMI6dwQJ53O19K84QVhqKYcCrBfmqen1pigkNIRq&X-Amz-Signature=e734d1ab51903c8cba68d26d11f37b51b773f6f093536c846b2c06b23f499b63&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/2709997c-3eac-45e3-8347-5fd5266a1a56/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SZBTFDEC%2F20260708%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260708T164200Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMD%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIQCB3qquT2w5UzbVJMxdqezxZEMFdfxXS%2BAYne7lSZdGlQIgT9DrmlEFxhxcUrGydLUWpCJKCGEoDvpfIydk5M5cC2gqiAQIiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDLHcz3JxM7Exsg7ZhircAzC%2FuxPhaqlC1cGKkf8BVOEPkneAEdD4rTU%2BG72JPET46LXxWkLEh2IEEHh5hE%2F6%2FaOTTl5uMUzICwP7Y3Qw2ob1plGXDJZb6VgRLDqMy2Vxs6fzrxh9GXQjr6IF42nZ7sgNZ6W571F%2BYX%2BhfU4FpmBKQIcTN41ODEVMV4jnEIgYC1Db9o6bVWvObSzuoWLpkHIFylO%2Fvsn7a2AEojS3hxQ84bK%2BJA8cwx5W7fADZchvuIVdLT%2Fko0af9iE7Y1Ao85KR%2FeCG84%2FnYQlGo5Vc8NRXfjAUC32220z6Q0EwR6w5s8%2BG%2BkjOk30t%2BMwq%2BlljC0cJSk2sM2BTIpU4%2B%2BFgkscKqxEE63d5d36fFAl94hSsK1Kqau2SOux58MX9%2FuNGD%2B7gfMvNbeRIHKFqwWDfEXvkw4MhuAHaAAU08vwTuGlfqT5JLg3u1HPhNnRn3Ztp54SxSP9jsFlO2Uk1nXz4c8XwZfTF7cMAxXCKhSjrkBQ%2BO8Gc9m1PWMWTTaiqhovEX%2BR6GhZP5KJhwTkGsijyD6s0AZXfbQLclgT3q4kg1XpxvqOyPe3ZXcS%2BO8NMlxzCnx%2BrR96GyOenuelYe2W2Rb8SLwB5rVjPJUMeAZP8B0Hwk%2BBOwN7nhbgNLAaIMIDcudIGOqUB5vAHx6K5gkbLie3R8ImSrJ2RK6Fwvz6TSaqNLHhU9yv%2F2%2FwfrFbBUNxcQ7NgMK%2FFaw93RQR%2Fnqgm4H6f%2FbaL9WuyERP32p8aHbjLiJ4DolWONYhgbRzIdGIdD21UAPZN0G2bCSOPv5%2FeKIzcCxACLCFb3ZQI4WVWHSlnZEokd8XKrPsC2oAYKMI6dwQJ53O19K84QVhqKYcCrBfmqen1pigkNIRq&X-Amz-Signature=b8bf68785313ce458a4ae78e58fade286eead9f6c1356ba83642d7b5849f658a&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/f512098e-7060-445c-9d77-5b23434bb1f0/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SZBTFDEC%2F20260708%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260708T164200Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMD%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIQCB3qquT2w5UzbVJMxdqezxZEMFdfxXS%2BAYne7lSZdGlQIgT9DrmlEFxhxcUrGydLUWpCJKCGEoDvpfIydk5M5cC2gqiAQIiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDLHcz3JxM7Exsg7ZhircAzC%2FuxPhaqlC1cGKkf8BVOEPkneAEdD4rTU%2BG72JPET46LXxWkLEh2IEEHh5hE%2F6%2FaOTTl5uMUzICwP7Y3Qw2ob1plGXDJZb6VgRLDqMy2Vxs6fzrxh9GXQjr6IF42nZ7sgNZ6W571F%2BYX%2BhfU4FpmBKQIcTN41ODEVMV4jnEIgYC1Db9o6bVWvObSzuoWLpkHIFylO%2Fvsn7a2AEojS3hxQ84bK%2BJA8cwx5W7fADZchvuIVdLT%2Fko0af9iE7Y1Ao85KR%2FeCG84%2FnYQlGo5Vc8NRXfjAUC32220z6Q0EwR6w5s8%2BG%2BkjOk30t%2BMwq%2BlljC0cJSk2sM2BTIpU4%2B%2BFgkscKqxEE63d5d36fFAl94hSsK1Kqau2SOux58MX9%2FuNGD%2B7gfMvNbeRIHKFqwWDfEXvkw4MhuAHaAAU08vwTuGlfqT5JLg3u1HPhNnRn3Ztp54SxSP9jsFlO2Uk1nXz4c8XwZfTF7cMAxXCKhSjrkBQ%2BO8Gc9m1PWMWTTaiqhovEX%2BR6GhZP5KJhwTkGsijyD6s0AZXfbQLclgT3q4kg1XpxvqOyPe3ZXcS%2BO8NMlxzCnx%2BrR96GyOenuelYe2W2Rb8SLwB5rVjPJUMeAZP8B0Hwk%2BBOwN7nhbgNLAaIMIDcudIGOqUB5vAHx6K5gkbLie3R8ImSrJ2RK6Fwvz6TSaqNLHhU9yv%2F2%2FwfrFbBUNxcQ7NgMK%2FFaw93RQR%2Fnqgm4H6f%2FbaL9WuyERP32p8aHbjLiJ4DolWONYhgbRzIdGIdD21UAPZN0G2bCSOPv5%2FeKIzcCxACLCFb3ZQI4WVWHSlnZEokd8XKrPsC2oAYKMI6dwQJ53O19K84QVhqKYcCrBfmqen1pigkNIRq&X-Amz-Signature=dd3913c8be2da2226df8afe03bfe74161a827309e6b5f29c804504ddf119bb03&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/24891e17-216e-4ccb-8bf8-c1e427a1af8d/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SZBTFDEC%2F20260708%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260708T164200Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMD%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCIQCB3qquT2w5UzbVJMxdqezxZEMFdfxXS%2BAYne7lSZdGlQIgT9DrmlEFxhxcUrGydLUWpCJKCGEoDvpfIydk5M5cC2gqiAQIiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgw2Mzc0MjMxODM4MDUiDLHcz3JxM7Exsg7ZhircAzC%2FuxPhaqlC1cGKkf8BVOEPkneAEdD4rTU%2BG72JPET46LXxWkLEh2IEEHh5hE%2F6%2FaOTTl5uMUzICwP7Y3Qw2ob1plGXDJZb6VgRLDqMy2Vxs6fzrxh9GXQjr6IF42nZ7sgNZ6W571F%2BYX%2BhfU4FpmBKQIcTN41ODEVMV4jnEIgYC1Db9o6bVWvObSzuoWLpkHIFylO%2Fvsn7a2AEojS3hxQ84bK%2BJA8cwx5W7fADZchvuIVdLT%2Fko0af9iE7Y1Ao85KR%2FeCG84%2FnYQlGo5Vc8NRXfjAUC32220z6Q0EwR6w5s8%2BG%2BkjOk30t%2BMwq%2BlljC0cJSk2sM2BTIpU4%2B%2BFgkscKqxEE63d5d36fFAl94hSsK1Kqau2SOux58MX9%2FuNGD%2B7gfMvNbeRIHKFqwWDfEXvkw4MhuAHaAAU08vwTuGlfqT5JLg3u1HPhNnRn3Ztp54SxSP9jsFlO2Uk1nXz4c8XwZfTF7cMAxXCKhSjrkBQ%2BO8Gc9m1PWMWTTaiqhovEX%2BR6GhZP5KJhwTkGsijyD6s0AZXfbQLclgT3q4kg1XpxvqOyPe3ZXcS%2BO8NMlxzCnx%2BrR96GyOenuelYe2W2Rb8SLwB5rVjPJUMeAZP8B0Hwk%2BBOwN7nhbgNLAaIMIDcudIGOqUB5vAHx6K5gkbLie3R8ImSrJ2RK6Fwvz6TSaqNLHhU9yv%2F2%2FwfrFbBUNxcQ7NgMK%2FFaw93RQR%2Fnqgm4H6f%2FbaL9WuyERP32p8aHbjLiJ4DolWONYhgbRzIdGIdD21UAPZN0G2bCSOPv5%2FeKIzcCxACLCFb3ZQI4WVWHSlnZEokd8XKrPsC2oAYKMI6dwQJ53O19K84QVhqKYcCrBfmqen1pigkNIRq&X-Amz-Signature=299545317fc66e5ad14d22d7614a1978e587aa332b19589bced61da582b7b4a4&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

---

This report was drafted on Notion ([www.notion.so](https://www.notion.so/))
