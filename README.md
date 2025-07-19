<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines, Vnets, NSGs)
- Remote Desktop
- Active Directory Domain Services
- PowerShell 7.x
- Wireshark 4.0

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
- Ubuntu Linux 20.04 LTS

<h2>Implementation Steps</h2>

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

Windows 10 Client VM

Setting	Value
Name	win10-client
Image	Windows 10 Pro, 21H2
VNet	Lab2-Vnet
NSG Rules	Auto-created RDP (3389)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Ubuntu Linux VM

Setting	Value
Name	ubuntu-test
Authentication	Username/Password
IP Assignment	Dynamic (10.0.0.x)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />

<p>
<h2>Tool Installation & Network Validation</h2>

PowerShell 7 Installation

powershell
winget install --id Microsoft.PowerShell --accept-package-agreements

Verification:
$PSVersionTable.PSVersion
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Wireshark Installation

powershell
choco install wireshark -y
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Wireshark capturing ICMP traffic between VMs
Filter: icmp && ip.addr == 10.0.0.4 && ip.addr == 10.0.0.5
Ping Tests
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />
