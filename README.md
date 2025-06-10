# On-Premises Active Directory in Azure
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
- Azure Virtual Networking
- Network Security Groups

<h2>Operating Systems Used </h2>

- Windows Server 2022 (Domain Controller)
- Windows 10 (21H2) (Client Machine)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Azure Resources and Configure Networking
- Set Up Domain Controller (Windows Server 2022)
- Create and Configure Active Directory Users
- Join Client Machine to Domain
- Test and Validate Functionality

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<strong>1. Azure Resource Provisioning</strong>
<ol>
<li>Create Resource Group in Azure Portal</li>
<li>Deploy Windows Server 2022 VM (Domain Controller)</li>
<li>Deploy Windows 10 VM (Client Machine)</li>
<li>Configure Virtual Network with appropriate subnetting</li>
<li>Set up Network Security Groups for proper traffic filtering</li>
</ol>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<strong>2. Domain Controller Configuration</strong>
<ol>
<li>Connect to Windows Server VM via RDP</li>
<li>Install Active Directory Domain Services role</li>
<li>Promote server to Domain Controller (use PowerShell or GUI)</li>
<li>Create new forest (e.g., "yourdomain.local")</li>
<li>Configure DNS settings and reverse lookup zones</li>
<li>Set up DHCP scope if needed</li>
</ol>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<strong>3. Active Directory Management</strong>
<ol>
<li>Create Organizational Units (OUs) for structure</li>
<li>Create user accounts and security groups</li>
<li>Configure Group Policy Objects (GPOs) for:
  <ul>
    <li>Password policies</li>
    <li>Desktop restrictions</li>
    <li>Security settings</li>
  </ul>
</li>
<li>Test account creation and authentication</li>
</ol>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Client Configuration"/>
</p>
<p>
<strong>4. Client Machine Setup</strong>
<ol>
<li>Configure client VM to use DC as DNS server</li>
<li>Join Windows 10 machine to the domain</li>
<li>Verify domain join with <code>systeminfo</code> command</li>
<li>Test user logins with created AD accounts</li>
<li>Verify Group Policy application with <code>gpresult /r</code></li>
</ol>
</p>
<br />
