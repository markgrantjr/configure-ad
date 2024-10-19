<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>


- Step 1
- Setup Domain Controller and Client-1 in Azure
-  Step 2
- install Active Directory
- Step 3
- Create a Domain Admin user within the domain
- Step 4
- Join Client-1 to your domain (mydomain.com)
- Step 5
- Setup Remote Desktop for non-afministrative users on Client-1
- Step 6
- Create additional users and attempt to log into Client-1 with one of the users

  
<h2>Deployment and Configuration Steps</h2>

<p>
  
Setup the Domain Controller in Azure. To do that you will create a resouce group, create a virtual network and subnet, create the Domain Controller virtual machine( Windows server 2022) named DC-1. After the VM is created, set the Domain controllers NIC private IP address to be static. Log into the VM and disable the Windows Firewall (for testing connectivity)


![Screen Shot 2024-10-14 at 9 02 50 PM](https://github.com/user-attachments/assets/bc83340d-f504-453e-8324-ad920b9936ea)
![Screen Shot 2024-10-14 at 9 00 27 PM](https://github.com/user-attachments/assets/e38822c8-2f9d-4e9a-8f75-8e9c2311280a)
![Screen Shot 2024-10-14 at 9 11 25 PM](https://github.com/user-attachments/assets/bfbb8b61-d12f-4d4b-a891-e27a53e3538c)
![Screen Shot 2024-10-14 at 9 11 54 PM](https://github.com/user-attachments/assets/440eed71-d619-4933-a37a-2bed0f0cd73c)
![Screen Shot 2024-10-14 at 9 15 40 PM](https://github.com/user-attachments/assets/759ed810-86d8-4439-8836-1c01e3cde9d8)
![Screen Shot 2024-10-14 at 9 17 50 PM](https://github.com/user-attachments/assets/3dd97bd7-2122-445b-ad21-1d145fe5514b)
![Screen Shot 2024-10-14 at 9 19 07 PM](https://github.com/user-attachments/assets/6daeb7b3-7225-46e3-95e2-a0f0b1ca9019)
![Screen Shot 2024-10-14 at 9 19 43 PM](https://github.com/user-attachments/assets/c1e1fe9f-eaac-4e11-868a-5c80b4e6cf11)


</p>
<p>
Setup Client-1 in Azure

Create the Client VM (Windows 10) named “Client-1”
Attach it to the same region and Virtual Network as DC-1
After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address
From the Azure Portal, restart Client-1
Login to Client-1
Attempt to ping DC-1’s private IP address
Ensure the ping succeeded
From Client-1, open PowerShell and run ipconfig /all
The output for the DNS settings should show DC-1’s private IP Address

</p>
<br />

<p>

  ![Screen Shot 2024-10-14 at 9 03 51 PM](https://github.com/user-attachments/assets/1efdea82-974e-4cd5-acfc-130a4946eb68)
![Screen Shot 2024-10-14 at 9 31 27 PM](https://github.com/user-attachments/assets/841267af-de8c-4492-b3ad-56efdb3386e8)
![Screen Shot 2024-10-14 at 9 31 47 PM](https://github.com/user-attachments/assets/9c428646-975b-421b-89bb-1fd17e198227)
![Screen Shot 2024-10-14 at 9 32 26 PM](https://github.com/user-attachments/assets/ce801671-be88-4c2e-8dfc-1606cfd652b1)
![Screen Shot 2024-10-14 at 9 38 42 PM](https://github.com/user-attachments/assets/cbde2baa-68ef-4713-a1ee-13113972fa6f)
![Screen Shot 2024-10-14 at 9 39 24 PM](https://github.com/user-attachments/assets/d946b9d7-b24e-4b70-843f-b54c7bd46c45)
![Screen Shot 2024-10-14 at 9 40 36 PM](https://github.com/user-attachments/assets/368cd8dc-436d-4a82-a6ca-6e414522bf02)
![Screen Shot 2024-10-14 at 9 42 27 PM](https://github.com/user-attachments/assets/3cb1827f-6514-4db8-a8d1-7683f09b9560)

</p>
<p>
Install Active Directory
—
Login to DC-1 and install Active Directory Domain Services
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Restart and then log back into DC-1 as user: mydomain.com\labuser


</p>
<br />

<p>

  ![Screen Shot 2024-10-14 at 9 14 38 PM](https://github.com/user-attachments/assets/2ab8b650-8d22-4487-bfc9-c6225dfa3cb8)
![Screen Shot 2024-10-14 at 9 15 20 PM](https://github.com/user-attachments/assets/d0839ad6-11c9-4350-b5c2-e66009771087)
![Screen Shot 2024-10-14 at 10 02 20 PM](https://github.com/user-attachments/assets/8ef94717-b37d-41bf-8b1b-32a9be9dbbd0)
![Screen Shot 2024-10-14 at 10 03 02 PM](https://github.com/user-attachments/assets/be8c94c2-e7bc-42d3-9de8-a6d5390f2594)
![Screen Shot 2024-10-14 at 10 04 27 PM](https://github.com/user-attachments/assets/1bf66784-8896-463c-9c2a-da04ed2522e4)
![Screen Shot 2024-10-14 at 10 04 39 PM](https://github.com/user-attachments/assets/c675233d-81b9-4a9a-b360-1a8407a3f1b7)
![Screen Shot 2024-10-14 at 10 05 34 PM](https://github.com/user-attachments/assets/59a3ebb2-7619-49bb-a766-8f4815bfc511)
![Screen Shot 2024-10-14 at 10 05 56 PM](https://github.com/user-attachments/assets/9379bb3d-98d8-4f1f-887b-6ee886a39ea7)
![Screen Shot 2024-10-14 at 10 07 01 PM](https://github.com/user-attachments/assets/5049b7ab-ebaf-4d9b-847a-73941c67903a)
![Screen Shot 2024-10-14 at 10 07 26 PM](https://github.com/user-attachments/assets/6b508827-af09-42c9-b33e-60ab97a59f00)
![Screen Shot 2024-10-14 at 10 07 52 PM](https://github.com/user-attachments/assets/7463a510-7337-41af-9ea9-8163ab7ff3cb)
![Screen Shot 2024-10-14 at 10 09 09 PM](https://github.com/user-attachments/assets/cb167ec7-67f7-4b01-b6c2-2404e3f8ab4b)
![Screen Shot 2024-10-14 at 10 09 43 PM](https://github.com/user-attachments/assets/c5e36f1b-a745-421e-b441-f800647d32b9)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

</p>
<p>
  
![Screen Shot 2024-10-14 at 10 21 08 PM](https://github.com/user-attachments/assets/2a72e48d-29e6-4be8-96d7-f6144dcbfb1a)
![Screen Shot 2024-10-14 at 10 23 51 PM](https://github.com/user-attachments/assets/a450fc39-c6be-4e50-bbf2-2ff5335b9e90)
![Screen Shot 2024-10-14 at 10 24 25 PM](https://github.com/user-attachments/assets/b55b8ee5-f9a7-42c4-859e-40bff551a4df)
![Screen Shot 2024-10-14 at 10 26 17 PM](https://github.com/user-attachments/assets/6f3aa7a0-da71-47df-9f0b-4fb276e59fae)
![Screen Shot 2024-10-14 at 10 24 45 PM](https://github.com/user-attachments/assets/569bed20-6e27-45b0-8df5-69fa8e7fe128)
![Screen Shot 2024-10-14 at 10 26 32 PM](https://github.com/user-attachments/assets/0eb5e7da-3879-421d-b6b4-1057095c9907)
![Screen Shot 2024-10-14 at 10 29 57 PM](https://github.com/user-attachments/assets/50c739d7-5bec-4d87-9ad9-20c3529a3ca7)
![Screen Shot 2024-10-18 at 8 47 01 PM](https://github.com/user-attachments/assets/ae403845-8377-4a76-9efe-afa0956991a1)







