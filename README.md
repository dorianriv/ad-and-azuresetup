<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Project Logo"/>
</p>

<h1>Active Directory Setup & Network Traffic Analysis with Azure VMs</h1>

<p>
This project kicks off a hands-on lab series focused on deploying Active Directory in a simulated Azure environment. In this first part, we’ll build the core infrastructure needed to replicate how AD works in a real enterprise network.
</p>

<h2>Overview</h2>

<p>
This project involves setting up two virtual machines in Azure, each with a specific role. One acts as the Domain Controller, while the other functions as a client machine for testing connectivity and interaction.
</p>

<h2>Key Objectives</h2>

<h3>Virtual Machine Setup</h3>

- Configure the Domain Controller virtual machine
- Establish the Client virtual machine

<h3>Remote Connectivity</h3>

- Enable a connection using Remote Desktop 

<h3>Network Verification</h3>

- Perform a basic inspection of the network traffic between the Domain Controller and Client virtual machines

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)  
- Remote Desktop  
- Active Directory Domain Services 
- PowerShell

<h2>Operating Systems Used</h2>

- Windows Server 2022  
- Windows 10  

<h2>Configuration Steps</h2>

<h3>&#9332; Create the Domain Controller</h3>

- Create a virtual machine on Azure 
- Name it: DC-01
- Select Windows Server 2022: Azure Edition - x64 Gen2 as the image 

<p><img src="[Insert Image URL]" alt="Screenshot of VM setup"/></p>

<p><strong>NOTE:</strong> Ensure resources (CPU/RAM) and network settings are appropriate for this lab.</p>

<h3>&#9333; Set the [Role A] Private IP to Static</h3>

- Navigate to Networking  
- Open IP configuration settings  
- Change Private IP to static  

<p><img src="[Insert Image URL]" alt="Screenshot of static IP setup"/></p>

<h3>&#9334; Create the [Role B] Virtual Machine</h3>

- Repeat VM creation  
- Name it: [VM Name]  
- Use [OS Image]  
- Assign to same vNet and resource group as [Role A]  

<p><img src="[Insert Image URL]" alt="Screenshot of second VM setup"/></p>

<h3>&#9335; Verify Connectivity Between the Two VMs</h3>

- Log into [Role B] VM using Remote Desktop  
- Use `ping` or other network command to test communication with [Role A]  
- Troubleshoot any firewall or security group rules if traffic is blocked  

<p><img src="[Insert Image URL]" alt="Screenshot of ping test"/></p>

<p><strong>TIP:</strong> Check firewall settings on [Role A] and enable ICMP if needed.</p>

<h2>Final Thoughts</h2>

<p>
This lab lays the groundwork for [insert future goals or follow-up labs]. It covers deploying and connecting two basic systems, validating communication, and addressing early-stage network rules. Future stages may explore advanced services, automation, or security hardening based on this setup.
</p>
