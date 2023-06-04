# This is another CTF room designed for beginners
# The tryhackme link to the room: https://tryhackme.com/room/rrootme

Let's start by deploying the target machine and our attack machine.

Target Machine IP : 10.10.237.141

As always, let's start out by scannning and Enumerating the target.

# Reconnaissance
Running nmap against the target machine to map out the open ports and services they are providing. The result is as follows:

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e11e7410-0719-44d6-9609-656aceeb2e01)

There are two ports open, port 22 and port 80 for ssh and http, respectively. 
Take note: we are also able to infer the version of the services they are providing which is essentially version disclosure. That can later be used to find PoC exploits to leverage potential vulnerabilities associated with that particular version. 

Let's browse the website.
This is the web page.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/6bf6924d-08f2-4f50-90d9-db6d75f83202)

Viewing the page source does not give away much information

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a420f6fa-3f80-40d0-9f21-9d42ebbf63c5)

Let's launch gobuster to find hidden directories and files.
And this is the output.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/ed04f127-4281-4ab6-9267-64ccd43a7e26)

panel and uploads are particulary of interest for us. Let's browse them.

Panel directory provides an interface to upload a file and uploads directory is where all files are stored.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f9ae3dbd-7146-4592-9aca-e03478df25af)

Let's use the panel page to upload a web shell (php reverse shell) that will form a reverse connection to us.
However, the site does not allow to upload a php file. 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/35831ecd-15a6-4535-9e83-07d9ef16b12d)

Let's change the file extention and upload it again. Before that, let's open a netcat listner on our machine that will be used to receive a reverse shell and also edit the php file i.e IP address of our machine and the port our machine is listening on.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/4acb5635-43b0-49e6-a328-fde355215533)

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c29af7e1-fac4-4d30-80ba-f2173302df2c)

Now, the upload is successful.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e33eb755-bfd7-4082-abe2-fff5319d6a07)

Let's go to uploads page, and click the file that we uploaded. 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/69d645f5-4fab-4728-a6da-49cb45118c86)

Now, let's find a way to escalate the privilege to root level.
One way to do that is to find files with suid set. Meaning they can be executed with the privilege of their owner.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a7f6a057-fb9f-4f13-b65e-79a2749fa919)

/usr/bin/python has a SUID bit set. Let's search for a way to escalate privilege using on GTFOBins.


We have acquired a reverse shell and stabilize the terminal. Let's look for flags.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d9a6fe2a-1770-4966-a026-9b11cf4b4a01)

We first executed "find" command and once we found out where the file is located, we can see its content.



