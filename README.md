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
<p>
<img width="1370" height="495" alt="Image" src="https://github.com/user-attachments/assets/c1832eb6-22b4-4775-ae04-5eacc650db65" />
</p>
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
<img width="1052" height="725" alt="Image" src="https://github.com/user-attachments/assets/819b044d-a9e4-492b-9fbc-738118378cfc" />
</p>

Ubuntu Linux VM

Setting	Value
Name	ubuntu-test
Authentication	Username/Password
IP Assignment	Dynamic (10.0.0.x)
<p>
<img width="1353" height="998" alt="Image" src="https://github.com/user-attachments/assets/0ad0c7f5-ea5c-4081-8d8e-de4bb8850e40" />
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

Wireshark Installation

powershell
choco install wireshark -y
<p>
<img width="1145" height="647" alt="Image" src="https://github.com/user-attachments/assets/3519e008-9c0c-4d63-a5ff-dd635a827d1f" />
</p>

Wireshark capturing ICMP traffic between VMs
Filter: icmp && ip.addr == 10.0.0.4 && ip.addr == 10.0.0.5
Ping Tests
<p>
<img width="2231" height="861" alt="Image" src="https://github.com/user-attachments/assets/0905cf50-139c-4761-9cfa-a807b1cb5afa" />
</p>
</p>
<br />
