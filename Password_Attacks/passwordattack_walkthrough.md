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






