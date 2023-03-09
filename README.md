<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

Active Directory Deployed in the Cloud (Azure)</h1>
Active Directory (AD) is a database and set of services that connect users with the network resources they need to get their work done. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
- First step is to create to two Azure virtual machines.

<img src="https://i.imgur.com/XbuO2GD.png" height="80%" width="80%" alt="1. "/>

SET THE IP ADDRESS TO STATIC
<img src="https://i.imgur.com/epKINcm.png" height="80%" width="80%" alt="2.client-1 VM"/>
<img src="https://imgur.com/lmcuYCn.png" height="80%" width="80%" alt="1. "/>
                   
<img src="https://i.imgur.com/MhfRJiH.png" height="80%" width="80%" alt="1. "/>

<img src="https://i.imgur.com/6TmBUu1.png" height="80%" width="80%" alt="3. "/>

ENSURE CONNNECTION BETWEEN DC-1 AND CLIENT-1
 log into client-1 and ping Dc-1
<img src="https://i.imgur.com/hhelYIM.png" height="80%" width="80%" alt="1. "/>
 <img src="https://i.imgur.com/axnzdcP.png" height="80%" width="80%" alt="1. "/>   
 <img src="https://i.imgur.com/gqQwYO8.png" height="80%" width="80%" alt="1. "/> 



- Step 4

<h1>Back Inside the Virtual Machine of DC-1</h1>

<p>
Navigate back to the virtual machine "DC-1", bring up the Server Manager. If not already open, open the start menu and search it. Click "Add roles and features", and go through the installer. Once you get to "Server Roles", check the box beside "Active Directory Domain Services" and finish the installer.
</p>
<p>
<img src="https://i.imgur.com/zG16QBV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
You still have to promote "DC-1" to a Domain Controller. Click the flag with a yellow warning sign and click "Promote this server to a domain controller".
</p>
<p>
<img src="https://i.imgur.com/jHJee1y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
The computer will restart and disconnect. Log into the virtual machine with "< domain name >/< username >" then enter the password and hit enter.
</p>
<br />
  
<p>
Open the Server manager, click "Tools", then click "Active Directory Users and Computers"
<p>
<p>
<img src="https://i.imgur.com/hSi9f3x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Right-click on your domain name to create a couple new organizational units. One named "EMPLOYEES" and the other named "ADMINS".
</p>
<p>
<img src="https://i.imgur.com/pnjPRLE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
  
<p>
Create a new user in "EMPLOYEES", and assign them to the "Domain Admins" group.
</p>
<p>
<img src="https://i.imgur.com/S6tn9hv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
  
<p>
Log out of "DC-1" and log back in with the new user with admin permission.
</p>
  
<h1>Joining Client-1 to the Domain With Azure</h1>

<p>
Head back to Microsoft Azure virtual machines, click "Client-1", click "Networking", then click "Client-192".
<p>
<p>
<img src="https://i.imgur.com/fDAzj4x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> 
  
<p>
Click "DNS Servers", click "Custom", and paste the Private IP of "DC-1". Save, then restart "Client-1" through Azure.
</p>
<p>
<img src="https://i.imgur.com/D6Aqdgl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /> 
  
<p>
Log into "Client-1" as the original admin user (the one you created with the VM). Search "Settings" and open it, click "About", click "Rename this PC (advanced)". A window will pop up, click "Change...", click "Domain" and enter your domain. Another window will pop up, log in with a user that has admin privileges.
</p>
<p>
<img src="https://i.imgur.com/kHpYsn6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
  
<p>
Log into "DC-1" and navigate to "Active Directory Users and Computers" in the Server Manager. Click "Computers" to see if "Client-1" appears. Create a new organizational unit named "Clients" and drag "Client-1" into it.
</p>
<p>
<img src="https://i.imgur.com/3EmViVb.png" height="80%" width="80%" alt="my active_directory"/>
</p>

<h1>Configuring Remote Desktop for Non-administrator Users</h1>
  
<p>
Log into "DC-1" and navigate to "Settings". Click "Remote Desktop", click "Select users that can remotely access this PC". Click "Add...". Add "Domain Users" and click "Ok".
</p>
<p>
<img src="https://i.imgur.com/3EmViVb.png" height="80%" width="80%" alt=my active dictory"Steps"/>
</p>
<br />

<p>
Any user who is in your domain may now connect to the virtual machine.





