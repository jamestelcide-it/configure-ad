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

<img src="https://github.com/user-attachments/assets/ec717154-50ac-4e9d-b3e8-2cb6937f3bad" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/ec717154-50ac-4e9d-b3e8-2cb6937f3bad) -->
<p>
Next we can promote as a Domain Controller.
</p>
<br />

<img src="https://github.com/user-attachments/assets/527913fb-cea5-4694-878c-8578da56c30e" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/527913fb-cea5-4694-878c-8578da56c30e) -->
<p>
Next we setup a new forest and give it any domain we would like. In this example I will name mine myadproject.com.
</p>
<br />

<img src="https://github.com/user-attachments/assets/2794fa03-f02c-4302-ad35-cad563da2dfd" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/2794fa03-f02c-4302-ad35-cad563da2dfd) -->
<p>
Now we can restart and log back into DC-1 as the user: myadproject.com\labuser.
</p>
<br />

<h2>Create an Admin and Normal User Account in AD</h2>

<img src="https://github.com/user-attachments/assets/11576d7d-6faa-46c7-86c6-a401f4405783" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/11576d7d-6faa-46c7-86c6-a401f4405783) -->

<img src="https://github.com/user-attachments/assets/1a8c4eaf-1dc8-471d-8415-4d2e622a52b9" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/1a8c4eaf-1dc8-471d-8415-4d2e622a52b9) -->

<p>
In Active Directory Users and Computers (ADUC) we can create an Organizational Unit called "_EMPLOYEES" and another Organizational Unit called "_ADMINS".
</p>
<br />

<img src="https://github.com/user-attachments/assets/894fdf04-3d68-40b7-bd5c-2869eca04b52" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/894fdf04-3d68-40b7-bd5c-2869eca04b52) -->
<p>
We can now create a new employee named "Jane Brown" with the username of "jane_admin".
</p>
<br />

<img src="https://github.com/user-attachments/assets/a5c5b534-b73e-4a71-92d1-13d93cacf2d6" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/a5c5b534-b73e-4a71-92d1-13d93cacf2d6) -->
<p>
Now we can add jane_admin to the "Domain Admins" Security Group.
</p>
<br />

<img src="https://github.com/user-attachments/assets/4ef002a3-1016-48f8-9bb4-42c4d5dd1183" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/4ef002a3-1016-48f8-9bb4-42c4d5dd1183) -->
<p>
Now we can log out of the Remote Desktop connection to DC-1 and log back in as "MYACTIVEDIRECTO\jane_admin". We can use jane_admin as our account from now on.
</p>
<br />

<h2>Join Client-1 To Your Domain</h2>

<img src="https://github.com/user-attachments/assets/06bc12e5-d361-4270-8344-6094de08321a" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/06bc12e5-d361-4270-8344-6094de08321a) -->
<p>
From the Azure Portal, set Client-1's DNS settings to the DC's Private IP address.
</p>
<br />

<img src="https://github.com/user-attachments/assets/0cc08b5e-0dc8-4f84-bed4-6681ae0a188b" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/0cc08b5e-0dc8-4f84-bed4-6681ae0a188b) -->

<img src="https://github.com/user-attachments/assets/022f0f59-60fd-49be-ab61-eb893ddb94ed" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/022f0f59-60fd-49be-ab61-eb893ddb94ed) -->

<p>
Next from the Azure Portal, Restart Client-1. Then we can Login to Client-1 through Remote Desktop as the original local admin and join it to the domain
</p>
<br />

<img src="https://github.com/user-attachments/assets/1895199e-c945-4fe0-84ef-a22c26b42f67" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/1895199e-c945-4fe0-84ef-a22c26b42f67) -->

<img src="https://github.com/user-attachments/assets/232e3871-2454-49d7-b254-627282f24044" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/232e3871-2454-49d7-b254-627282f24044) -->

<p>
We can now login to the Domain Controller through remote desktop and verify Client-1 shows up in Active Directory Users and Computers. For better organization we will create a new Organizational Unit named "_CLIENTS" and drag Client-1 here.
</p>
<br />

<h2>Setup Remote Desktop for Non-Administrative Users on Client-1</h2>

<img src="https://github.com/user-attachments/assets/cf5e7bb0-3451-4996-a3dc-6e79b4ee356a" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/cf5e7bb0-3451-4996-a3dc-6e79b4ee356a) -->
<p>
we can log into Client-1 as jane_admin and open system properties. Then we can click "Remote Desktop", Allow "Domain Users" access to Remote Desktop, then we can log into Client-1 as a non-administrative user.
</p>
<br />

<h2>Create Many additional Users and Attempt to Log Into Client-1 with One of the Users</h2>

<img src="https://github.com/user-attachments/assets/4b33b298-073c-4410-874f-fe578709396d" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/4b33b298-073c-4410-874f-fe578709396d) -->
<p>
We can log into DC-1 as jane_admin, open PowerShell_ise as an administrator. Then we create a new file and paste the contents of our script into it.
</p>
<br />

<img src="https://github.com/user-attachments/assets/e792e5c5-7e8f-43be-a784-8f722a2524ce" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/e792e5c5-7e8f-43be-a784-8f722a2524ce) -->
<p>
Once that is complete we can open Active Directory Users and Computers and confirm the accounts have been created. We will log into Client-1 with one of the accounts below
</p>
<br />

<img src="https://github.com/user-attachments/assets/2466e78a-4314-476e-aa5f-300c012e12d7" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/2466e78a-4314-476e-aa5f-300c012e12d7) -->

<img src="https://github.com/user-attachments/assets/954f679a-6296-4370-a573-b98b813d8e1f" height="80%" width="80%" />
<!-- ![image](https://github.com/user-attachments/assets/954f679a-6296-4370-a573-b98b813d8e1f) -->
