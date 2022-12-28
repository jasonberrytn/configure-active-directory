<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Two Virtual Machines
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users and attempt to login Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<h3>Create Two Virtual Machines</h3>

<p>
<img src="https://i.imgur.com/pqp7C8d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To start go to portal.azure.com and create a profile or login. Create a subscription name-->Create a resource group-->Create two virtual machines-->Create a domain controller using Windows Server and a client PC using Windows 10 Pro
</p>
<br />

<p>
<img src="https://i.imgur.com/bYr2TgH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open remote desktop connection and create two instances for the domain controller and the client.  You will need this to create connectivity between the two in the next step.
</p>
<br />

<h3>Ensure Connectivity between the client and Domain Controller</h3>
<p>
<img src="https://i.imgur.com/b5AWooQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Azure, click on Networking and from there it will open its page.  We can change the private IP address from dynamic to static so the IP address will stay the same for client's DNS to connect to the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/gQDiGHf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the networking screen, click on your Network interface name to open ipconfig from the menu.
</p>
<br />

<p>
<img src="https://i.imgur.com/56btGwo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once your NIC settings are open click on IP Configuration-->and the 3 dots for your private IP address at the bottom of the screen.
</p>
<br />

<p>
<img src="https://i.imgur.com/mhUy4vv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the ipconfig1 screen, change the assignment of the private IP address from dynamic to static.  Then click Save.
</p>
<br />

<p>
<img src="https://i.imgur.com/JkHLSUC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to the Domain Controller through the Remote Desktop Connection and enable ICMPv4 on the local Windows Firewall.  To do this go to Start-->Windows Administrative Tools-->Windows Defender Firewall with Advanced Security
</p>
<br />

<p>
<img src="https://i.imgur.com/m9W0gaQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows Defender menu click on Inbound Rules-->Click on Protocol to ascend the types-->Look for ICMPv4 protocol-->Right Click on echo requests and Enable Rule.  This will now allow the clients DNS server to establish connection with the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/NuJNMKK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To confirm connectivity, Open an instance of your client desktop and open your command prompt-->type ping -t and the private Ip address-->enter.  If a connection has been established between, this command will ping the specified host continuously until stopped. The host is replying so we have an established a successful connection between the client and the host.
</p>
<br />

<h3>Install Active Directory</h3>
<p>
<img src="https://i.imgur.com/5JTXYCf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open an instance of your Domain Controller from the Remote Desktop Connection and open the server manager.  Click on Add roles and features.  The following steps will install Active Directory on this server.
</p>
<br />

<p>
<img src="https://i.imgur.com/n8YIEe5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Add roles and features and the wizard will open.  Click on next continually until you see your destination server to connect.  Click next a few times again until you see the Select server roles.  Check the radio button Active Directory Domain Services.  On that page, click on Add Features. Click on next through the proceeding pages that installs all of the dependencies and the final install button.
</p>
<br />

<p>
<img src="https://i.imgur.com/gQbW88z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once Active Directory is installed the server still needs to be promoted as a domain server. In the upper right hand corner you will see a yellow caution sign next to the flag.  Click on that flag and the drop-down menu will populate and select Promote the server to a domain controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/gmSThMt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Deployment Configuration dialog box click on Add a new forest and give your DC a domain name and click on next. 
</p>
<br />

<p>
<img src="https://i.imgur.com/fmr2l9S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a password for Directory Service Restoration Mode (DSRM)-->Click Next until the domain controller finishes installing.  It will automatically reboot, and you will need to log in with your domain name\username and password as the server has been promoted to a domain controller. 
</p>
<br />

<h3>Create an Admin and Normal User Account in AD</h3>
<p>
<img src="https://i.imgur.com/hR8Wc6x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to your Remote Desktop Connection and log into your domain controller.  In the Server Manager Menu Click on Tools-->Active Directory Users and Computers and it will open its window.
</p>
<br />

<p>
<img src="https://i.imgur.com/WGcJQ4h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
In the Active Directory right click on your domain name and move your mouse to hover new-->Organizational Unit and left click to create folders for your AD.  We will create employees, admins, and security groups.
<p>

