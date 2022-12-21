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

- Step 1 Create Two Virtual Machines
- Step 2 Ensure Connectivity between the client and Domain Controller
- Step 3 Install Active Directory
- Step 4

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
Click Add roles and features and the wizard will open.  Click on next a couple of times until you see your destination server to connect.  Click next a few times again until you see the Select server roles.  Check the radio button Active Directory Domain Services.  On that page, click on Add Features. Click on next through the proceeding pages that installs all of the dependencies and the final install button.
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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
