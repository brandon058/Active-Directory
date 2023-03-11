<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>

Active Directory (AD) is a database and set of services that connect users with the network resources they need to get their work done. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2> Configuration Steps</h2>
   
  
  -1:Setup resources in microsoft Azure   
  
  -2:Establish connectivity between the client and Domain Controller
  
  -3:Install active Directory
 
  -4:Create an administrator and regular account in Active Directory 
 
  -5:Join client to Domain 
 
  -6:Setup Remote Desktop for non -administrative users
    

<h3> Setup resource in microsoft Azure</h3>
 
 First we need to create two virtual machine. The first one will be (Client-1) will be using windows 22
 and (DC-1) will have windows 10. Be sure to keep both virtual machines in the same Region.
 

<img src="https://i.imgur.com/XbuO2GD.png" height="80%" width="80%" alt="1. DC-1 VM"/>
<img src="https://i.imgur.com/epKINcm.png" height="80%" width="80%" alt="2.client-1 VM"/>
   
   
   
   Navigate to DC-1"s Networking section and set the IP Address to static

<p>
<img src="https://imgur.com/lmcuYCn.png" height="80%" width="80%" alt="1. "/>
</p>   
 
  Click on IP config            

 <p>
 <img src="https://i.imgur.com/MhfRJiH.png" height="80%" width="80%" alt="1. "/>
 </p>   
   
 Look for the private IP address.Click the Assignment and set to static.

<p>
<img src="https://i.imgur.com/6TmBUu1.png" height="80%" width="80%" alt="3. "/>



<h3>Establish connectivity between the client and Domain Controller</h3>
<p>

 Ensure connection between DC-1 and Client-1. log into client-1 open the command line and type ping-t to ping Dc-1.

 <img src="https://i.imgur.com/hhelYIM.png" height="80%" width="80%" alt="1. "/>
 <img src="https://i.imgur.com/axnzdcP.png" height="80%" width="80%" alt="1. "/>   
 <img src="https://i.imgur.com/gqQwYO8.png" height="80%" width="80%" alt="1. "/> 


<h3>Install active Directory</h3>



<p>
Going back to DC-1", open the Server Manager, it should already be open. or select the start menu and search it. Click "Add roles and features", follow the prompts.select "Server Roles", check "Active Directory Domain Services" and
continue to follow all installaion until it done.
</p>
<p>
<img src="https://i.imgur.com/zG16QBV.png" height="80%" width="80%" alt="Active dirctory" Steps"/>
</p>
<p>
<img src="https://i.imgur.com/y8hU38D.png" height="80%" width="80%" alt="AD" Steps"/>
</p>
Click the flag with a yellow warning sign and click "Promote this server to a domain controller".
</p>
<p>
<img src="https://i.imgur.com/jHJee1y.png" height="80%" width="80%" alt="activedirectory" Steps"/>
</p>
<br />

<p> 
 Domain controller will restart and add updates to DC-1. 
 Once it's completed Log into the virtual machine with domain name/username and password
<p>
<img src="https://i.imgur.com/l6S8LQn.png" height="80%" width="80%" alt="DC1" Steps"/>
</p>


<h3>Create an administrator and regular account in Active Directory </h3>
Open the server manger, click Tools,then click Active directory users and computers

  

<img src="https://i.imgur.com/hSi9f3x.png" height="80%" width="80%" alt="D S Steps"/>

<p
Right-click on your domain name to create a couple new organizational units. One named "EMPLOYEES" and the other named "ADMINS".
</p>
<p>
<img src="https://i.imgur.com/NbzijVW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
  
<p>
Create a new user in "EMPLOYEES", and assign them to the "Domain Admins" group.
</p>

<p>
<img src="https://i.imgur.com/7RV8jxp.png" height="80%" width="80%" alt="ADMIN A Steps"/>
</p>

<p>
<img src="https://i.imgur.com/XO25pkZ.png" height="80%" width="80%" alt="k n Steps"/>
</p>

 <p>
 <img src="https://i.imgur.com/oaklLo6.png" height="80%" width="80%" alt="k n DZ "/>
 </p>


<p>   
Log out of "DC-1" as Labuser and log back in as the admin account (jane_admin)
</p>
  
<h3>Join Client to the Domain </h3>

<p>
To do this Head back to Microsoft Azure virtual machines, click "Client-1", click on "Networking" 
</p>

<p>
<img src="https://i.imgur.com/YYIEwPK.png" height="80%" width="80%" alt="Admin Steps"/>                                                                                                                                        </p>

  

<p>
 Click "DNS Servers", Then click "Custom",
</p>
<p>
<img src="https://i.imgur.com/8Zn5ky9.png" height="80%" width="80%" alt="Domain Steps"/>
</p>
<br /> Copy and paste the Private IP of "DC-1". Save, then restart "Client-1" through Azure.
<img src="https://i.imgur.com/lTkiGzN.png" height="80%" width="80%" alt="DNSs"/>
<p> 
   
ok so log back into "Client-1" Search "Settings" and open it,on the rightside of your screen click"Rename this PC (advanced)". A window will pop up, click "Change...", enter your domain name.
</p>
<p>
<img src="https://i.imgur.com/xaYQFK3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Configuring Remote Desktop for Non-administrator Users</h3>
    This time log in using the domaine name and the admin account (mydomaine.com/jane_admin).
    after you are logged in.client-1 is going to restart.
<p>
<img src="https://i.imgur.com/BsJtyy1.png" height="80%" width="80%" alt="notice"/>
    
   Go back to Client-1 and "Right click" to open system properties.
<img src="https://i.imgur.com/TLAfjB6.png" height="80%" width="80%" alt="Active"/>
</p>
    Select users that can remotely access this PC to Add Domaine user group.
<img src="https://i.imgur.com/gnAcPyL.png" height="80%" width="80%" alt="configu"/>
  

  Log into "DC-1" and open up "Active Directory Users and Computers"click on the flolder name Users . then double Click on Domaine users
  anyone whos in domane user group should be allow to log in to client-1.

<p>
<img src="https://i.imgur.com/8cMmP1e.png" height="80%" width="80%" alt="my active_directory"/>
</P>








