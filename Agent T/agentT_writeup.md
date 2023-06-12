# Agent T
# Description: Something seems a little off with the server
# Link to the Tryhackme Room
https://tryhackme.com/room/agentt

This is a simple CTF activity

Target IP : 10.10.62.95

# Reconnaissance

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d69bdb30-5119-477c-87aa-e1e05c67e456)

After scanning using nmap, we see that there is only one port open which is port 80 hosting a webserver. 
let's walk around the website.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/b0916c4d-354e-4b96-83b7-16009dfad275)

Interestingly, we are logged in as an admin without authentication and we see the admin dashboard. There is not much we get from the page source.

After running nikto ( a cmd tool that scans websites for known vulnerabilities), we see the following output. 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/880de6b5-ff17-4e49-b99d-3fc5feb4174b)

The first thing that we observe is the website is powered by php 8.1.0-dev. Based on this version disclosure, let's look for PoC exploits. 
Searching exploit-db gives us the following output.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/cc65f642-f560-49ff-8932-eedc36872e8b)

The first output can be used to gain RCE. Let's download it and see how we can use it.

After executing the python file as follows, we get an interactive shell as the root user.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/71040f50-079e-4db1-9321-ae62aead6b31)

And we also see the flag is located in the root directory.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/03880d9b-8489-4284-9d92-6b2d04eb6160)

and with that, the mission is accomplished.

Credits:  https://tryhackme.com/p/ben

          https://tryhackme.com/p/JohnHammond
          
          https://tryhackme.com/p/cmnatic
          
          https://tryhackme.com/p/blacknote
          
          https://tryhackme.com/p/timtaylor
          
          https://tryhackme.com/p/THMDan


