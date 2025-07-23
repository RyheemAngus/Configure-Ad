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
- DNS Management
- Group Policy 

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Azure Infrastructure Setup
- Active Directory Installation
- Client Machine Domain Join
- User Account Management
- Group Policy Configuration
- DNS Record Implementation
- File Share Permissions

<h1>Detailed Deployment Guide</h1>
<p>
<h2>Azure Infrastructure Setup</h2>

Created Resource Group in Azure

Established Virtual Network with appropriate subnet

Deployed two VMs:
<p>
<img width="1044" height="936" alt="Image" src="https://github.com/user-attachments/assets/25809aad-45e9-4c5b-bada-4f3a98298284" />
</p>
DC-1 (Windows Server 2022) - Domain Controller

Client-1 (Windows 10) - Client Machine

- Configured static private IP for DC-1
- Set Client-1's DNS to point to DC-1's private IP
<p>
<img width="1368" height="1011" alt="Image" src="https://github.com/user-attachments/assets/d7021002-14ae-4658-ba58-12c7d328d1e0" />
</p>
Disabled Windows Firewall on DC-1 for initial testing

Verified network connectivity between VMs
<p>
<img width="590" height="610" alt="Image" src="https://github.com/user-attachments/assets/aa9ac1ab-7794-4c94-a5bf-c81b32158d9b" />
</p>
</p>
<br />

<p>
<h2>Active Directory Installation</h2>
 Logged into DC-1 and installed Active Directory Domain Services
  
 Promoted DC-1 as Domain Controller for new forest: mydomain.com
  <p>
<img width="1110" height="770" alt="Image" src="https://github.com/user-attachments/assets/4f4f4974-e587-43cb-b869-d438490aa450" />
</p>
Created initial OUs:

  - _EMPLOYEES
  - _ADMINS
  - _CLIENTS
<p>
<img width="634" height="878" alt="Image" src="https://github.com/user-attachments/assets/3d1b0dd8-3ef7-4431-9a88-8d7ed387b78c" />
</p>
Created domain admin account (jane_admin) and added to Domain Admins group

Verified domain functionality
<p>
<img width="1596" height="1016" alt="Image" src="https://github.com/user-attachments/assets/e9f0c5a9-0214-4f17-b7cd-9ded9f7284d2" />
</p>
</p>
<br />

<p>
<h2>Client Machine Domain Join</h2>

Configured Client-1's DNS settings to point to DC-1

Joined Client-1 to mydomain.com domain

Verified computer object appeared in ADUC

Moved Client-1 computer object to _CLIENTS OU

Configured Remote Desktop access for domain users
<p>
<img width="1823" height="1009" alt="Image" src="https://github.com/user-attachments/assets/4751744f-d239-49be-862e-fee926484ff8" />
</p>
</p>
<br />

<p>
<h2>User Account Management</h2>

Used PowerShell script to bulk create user accounts
<p>
<img width="2240" height="1260" alt="Image" src="https://github.com/user-attachments/assets/b8db621c-1b0c-40c0-a0a4-b04163f3761e" />
</p>
</p>
<br />

<p>
<h2>Group Policy Configuration</h2>

The user that I will select and use for this will be bed.cow

Configured Account Lockout Policy:
Threshold: 5 attempts
Duration: 30 minutes
<p>
<img width="1210" height="842" alt="Image" src="https://github.com/user-attachments/assets/8481d3a9-82d4-425b-a125-b1fcd754dc21" />
</p>
Tested lockout by intentionally entering wrong password
<p>
<img width="880" height="759" alt="Image" src="https://github.com/user-attachments/assets/ac87f13a-f921-41a8-83bd-2fbeb42e1790" />
</p>
Verified lockout in Event Viewer

Unlocked account and reset password
<p>
<img width="850" height="618" alt="Image" src="https://github.com/user-attachments/assets/9a115166-25b7-4299-b0a0-f33cdda96630" />
</p>
</p>
<br />

<p>
<h2>DNS Record Implementation</h2>

Created A-record for "mainframe" pointing to DC-1's IP
<p>
<img width="683" height="1217" alt="Image" src="https://github.com/user-attachments/assets/6882b315-ec68-4eaf-aad2-bfe90f170b56" />
</p>
Verified ping and nslookup worked from Client-1

Demonstrated DNS cache behavior:

Changed A-record to point to 8.8.8.8
<p>
<img width="667" height="336" alt="Image" src="https://github.com/user-attachments/assets/741f7f93-d299-430c-a551-6caed79422ad" />
</p>
Observed cached resolution before flush

Used ipconfig /flushdns to clear cache

Verified new resolution

- Created CNAME record "search" pointing to www.google.com
- Verified resolution worked from Client-1
<p>
<img width="468" height="591" alt="Image" src="https://github.com/user-attachments/assets/b05444cb-9b35-4044-a192-18e9cf00963d" />
</p>
</p>
<br />

<p>
<h2>File Share Permissions</h2>

Created shared folders on DC-1:

Created read-access (Domain Users: Read)

Created write-access (Domain Users: Read/Write)

Created no-access (Domain Admins only)

Created accounting (ACCOUNTANTS group: Read/Write)

Created ACCOUNTANTS security group
<p>
<img width="1325" height="849" alt="Image" src="https://github.com/user-attachments/assets/7ef2bae6-5e50-462e-bb79-89e3a8dbfc33" />
</p>
Tested access:

Regular user could access read-access and write-access

Regular user couldn't access no-access or accounting
<p>
<img width="1444" height="763" alt="Image" src="https://github.com/user-attachments/assets/1910dbb5-a6aa-4386-8736-8688d01e4605" />
</p>
After adding user to ACCOUNTANTS group, access to accounting was granted
<p>
<img width="1229" height="692" alt="Image" src="https://github.com/user-attachments/assets/d1cef1a8-78c7-45da-bff2-f5bba4961dac" />
</p>
</p>
<br />
