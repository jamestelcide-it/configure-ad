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

- Create resources
- Ensure connectivity between the client and Domain Controller
- Install Active Directory
- Create an admin and normal user account in AD
- Join Client-1 to your domain
- Setup remote desktop for non-administrative users on Client-1
- Create additional users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<h2>Setup Resources in Azure</h2>

<img src="https://github.com/user-attachments/assets/1acb6b35-fa24-47df-ac89-12085cd282fd" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/1acb6b35-fa24-47df-ac89-12085cd282fd) -->

<img src="https://github.com/user-attachments/assets/016eb755-087b-4d20-bd09-dfa6349a69ca" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/016eb755-087b-4d20-bd09-dfa6349a69ca) -->

<p>
We create the Domain Controller VM and give it the name "DC-1".
</p>
<br />

<img src="https://github.com/user-attachments/assets/c6dffe8a-70e1-408e-a76c-b6c521a80a21" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/c6dffe8a-70e1-408e-a76c-b6c521a80a21) -->

<p>
Now we can create the Client VM that we can call "Client-1". While setting it up we can use the same Resource Group and VNet that was created while setting up our domain controller.
</p>
<br />

<img src="https://github.com/user-attachments/assets/9cf95844-f378-4322-9085-60901e8af0d1" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/9cf95844-f378-4322-9085-60901e8af0d1) -->

<img src="https://github.com/user-attachments/assets/b2a6006d-851b-47d8-be5a-6f89fa5d5670" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/b2a6006d-851b-47d8-be5a-6f89fa5d5670) -->

<p>
Now we can set the Domain Controller's NIC Private IP address to be static.
</p>
<br />

<h2>Ensuring Connectivity Between the Client and Domain Controller</h2>

<img src="https://github.com/user-attachments/assets/ed60fbaf-e597-4839-b8bb-8db977449724" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/ed60fbaf-e597-4839-b8bb-8db977449724) -->

<img src="https://github.com/user-attachments/assets/9830a2db-b00c-4d2a-b331-5d67641059d6" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/9830a2db-b00c-4d2a-b331-5d67641059d6) -->

<p>
We can now log into the Domain Controller and enable ICMPv4 in the local windows firewall
</p>
<br />


<img src="https://github.com/user-attachments/assets/22ca79f5-8c6a-4bcb-9b43-523799633932" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/22ca79f5-8c6a-4bcb-9b43-523799633932)
 -->
<p>
We can now log into Client-1 with Remote Desktop and ping DC-1's private IP address with ping -t (-t indicates a perpetual ping)
</p>
<br />

<h2>Install Active Directory</h2>

<img src="https://github.com/user-attachments/assets/7e696f0b-d6ef-4762-8ce1-2df3d2e9e8f3" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/7e696f0b-d6ef-4762-8ce1-2df3d2e9e8f3) -->
<p>
To install Active Directory we can start by installing Active Directory Domain Services.
</p>
<br />

<h2>Create an Admin and Normal User Account in AD</h2>

<img src="" height="80%" width="80%" />
<!--  -->
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<h2>Join Client-1 To Your Domain</h2>

<img src="" height="80%" width="80%" />
<!--  -->
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<h2>Setup Remote Desktop for Non-Administrative Users on Client-1</h2>

<img src="" height="80%" width="80%" />
<!--  -->
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<h2>Create Many additional Users and Attempt to Log Into Client-1 with One of the Users</h2>

<img src="" height="80%" width="80%" />
<!--  -->
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
