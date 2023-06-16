# IDE
# Description - Capture The Flag - An Easy Box To Polish Your Enumeration Skills
# Link to Tryhackme Room
https://tryhackme.com/room/ide

target IP: 10.10.226.120

As always, let's start with scanning the host and enumerating services.

# Reconnaissance

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/cd658c99-67c9-421f-a71c-a9ff2a7ca34e)

There are 4 ports open. And right off the bat, we see that the FTP server allows anonymous login.

# Gaining Access/Foothold

Let's try to login to the FTP server as anonymous

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/dfa602a6-b695-4efc-9834-7d7eddb57d4d)

Upon successful login, we found a file. Let's have a look at its contents.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e4a48a0f-8107-4dde-8a3e-b8abb9d57e8e)

We can infer possible credentials: username - john and default password - password.
Let's turn our attentions to the webservers.
Remote Denial of Service is not the type of attack we want to capture the flags as it would interrupt the availability.
Let's turn our attention to the two http services on port 80 and 62337.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e4e68a2d-d7fc-4a2a-b315-a1ae8c512d2d)

These associated exploits of httpd 2.4 are not exactly useful as they are designed for windows platform. From our scan, we see the host is linux-based.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/2d23bac8-cf86-4034-9112-4f210ed92840)

Port 80 shows default apache webpage. There is not anything of importance in the source page as well.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/39c84216-1751-418c-86cd-1f8852a1e507)

But the other http service on port 62337 seems interesting and it offers a login page.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/6f15b40e-b2a7-4b62-af11-5725401b1487)

And let's try to login using the credentials.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f5dba3ae-ad35-4e9a-a847-4bae4da08314)

Successful login.

The keyword "codiad 2.8.4" looks like a clue. Let's do an OSINT on it.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/357229f8-bc7d-44a6-88df-0545a5729c28)

There is an exploit to get Remote Code Execution, the fourth and verified one.
Let's download it.
And we need the credentials to use it. Let's execute the exploit.
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/19439962-b2f5-48ad-a4db-22a3b79bb0b0)

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5a579858-c647-4976-bcff-dd60badc977a)

Successful reverse shell.

# user.txt
We see that the user.txt flag is in /home/drac. But we don't have permission to read it.
Printing the history.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/3809dacb-37eb-4235-ba66-322864fade89)

We can see the credentials of drac, which we can use to escalate privilege.
We successfully sshed as drac and see that user.txt

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/2c45f12a-1239-431e-9919-eae479c4c316)

# root.txt
Usually, root.txt is found /root folder. But we need to further escalate our privilege.
we observe that drac can execute these commands with root privilege.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d7741992-e705-4347-afc3-4f99fbc4f209)










































# Credits
https://tryhackme.com/p/bluestorm
https://tryhackme.com/p/403Exploit
