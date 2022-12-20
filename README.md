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
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<h3>Create Two Virtual Machines</h3>

<p>
<img src="https://i.imgur.com/pqp7C8d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To start go to portal.azure.com and create a profile or login. Create a subscription name-->Create a resource group-->Create two virtual machines>Create a domain controller using Windows Server and a client PC using Windows 10 Pro
</p>
<br />

- Step 2 Ensure Connectivity between the client and Domain Controller
<p>
<img src="https://i.imgur.com/b5AWooQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Azure, click on Networking and from there it will open its page.  We can change the private IP address from dynamic to static so the IP address will stay the same for client's DNS to connect to the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
