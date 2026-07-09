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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/ece2c03e-2c2f-4779-950b-c6d8a160b5f5/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4664KDPMU64%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T150624Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjENf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIGz8zlKtIufoOX2Xo91rZjF9EM%2B3mhkITFAyYykPqwMhAiAhr6yqKqX7xfMKwaw6Lr2KmOYoGCXmbpmpMAlEp9iJwSqIBAig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMWM8InGzBH37GDCP4KtwDZul7rA3iBq%2Fd9znXP%2BQWt3SrqXRU9dHbYUwctuA4MOB0mRl76nJSqP3FtN3zkOzbVltgV8Ei6cOieuipnXGecPrArqGiTcwp7whJZ7Ux0sZ4qLcI2d%2BwX4rIXJXbTIOCzha8rhsBL%2FDOmyn27mhU9zo2Hd4UOxfAR%2BEossSNld6SBo1xo0yue24MID%2BqW10UyfdAc%2Baazp0CyvLsmegPff6sJJhkC4Exk7FeaFo6M1KtlmuL7wBbfJfhzcRC%2FH2JWsCqGKyQswi3U6y1chHIHJqMoqPvtDyXJ%2FB6%2Bp85cK3nC%2B1U828ZRdd9OfTna3stG05jE4ioaoGHFu%2F0tTNeW4JlKP%2BgZ%2B9MK%2FV5khAme699klggFsyEjZU1yLoMNvambhSS8V9JqzDC1%2FlD0yRe8kqjx99bvF70WSBXZABegmIcmwIn6Vk5S0ZPwf8BZYFcBI2HmYXBT0B0e%2BE%2BgLjKgezduEWCtxcM%2BczknkqO%2FTskxaFTSCP0FEgmxL8m7jaTPP1Ap%2BUe7r%2F8%2BDW7ykiIxMnMJ%2FIPTc6mcGWx7MUKJ%2FwHRv%2Fh9gvcTHeWZNDoj2bfxBe4GKD9V9cBt6wPpX%2B9JpSfJ1jyqpiWA0Kk0asIlLleKUeQBw69uEnrW7EwxOy%2B0gY6pgE4hsRQgZqCmLyhzFdEcSAYyq%2BmLlR1BnMhkqgCom1lZVFzqh0h8%2FhPrTdNqrf4Y65Fhuzy7lUioIu63gUnTK21v%2BjlKiwbpkjUgx3BtqDwjO%2BHkVdl7UJGKQIrZ99pKrt%2BlsxnTOZ7Qt9Z9K0fvgMHspCvQXV2z2Ifvq5tNnIYD5T6SmGdnGld5bMhwvnRVF0pUNphZMHXnCA28HUEINz9iRAhilp9&X-Amz-Signature=7d1b24ea8c6c1efde69d13001a647cb4a5b4df4daee749b8ec787cfc66209ec3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/2709997c-3eac-45e3-8347-5fd5266a1a56/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4664KDPMU64%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T150624Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjENf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIGz8zlKtIufoOX2Xo91rZjF9EM%2B3mhkITFAyYykPqwMhAiAhr6yqKqX7xfMKwaw6Lr2KmOYoGCXmbpmpMAlEp9iJwSqIBAig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMWM8InGzBH37GDCP4KtwDZul7rA3iBq%2Fd9znXP%2BQWt3SrqXRU9dHbYUwctuA4MOB0mRl76nJSqP3FtN3zkOzbVltgV8Ei6cOieuipnXGecPrArqGiTcwp7whJZ7Ux0sZ4qLcI2d%2BwX4rIXJXbTIOCzha8rhsBL%2FDOmyn27mhU9zo2Hd4UOxfAR%2BEossSNld6SBo1xo0yue24MID%2BqW10UyfdAc%2Baazp0CyvLsmegPff6sJJhkC4Exk7FeaFo6M1KtlmuL7wBbfJfhzcRC%2FH2JWsCqGKyQswi3U6y1chHIHJqMoqPvtDyXJ%2FB6%2Bp85cK3nC%2B1U828ZRdd9OfTna3stG05jE4ioaoGHFu%2F0tTNeW4JlKP%2BgZ%2B9MK%2FV5khAme699klggFsyEjZU1yLoMNvambhSS8V9JqzDC1%2FlD0yRe8kqjx99bvF70WSBXZABegmIcmwIn6Vk5S0ZPwf8BZYFcBI2HmYXBT0B0e%2BE%2BgLjKgezduEWCtxcM%2BczknkqO%2FTskxaFTSCP0FEgmxL8m7jaTPP1Ap%2BUe7r%2F8%2BDW7ykiIxMnMJ%2FIPTc6mcGWx7MUKJ%2FwHRv%2Fh9gvcTHeWZNDoj2bfxBe4GKD9V9cBt6wPpX%2B9JpSfJ1jyqpiWA0Kk0asIlLleKUeQBw69uEnrW7EwxOy%2B0gY6pgE4hsRQgZqCmLyhzFdEcSAYyq%2BmLlR1BnMhkqgCom1lZVFzqh0h8%2FhPrTdNqrf4Y65Fhuzy7lUioIu63gUnTK21v%2BjlKiwbpkjUgx3BtqDwjO%2BHkVdl7UJGKQIrZ99pKrt%2BlsxnTOZ7Qt9Z9K0fvgMHspCvQXV2z2Ifvq5tNnIYD5T6SmGdnGld5bMhwvnRVF0pUNphZMHXnCA28HUEINz9iRAhilp9&X-Amz-Signature=10ab80ab377ad004179584094d3afc3ba82476982e1e6dc4470be8a2c6d9de18&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/f512098e-7060-445c-9d77-5b23434bb1f0/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4664KDPMU64%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T150624Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjENf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIGz8zlKtIufoOX2Xo91rZjF9EM%2B3mhkITFAyYykPqwMhAiAhr6yqKqX7xfMKwaw6Lr2KmOYoGCXmbpmpMAlEp9iJwSqIBAig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMWM8InGzBH37GDCP4KtwDZul7rA3iBq%2Fd9znXP%2BQWt3SrqXRU9dHbYUwctuA4MOB0mRl76nJSqP3FtN3zkOzbVltgV8Ei6cOieuipnXGecPrArqGiTcwp7whJZ7Ux0sZ4qLcI2d%2BwX4rIXJXbTIOCzha8rhsBL%2FDOmyn27mhU9zo2Hd4UOxfAR%2BEossSNld6SBo1xo0yue24MID%2BqW10UyfdAc%2Baazp0CyvLsmegPff6sJJhkC4Exk7FeaFo6M1KtlmuL7wBbfJfhzcRC%2FH2JWsCqGKyQswi3U6y1chHIHJqMoqPvtDyXJ%2FB6%2Bp85cK3nC%2B1U828ZRdd9OfTna3stG05jE4ioaoGHFu%2F0tTNeW4JlKP%2BgZ%2B9MK%2FV5khAme699klggFsyEjZU1yLoMNvambhSS8V9JqzDC1%2FlD0yRe8kqjx99bvF70WSBXZABegmIcmwIn6Vk5S0ZPwf8BZYFcBI2HmYXBT0B0e%2BE%2BgLjKgezduEWCtxcM%2BczknkqO%2FTskxaFTSCP0FEgmxL8m7jaTPP1Ap%2BUe7r%2F8%2BDW7ykiIxMnMJ%2FIPTc6mcGWx7MUKJ%2FwHRv%2Fh9gvcTHeWZNDoj2bfxBe4GKD9V9cBt6wPpX%2B9JpSfJ1jyqpiWA0Kk0asIlLleKUeQBw69uEnrW7EwxOy%2B0gY6pgE4hsRQgZqCmLyhzFdEcSAYyq%2BmLlR1BnMhkqgCom1lZVFzqh0h8%2FhPrTdNqrf4Y65Fhuzy7lUioIu63gUnTK21v%2BjlKiwbpkjUgx3BtqDwjO%2BHkVdl7UJGKQIrZ99pKrt%2BlsxnTOZ7Qt9Z9K0fvgMHspCvQXV2z2Ifvq5tNnIYD5T6SmGdnGld5bMhwvnRVF0pUNphZMHXnCA28HUEINz9iRAhilp9&X-Amz-Signature=49a46815b04ec19516a920046631b5f3021b155d99892b4a549173ab1bef4138&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/394de64d-f353-4006-bc0a-9eeeddb852db/24891e17-216e-4ccb-8bf8-c1e427a1af8d/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB4664KDPMU64%2F20260709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20260709T150624Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjENf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIGz8zlKtIufoOX2Xo91rZjF9EM%2B3mhkITFAyYykPqwMhAiAhr6yqKqX7xfMKwaw6Lr2KmOYoGCXmbpmpMAlEp9iJwSqIBAig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMWM8InGzBH37GDCP4KtwDZul7rA3iBq%2Fd9znXP%2BQWt3SrqXRU9dHbYUwctuA4MOB0mRl76nJSqP3FtN3zkOzbVltgV8Ei6cOieuipnXGecPrArqGiTcwp7whJZ7Ux0sZ4qLcI2d%2BwX4rIXJXbTIOCzha8rhsBL%2FDOmyn27mhU9zo2Hd4UOxfAR%2BEossSNld6SBo1xo0yue24MID%2BqW10UyfdAc%2Baazp0CyvLsmegPff6sJJhkC4Exk7FeaFo6M1KtlmuL7wBbfJfhzcRC%2FH2JWsCqGKyQswi3U6y1chHIHJqMoqPvtDyXJ%2FB6%2Bp85cK3nC%2B1U828ZRdd9OfTna3stG05jE4ioaoGHFu%2F0tTNeW4JlKP%2BgZ%2B9MK%2FV5khAme699klggFsyEjZU1yLoMNvambhSS8V9JqzDC1%2FlD0yRe8kqjx99bvF70WSBXZABegmIcmwIn6Vk5S0ZPwf8BZYFcBI2HmYXBT0B0e%2BE%2BgLjKgezduEWCtxcM%2BczknkqO%2FTskxaFTSCP0FEgmxL8m7jaTPP1Ap%2BUe7r%2F8%2BDW7ykiIxMnMJ%2FIPTc6mcGWx7MUKJ%2FwHRv%2Fh9gvcTHeWZNDoj2bfxBe4GKD9V9cBt6wPpX%2B9JpSfJ1jyqpiWA0Kk0asIlLleKUeQBw69uEnrW7EwxOy%2B0gY6pgE4hsRQgZqCmLyhzFdEcSAYyq%2BmLlR1BnMhkqgCom1lZVFzqh0h8%2FhPrTdNqrf4Y65Fhuzy7lUioIu63gUnTK21v%2BjlKiwbpkjUgx3BtqDwjO%2BHkVdl7UJGKQIrZ99pKrt%2BlsxnTOZ7Qt9Z9K0fvgMHspCvQXV2z2Ifvq5tNnIYD5T6SmGdnGld5bMhwvnRVF0pUNphZMHXnCA28HUEINz9iRAhilp9&X-Amz-Signature=0c4bb17c4e8322f21310b0770410280bb8b88d542481eb8b4c20037464070ae5&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

---

This report was drafted on Notion ([www.notion.so](https://www.notion.so/))
