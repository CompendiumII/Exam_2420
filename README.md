# Exam_2420

## Updating sofware on Ubuntu OS

```

```


## Fixing code with Vim

First we vim our file...
![Capture](https://user-images.githubusercontent.com/46077062/206573987-7fbcc42d-03dc-4be2-902d-5a0d145362a6.PNG)

Then we can select the part to delet with the v command and use the d command to delete...
![1 2](https://user-images.githubusercontent.com/46077062/206574202-d7c96e82-5f80-4e26-8da8-f1de02b4efab.PNG)

And then we can copy the text that we need to in the command with yt) (copies from cursor until ")" character)...

And then we can paste it in...
![1-4](https://user-images.githubusercontent.com/46077062/206574346-64c9dac1-8345-4fea-9f5a-b285191a99a7.PNG)

We can move to the 0 in the first line and use the r command to replace it with a 0...

We can also use the /V function to find all capital Vs, replace them with r command with C, and then to go to the next appearance we use N...
![1-4](https://user-images.githubusercontent.com/46077062/206574628-21ea6627-59fe-4d9e-a61b-6d8214a52228.PNG)


## Part 3

Looking through the man pages for journalctl, we find current_boot...
![current_boot](https://user-images.githubusercontent.com/46077062/206574772-86664f4c-6ccf-4b98-9020-c156f2f0ddad.PNG)

As well as priority...
![priority](https://user-images.githubusercontent.com/46077062/206574812-cf6f811d-baa0-44dd-a71f-d1597750fdd9.PNG)

And finally json-pretty...
![json-pretty](https://user-images.githubusercontent.com/46077062/206574857-bc7cd50d-aabe-48e7-9e20-115fbfd17a33.PNG)

And we can use the following command to do what is asked of us...
![journalctl-final-command](https://user-images.githubusercontent.com/46077062/206574919-55417301-f321-41e4-9663-19b987d4c091.PNG)

## Part 4

We use the following script to print users and currently logged in user...
```
#!/bin/bash
#: Title       : Find Users
#: Date        : Dec 8 2022
#: Author      : Kevin Xu
#: Version     : Alpha 0.1
#: Description : This script searches for users and currently logged in users
#: Options     : No options
echo "Regular users on the system are:" > /etc/motd
temp=`grep -E 'x:100[1001-5000]+:' /etc/passwd | awk -F: '{print $1" "$3" "$7}' >> /etc/motd`
echo "" >> /etc/motd
echo "Users currently logged in are:" >> /etc/motd
who | awk '{print $1}' >> /etc/motd
```

The following input is visible when run as sudo ./part_4.sh...
![script output](https://user-images.githubusercontent.com/46077062/206575178-ce529783-6ae1-4480-a172-63447d7799cd.PNG)

We can cp this file into /bin/ to run later...

## Part 5

The following service file needs to be created in /etc/systemd/system/...

```
[Unit]
Description=Service to run message of the day

[Service]
Type=simple
User=root
Group=root
ExecStart=/usr/bin/part_4.sh
TimeoutStopSec=5s

[Install]
WantedBy=multi-user.target
```
The service RUNS, but I can't get it to work with sudo...
![service status](https://user-images.githubusercontent.com/46077062/206575586-f2f159e5-1b25-4f31-84e8-b2219ffb08d7.PNG)

