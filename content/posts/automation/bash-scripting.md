---
Category:
- Automation
Credits: ''
Reference: ''
Status: Done
createdAt: '2026-07-08T16:25:00.000Z'
title: BASH Scripting
updatedAt: '2026-07-09T16:23:00.000Z'
---


### Getting started with the bash scripting

Run the command to know which shell/script is being used.

```bash
~$ which $SHELL
/usr/bin/zsh
```

Use the “echo” command to display a message, like

```bash
~$ echo "Hello World"
Hello World
```

Create a file, and name it like name.sh. After a file is created, it will be automatically opened. If not then type _nano name.sh_

Start typing the script in the text editor. After you are done, type _Ctrl+X_, _y/Y_ then hit Enter.

```bash
#!/usr/bin/zsh
echo "Hello World"

sleep 3 #uses a delay of 3 seconds before continuing the scipt

echo "3 seconds wait completed"

sleep 1

echo "bye"
```

This script can be executed in two ways

Without privilege escalation

```bash
~# bash name.sh
```

With _chmod +x_

```bash
~# chmod +x name.sh
~# ./name.sh
```

### Using a variable

We can use a variable for purposes like …, well you gotta know that. Else, this is not for you right now, go back to building drag-n-drop code blocks.

We are using a variable _name_, and called it using _$name_ wherever we want.

```bash
#!/usr/bin/zsh

name="you"

echo "$name waking up..."
sleep 3
echo "GM, $name"
sleep 3
echo "howdy, $name"
sleep 3
echo "best day, $name!"
```

Another way to use variables, after receiving inputs from the user.

```bash
#!/usr/bin/zsh

echo "What is your name?"
read name

echo "$name waking up..."
sleep 3
echo "GM, $name"
sleep 3
echo "howdy, $name"
sleep 3
echo "best day, $name!"
```

One more way too use the variables, this time while initiating the script. This will take in _arguments_ while executing the script.

```bash
#!/usr/bin/zsh

user=$1
compliments=$2

echo "$name waking up..."
sleep 3
echo "GM, $name"
sleep 3
echo "howdy, $name"
sleep 3
echo "You are the best $compliments, $name!"

#Execute the above script by typing

~# ./name.sh KB hooman

where KB is first, and hooman is second argument
```

Realtime parameters like _whoami, date, pwd_

```bash
#!/usr/bin/zsh

user=$(whoami)
date=$(date)
path=$(pwd)

echo "Good morning, $name"
echo "Today's date is $date. You are on the path $path"
```

Script to create a folder, a shell, and enter text in it.

```bash
#!/usr/bin/zsh

mkdir SHUBHAM
cd SHUBHAM
touch note.txt
echo "FLAGGGSSSS---successful" > note.txt
```

Above script modified to get inputs from the user.

```bash
!/usr/bin/zsh

echo "Enter a folder name: "
read -p folder
sleep 0.5
echo "Enter a file name: "
read -p file
sleep 0.5
echo "Enter the secret message to put in the text file: "
read -sp text
sleep 0.5

#-p enables to input on the same line
#-s does not show the text while typing like sudo password
echo "creating a folder with the name $folder, and a file $file in it with the secret text>

mkdir $folder
cd $folder
touch $file.txt
echo $text > $file.txt
sleep 3
echo "Operation is completed successfully!"
echo "ending the script..."
sleep 2
```

### Using Arrays in shell

We can use arrays to extract a specific value from a given string. Just like python, the starting value is 0.

```bash
#!/usr/bin/zsh

echo "Enter Names: "
read -a names

echo "Names : ${names[0]}, ${names[1]}"
echo "The second name is: ${names[1]}"
```

### Using the $REPLY

$REPLY reads and immediately extracts the current value in the buffer (built-in variable, reply).

> 💡 Good for conserving space in the memory

```bash
#!/usr/bin/zsh

echo "Enter Names: "
read
echo "Name is: $REPLY"
```

### Using args=()

```bash
#!/usr/bin/zsh

echo $0 $1 $2 '> echo $1 $2 $3'
# $0 reads the script name

args=("$@") #takes input as array

echo ${args[0]}, ${args[1]}
```

## Basic Math

```bash
~$ expr 30 -10
```

```bash
#!/usr/bin/zsh

mynum1 = 100
mynum2 = 80

echo $mynum1

expr $mynum1 + 50
expr $mynum1 + $mynum2

#dont use echo before expr
```

```bash
#!/usr/bin/zsh

mynum=200

if [ $mynum -eq 200 ]
then
	echo "The condition is true"
else
	echo "The variable does not equal 200."
fi

# -ne not equals
# -gt greater than
# -lt less than
# -f checks for files


```

```bash
#!/usr/bin/zsh

command = /usr/bin/htop

iif [ -f $command ]
then
	echo "$command is available, now executing it..."
	sleep 3
else
	echo "$command is NOT available, installing it..."
	sleep 1
	sudo apt update && sudo apt install -y htop
fi

$command
```

## Exercise 2

- [x] script name - “day.sh”
- [x] greet w/ 3 messages
  - [x] GM
  - [x] howdy
  - [x] best
- [x] Executable
