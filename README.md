<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

Create Azure Resource Group and Virtual Network
Deploy Windows Server 2022 VM 
Deploy Windows 10 VM 
Configure Active Directory Domain Services

<h1>Deployment and Configuration Steps</h1>

<p>
<h2>Azure VM Deployment</h2>

Create a Resource Group

Navigate to Azure Portal.
Resource Groups → Create → Name: Networking-Lab-RG → Region: (East US 2).

Create Virtual Network (VNet)

During Windows Server VM creation:
Virtual Network: Create new (AD-VNet)
Subnet: Default (10.0.0.0/24)
</p>
<br />

<p>
<h2>Virtual Machine Deployment</h2>

Deploy Windows Server 2022 (Domain Controller)

Virtual Machines → Create → Azure Virtual Machine
Name: window-vm
Image: Windows Server 2022 Datacenter
Size: Standard_D2s_v3 (2 vCPUs, 8GB RAM recommended)
Username/Password: AdminUser/ComplexPassword123!
Networking:
Virtual Network: AD-VNet (created above)
Public IP: Enabled (for initial RDP access)

Deploy Windows 10 (Client Machine)

Repeat VM creation with:
Name: Lab2-Vnet
Image: Windows 10 Pro, 21H2
Virtual Network: AD-VNet
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
