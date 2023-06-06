# Gaming Server - A tryhackme room designed for beginner level CTF (An Easy Boot2Root box for beginners)
# Link to the room
https://tryhackme.com/room/gamingserver

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5c005f0b-f3ad-4781-bb3e-04d4b0bc82cb)

# Objective
To compromise the web app and find two flags.
Target IP: 10.10.210.57
As always, we will follow typical attack methodology.

# Reconnaissance

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/6f4d9c57-8b3e-4f5c-9a1f-cda2ff0c8cef)

Port 22 (ssh) and 80 (http) are open. 
Let's have a look at the web app.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/bfe494fb-3690-40a5-ad68-e236af2f3fdd)

This is the website homepage.

Looking at the page source.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b4445cbf-7aa2-4da6-8407-bc36ffbc50e5)

At the bottom of the page, there is a name (john). Potentially, one of the developers. Take note of that.

Let's run gobuster for further reconnaissance.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1aaa6908-33c0-4062-8811-628f884274be)

There are two directories of interest, namely uploads and secret. 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/4e25a502-348e-4094-a40f-cbbd82fd8146)

In the "secret" directory, there is a secret key stored, which seems a private key belonging to one of the developers. Let's copy it locally.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f1033003-f682-4d41-91f9-2a8eeae67cff)

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b7fe6253-f27d-4135-b776-eced46a566cc)

We need to modify the permissions of the secret key. Only the owner can read and write to it.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f93026dd-5c51-44ed-891d-ffdb5a919b6e)

Earlier, we saw a potential username john, so we can try to connect to the server over ssh using the username and secret key.
However, as shown in the above image, we need a passphrase to use the private key. Let's try ssh2john to figure out the passphrase.

using /opt/john/ssh2john secretkey > passphrase.txt
The hash of the passphrase is stored in the passphrase.txt

We can then use john to crack the hash.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/3185dd43-0b82-44d4-98a1-8bc94a11bfcb)

Now that we found the passphrase in plaintext, let's try to connect over ssh.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/9444f898-6e60-44c7-b363-2124fd6674d9)

Login Successful.

# First Flag - user.txt

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/9073ee1a-54af-49ed-ad21-726a5efef1a2)

Seems john doesn't have much privilege.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5f7f5f2b-e73e-4a18-9856-ee90ae4320d6)

But in the output of gobuster, we see a folder called uploads.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e3199bcb-258b-4d66-84ea-f0e1f631c7f1)

# Privlege Escalation to find root.txt flag

LXD (pronounced "lex-dee") is a container hypervisor for Linux systems. We can use to mount the root folder of the target machine to /mnt of the target machine.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/637040a0-2428-478e-a589-f2ccc80541b7)

git clone https://github.com/saghul/lxd-alpine-builder.git and create a simple container by running the build-apline (./build-apline), which will produce .tar.gz file and transfer it to the attacke machine.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/cf038a55-d72c-4021-849b-aa682b3eded5)

Now that the root folder is mounted to /mnt and we can change directory to find the flag.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/56bea12e-ddda-4806-8636-b6118d82f530)

All Done. A very good room.

Credits: https://tryhackme.com/p/SuitGuy
























