# Brooklyn99 
This room is a typical CTF task, where penetration testing is done against the target to capture the flags. This room particulary is intended for beginners.
The target IP address is 10.10.229.216.

# Scanning and Enumerating
First Scan and Enumerate the target using nmap command-line tool. By saving the output, we can refer to it at a later time.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a455e86e-8f26-43af-a9a9-95c134973fd0)

The output:

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/565bb803-cf78-4326-bcfe-5950aa4c5652)
We can see 3 ports are open, port 21, 22 and 80. 

# Engaging with the target
The ftp service allows anonymous loging as shown below.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a068a4a2-731b-4367-8a9c-31f40070ef14)

After connecting to the target over ftp, there is a file. Let's download it and see its content.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/bd5f0226-8531-4749-aaa2-ac663458d714)

After opening the file, Amy and Jake are possible usernames. In addition, we have learned Jake's password is weak, so we can try to brute-force.
Running hydra against ssh returns Jake's password and we have a successful login.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1136bae8-d3fd-4405-93e1-009bbce10aa3)

# Privilege Escalation
Let's see if we can escalate to root privileges

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/8e1d4d70-5dca-40c4-a0bd-d1574f4a1ddf)

executing "sudo -l" shows Jake can execute /usr/bin/less as a root.

But we are also able to change directory of another user. The user by the name Holt seems interesting. Let's go there.
And we find these file, out of which the last two are interesting.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/839f21ce-312b-4ec7-b614-efb9f3fe53e7)

The access controls show anyone can read user.txt. However, only root can read or write to nano.save.

# USER FLAG

Opening user.txt gives the first flag.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/9ab897be-5345-4432-b899-8a47951af8ff)

# ROOT FLAG

Now, we need root flag. nano.save is owned by the root. Let's open it using - /usr/bin/less - which can be executed with privileges.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/3f99e815-b0a1-4377-b87a-8d76fa31f7a5)

opening the file and not much useful information there. 

But commonly, the root flag is stored in /root. So, we can use /usr/bin/less which can be executed with root privileges to read root.txt

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a26e90c3-0131-4ed1-93c3-8905a159ba29)

# Credits
 Fsociety2006

Thank you for reading.





