<br />

<p>
<img src="https://i.imgur.com/o5ZdcFp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After the Admins and Employees folder has been created.  Create an admin user for the admin folder.  To create a user right click on the _ADMINS folder under your domain-->Hover over New-->Hover to User-->Left click User

</p>
<br />

<p>
<img src="https://i.imgur.com/O21m7cr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the user has been created, the account must be added as an admin to that folder.  To add this user as an administrator right click on the name-->Hover to Properties-->Click on Properties-->Click on the Member Of tab-->Double click on Domain Users to open the next window.
</p>
<br />

<p>
<img src="https://i.imgur.com/EXKhRiA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the group box is populated, type "domains" enter the object names to be selected box-->Click on Check Names to the right-->Select Domain Admins-->Click Ok-->Click on Apply-->Click Ok. This will add your user as a domain admin to your active directory. Log out of the server and log back into the server as the admin.
</p>
<br />

<h3>Join Client-1 To Your Domain</h3>
<p>
<img src="https://i.imgur.com/qLYumOe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Azure and go to Virtual Machines-->Click on DC-1-->Networking and get the private IP address.  You will need this IP address to connect Client-1's DNS server.
</p>
<br />

<p>
<img src="https://i.imgur.com/PxitGw1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure go to virtual machines and select Client-1-->Networking-->Click on the Network interface-->DNS servers-->Select the ratio button in DNS servers from Inherit from network to Custom-->Type in DC-1's private IP address in the bar-->click Save.  Once the settings are saved you will restart Client-1 within the Azure portal and it will flush the DNS cache.
</p>
<br />

<p>
<img src="https://i.imgur.com/eTnq9pH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Client-1 using your login credentials from Microsoft Azure go to Start-->Settings-->About-->Rename this PC (advanced)-->Click on Domain-->Type the name of your domain in the domain box-->Click OK.
</p>
<br />

<h3>Setup Remote Desktop for non-administrative users on Client-1</h3>

<p>
<img src="https://i.imgur.com/PDKNMqe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect to your remote desktop now as the admin that you created in your _ADMINS folder in your active directory.  Right click on the start menu and click on system properties-->Click on Remote Desktop-->Click Select users that can remotely access this PC-->Type "domain" in the object names box-->Click on Check Names to the right-->Another dialog box will show the groups, select Domain Users-->Click ok
</p>
<br />

<p>
<img src="https://i.imgur.com/gt1QUvv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to your domain controller (DC-1) as an admin.  Go to your Server Manager-->Tools-->Active Directory Users and Computers to open your AD--Click on Users-->Domain Users--> This will bring you to your domain users policy.  This is where your non-admin users will show up.  *note Group Policy will allow you to assign many users to many systems at once but its not covered in this session.
</p>
<br />

<br />
<h3>Create additional users and attempt to login Client-1 with one of the users</h3>
<p>
<img src="https://i.imgur.com/AZCCuwI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
**This method will add 10,000 users using programming code in Powershell***
Log into your remote desktop  Client-1 with your system admin credentials.  Once windows is open type Powershell ISE in your search bar-->Open as an administrator-->Click on the New File icon-->Paste the code-->Click on the Run icon that looks like a green play button and the users will load into the system. We will go back to DC-1 and choose a user, get credentials and log into Client-1 with that users credentials.
</p>
<br />

<p>
<img src="https://i.imgur.com/js2k0Sm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In you domain controller go to your Server Manager-->Tools-->Active Directory Users and Computers-->Click on your domain-->Click on _EMPLOYEES folder that was created previously-->Double click on a user and the Properties window will populate-->Click on the Account tab-->type a login name in the box for your user-->Click Ok
</p>
<br />

<p>
<img src="https://i.imgur.com/emsDREZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into your Remote Desktop Connection using the username and credentials from DC-1.  You would need to use the domain\default username and default password.  Open command prompt and confirm username by typing whoami and type host name to verify the name of computer.
</p>
<br />

