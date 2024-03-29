<h1>Comprehensive Lab</h1>



<h2>Description</h2> This lab involved me creating a visual diagram to illustrate how the Virtual Machines (VMs) and data will flow as well as making sure the IPs stay within the same network to ensure connectively. Then begun the tedious task of installing, configuring, and providing credentials to the four VMs on my local machine ensuring they can share resources without crashing or work at a crawling pace. I ran Ubuntu Server to host Splunk (a Security Information Event Management solution or SIEM), to injest logs from the endpoints. The endpoints being a windows 10 machine acting as a domain user and a Windows 2022 sever which would run active direcotry as the domain controller. They had sysmon and splunk universal forwarder configured to send logs to the splunk server. After I configured Active Directory Domain Services, I launched a seperate Kali Linux VM and performed a brute force attack against the domain user to obtain the credentials and see how the splunk logs would look. Lastly, I installed Atomic Red Team on the Windows 10 VM to generate more security logs to send to splunk for the sake of curiosity. 

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Windows CMD</b>
- <b>Linux Terminal</b>
- <b>Sever Manager</b>
- <b>Active Directory Domain Services</b>
- <b>Splunk Enterprise and Universal Forwarder</b>
- </b>Splunk Search Processing Language (SPL)</b> 
- <b>Crowbar and Atomic Red Team</b> 

<h2>Environments Used </h2>

- <b>Oracle Virtual Box for all Virtual Machines</b>
- <b>Windows 10 </b>
- <b>Linux Ubuntu Server </b>
- <b>Kali Linux</b>
- <b>Windows Server 2022</b>
<h2>Lab Overview</h2>

<p align="center">
Creating a visual network diagram with draw[.]io<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/81584485-1c09-4c29-a5a7-2a3513a92323" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
On Virtual Box configured the four VMs to use NAT Network to ensure cross connectivity and internet access. <br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/028449e9-765c-4666-b5b8-008860dbaf4d" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
On the Ubuntu Sever (named Splunk) installed netplan and configured static IPs of the network and DNS.<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/f9889662-63fc-4ff4-b397-eb7708abc798g" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/0de8c64a-98db-4473-8d7f-a6e1ff9dc6ff" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
After adding user: kirk to vboxsf, I mounted vboxsf to access a folder on my local machine where I installed the splunk host instance <br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/b6c879dd-1599-4123-8240-778fdf620eaf" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Moved Splunk to the /opt/splunk/ direcotry and changed user to splunk, and configured splunk to start on boot as user splunk<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/cb9283fa-3d6b-4eef-adbe-8f417b4046bc" height="50%" width="80%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/560da01c-755b-410f-a198-451e5658ca47" height="50%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Now that the Splunk sever has been configured, I moved to the Windows 10 endpoint and configured its network settings statically<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/121647b1-1ff1-456d-b185-5fcb12943b49" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
On the Windows 10 VM, I downloaded and configured splunk universal forwarder and sysmon with an external sysmon config. Both to generate logs for splunk<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/5e37c734-e2d3-4568-a7f8-802529740a51" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/a867cbc9-c59b-4e69-b29a-98391983b338" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
After creating a new inputs.conf file, I logged into splunk via web browser on the W10 host to ensure logs are being forwarded<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/33292b90-987b-44e7-9037-ce643fe3737e" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Now I moved over to the Windows Sever 2022 VM and begun configuring Active Directory Domain Servives (AD DS) and created a root domain<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/8b0d0af9-e3d5-4ae9-bf43-ecd8cf080623" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/fcd4a767-4c0d-4a9e-8fc3-2e238cab305c" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
The login screen ...\Administrator confirms that AD was configured correctly, so I logged back in as admin and begun adding users to a new Organizational Unit<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/d300d3ec-7a57-4e41-a367-5481f0d2e947" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/6c04c03b-994f-4099-aa16-d3fc20d6528a" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
Back on the Windows 10 VM, I became apart of the ADlab.local domain/forest I created with AD DS, restarted and logged in as the created user with active directory<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/14366df9-ed18-44fb-88c6-febe3f1e35b7" height="80%" width="80%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/66441845-135c-47bf-a549-d36c2b657c99" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Now for the fun part, I launched Kali Linux and begun preparing a brute-force attack against the Active Directory account I created, I used the tool crowbar with the rockyou.txt password file (I did nano the file and add the actual password for it to crack the account)<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/c1028223-927d-4f71-97f8-34e9ab3bb458" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Back to splunk, the EventID 4625 indicates a failed login attempt on windows, and the command I ran on kali used the file 50 times which can be seen on splunk, the alerts were generated at the same time 9:21:27.000, a clear sign of a brute-force attack<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/35ce4897-14e2-47d9-9b1c-9f3d256f9b71" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/7cbb6800-f80b-4619-8e70-cd98c10d4f5b" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
Lastly to generate more logs for splunk I installed Atomic Red Team that uses MITTER ATT&CK vectors (an attacker tool) on the W10 endpoint and used T1136.001 to create a new local account<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/432fa735-4dcd-4199-b2a2-16a79a7a36dc" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/ef2f43c9-ff51-43b5-9a87-eca445ffdfb6" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
<br/>
Earlier in powershell, you can see that a new user was successfully created which can be seen in the splunk logs. This was the Mitre Att&ck page for T1136 I used.<br />
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/6bfe171b-e430-4305-ab2e-9a48a74f121d" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/a0ae1d7a-2340-40f2-8044-bbb3ed89d63f" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />


<h2>Thoughts</h2>
This was definitely the most comprehensive well rounded lab I have done. It involved network and account provisioning by confiuring multiple IP addresses and the entire Actice Directory and adding users to it. It signficantly advanced by knowledge of cybersecurity blue teaming by creating rules in splunk, parsing the logs, and generating and identifying security incidents. The lab also increased my knowledge of how red-teamers or malicious actors could conduct a brute force attack in a live environment. I tried to be very methodical in my approach to this by first drawing up how I wanted the end result to look or a simple illustration of how it may look in real life environment without leveraging VMs. Moreover, it required me to research different attack vectors and splunk configuration rules something that is a crucial skill to have as a cybersecurity professional. However, the lab was also extremely stressful and had many hiccups ranging from the multiple VMs running on my local computer using up too much RAM and crashing, not asssigning enough storage space to kali and having to research how to increase storage to the partition and so on. It was a marathon of a lab to conduct in one sitting but absoutely worth it for the hands on experience I got in so many disiplines within cybersecurity.
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
