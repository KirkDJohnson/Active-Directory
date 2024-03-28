<h1>Comprehensive Lab</h1>



<h2>Description</h2> This lab involved me creating a visual diagram to illustrate how the Virtual Machines (VMs) and data will flow as well as making sure the IPs stry with within the same network submask to ensure conenctively. Then begun the grueling task of installing, launching, configuring, and credentially the four VMs on my local machine ensuring they can share resources without crashing or work at a crawling pace. I ran Ubuntu Server to host Splunk (a Security Information Event Management or SIEM), to inject logs from the other endpoints. The other endpoints being a windows 10 machine and a Windows 2022 sever which would run active direcotry as the domain controller. 

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Windows CMD</b>
- <b>Sever Manager</b>

<h2>Environments Used </h2>

- <b>Windows 10 </b>
- <b>Linux Ubuntu Server </b>
- <b>Kali Linux</b>
- <b>Microsoft Sever</b>
<h2>Program walk-through:</h2>

<p align="center">
Network Diagram<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/81584485-1c09-4c29-a5a7-2a3513a92323" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
On Virtual Box configured the four VMs to use NAT Network to ensure cross connectivity on the same network. <br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/028449e9-765c-4666-b5b8-008860dbaf4d" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
On the Ubuntu Sever (named Splunk) installed netplan and configured static IPs of the network and well as DNS.<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/f9889662-63fc-4ff4-b397-eb7708abc798g" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/0de8c64a-98db-4473-8d7f-a6e1ff9dc6ff" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
After adding user: kirk to vboxsf, I mounted vboxsf to access a file on my local machine where I installed the splunk host instance <br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/b6c879dd-1599-4123-8240-778fdf620eaf" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Moved Splunk to the /opt/splunk/ direcotry and changed user to splunk, and configured for splunk to start on boot as user splunk<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/cb9283fa-3d6b-4eef-adbe-8f417b4046bc" height="50%" width="50%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/560da01c-755b-410f-a198-451e5658ca47" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
Now that the Splunk sever has been configured I moved to the Windows 10 endpoint and configured its network settings statically<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/121647b1-1ff1-456d-b185-5fcb12943b49" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Downloaded and configured splunk universal forwarder and sysmon with an external sysmon config on the Windows 10 endpoint (both to generate logs for splunk<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/5e37c734-e2d3-4568-a7f8-802529740a51" height="50%" width="50%" alt="Active Directory/Splunk"/>
<br />
<br />
TEXT<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/121647b1-1ff1-456d-b185-5fcb12943b49" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br /><br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/121647b1-1ff1-456d-b185-5fcb12943b49" height="80%" width="80%" alt="Active Directory/Splunk"/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/7ce10f3e-d8b8-4387-baf8-bca915d70dbe" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
After creating a new inputs.conf file, I logged into splunk via web browser on the W10 host to ensure logs are being forwarded<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/33292b90-987b-44e7-9037-ce643fe3737e" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
Now I moved over to the Windows Sever 2022 VM and begun configuring Active Directory Domain Servives (AD DS)<br/>
<img src="https://github.com/KirkDJohnson/Active-Directory-/assets/164972007/8b0d0af9-e3d5-4ae9-bf43-ecd8cf080623" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
TEXT<br/>TEXT<br/>
<img src="" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
TEXT<br/>TEXT<br/>
<img src="" height="80%" width="80%" alt="Active Directory/Splunk"/>
<br />
<br />
TEXT<br/>
<h2>Thoughts</h2>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
