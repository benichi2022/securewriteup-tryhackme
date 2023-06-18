# This is a walkthrough for the Tryhackme room - Vulnversity
# Description : Learn about active recon, web app attacks and privilege escalation.
# It is part of offensive pentesting learning path
# Link to the task
https://tryhackme.com/room/vulnversity

I will use tryhackme's attackbox instead of using vpn on my Kali VM.
Target IP : 10.10.203.84

# Task 1: (Optional) - Connect using openvpn

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/4102a99f-9c2a-4213-9784-359b8e752cc1)

# Task 2: Reconnaissance
nmap -sV -A -p- --open 10.10.203.84 
Explanation for using the flags can be found in the following images.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/59a51042-af48-4b96-9f7d-1315d8f5c3c3)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a08d5f23-fdd1-4e31-8c6d-aa14a0e7436a)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1e945acf-042b-4244-b159-8e521ea8e4bd)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/955a7cd6-7465-46ae-92a5-787509021e2c)

Sample Scan: Here, nmap is scanning all the ports.  

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/04b844c0-27ed-4201-98b3-cd552a445ad1)

# Task 3: Locating directories using Gobuster

We saw that a webserver is running on port 3333. Let's use gobuster to further discover hidden directories and files.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1f22b6c5-503f-4993-b3f5-6fa45281a909)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/0f9b0d60-8aa4-4c9b-be50-9cfa18e907a2)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/228319eb-7630-4b42-9854-96bdab0a8830)

Gobuster returns the following result.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5707db36-9ab8-49a1-8716-0981fd3d18d3)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b65d5b5e-223d-4899-af35-ed173ecfe29d)

and we confirm /internal is an upload page.

# Task 4 : Compromise the Webserver

Here, we will upload a php script that will send us a reverse shell and ultimately gain an interactive command line. However, as a defense mechanism, webserver do not allow to upload a php file. So, let's find out which extensions are acceptable. We will use burpsuite intruder for automated attacks. Use the following link to set up burpsuite: https://tryhackme.com/module/learn-burp-suite and since I am using tryhackme attackbox, I just need to turn on the foxyproxy.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/70ea0617-4e21-4880-8c42-534a28c934fe)

To intercept traffic, so we can send to the intruder for customization.
Like I said, the server does not allows php files to be uploaded

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/650d2560-b1df-401a-99a1-9545411c3090)

We need a way to bypass this restriction. Let's make a list of potential plausible file extensions.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e67e8c98-5be0-4d29-bdd2-2c27116afe32)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/34516e20-58ca-47e0-983c-014c42e2fd80)

The request is intercepted. We need to send it to intruder.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c9cabded-e7a2-4c02-955a-51471e4be2bd)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b86ecc69-89b3-4eda-9ba1-52706502fc14)

Add the list of potential acceptable extensions and deselect the "URL-encode", otherwise it will not work. After starting the attack, we get the following result.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/7a3e16dc-11ce-4791-9beb-90199895afe5)

The odd one among the rest is usually the answer we need. Hence, phtml is the extension we need to use.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c527f39c-0628-4310-838f-2fcbba16ef4b)

Now that we knows, phtml is allowed. We upload a reverse shell file with such extension. The script can be downloaded from this link : https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php

But let's first copy the file to a new one with phtml extension and edit it to reflect our IP and port our machine is listening on. Let's also set up a netcat lisener, that awaits incoming connection.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d68bd958-a058-4483-8670-2485554fe6f5)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/aa5e0084-ed69-4121-bd7d-1901e3424b05)

Better to keep the port number low to disguise it as a normal traffic.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a6a694b6-0743-4662-90e4-7da3f17f25d5)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/08ced893-9f13-46d8-92bc-34d49150cdc5)

After triggering the execution of the "phtml" file, we successfully got a reverse shell. We also stabilized it.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/7851cd5a-b466-4f7f-a630-ee09cd7d5948)

Changing to the home directory, we see there is only one user and we find the user.txt flag in bill's home directory.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d414da99-9387-4d34-b241-bcc14ceccbae)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/7b14fe10-4567-406a-b71e-688e12272cc5)

# Task 5 : Privilege Escalation

Now we need to escalate privilege. One suggested way is as follows. 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d463ed37-a10f-472d-856e-39c199b63cc6)

Let's execute find command to discover all files with SUID bit set and owned by the root.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b894b8d2-f79c-43f4-aba5-6f2e3d9492b3)

/bin/systemctl stands out because the systemctl command manages both system and service configurations, enabling administrators to manage the OS and control the status of services. Further, systemctl is useful for troubleshooting and basic performance tuning.

By standing on the shoulder of gaints, let's seek help from gtfobins on how to escalate using /bin/systemctl with a SUID bit set. And here are the results.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/82dcb99a-5d0d-4de8-bf38-8e3d67886599)

All these series of steps aim to read a file that we don't have permission to read. In our case, we don't have the privilege to read /root/root.txt i.e our final flag. Instead of " id > /tmp/output ", we will execute "cat /root/root.txt > /tmp/root.txt"

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b423a424-a9e3-4024-afd0-6eb36b07042e)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/4fa9178d-2f94-4997-80d8-2cb507942fbc)

And with that, we are done with room.

Credits: 
        https://tryhackme.com/p/tryhackme
        https://tryhackme.com/p/1337rce




