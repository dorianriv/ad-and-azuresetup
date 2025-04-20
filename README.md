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
- Name it: DC-1
- Select Windows Server 2022: Azure Edition - x64 Gen2 as the image 

![image](https://github.com/user-attachments/assets/3f72ac12-1e33-4c7a-9bb5-fa080e4e96e7)

<p><strong>NOTE:</strong> Be sure to select a minimum of 2 vCPUs and 16 GiB of memory. Also, make note of the virtual network (VNet) created for the VM.</p>

![image](https://github.com/user-attachments/assets/44bbf2cb-67f0-4b8f-8e1a-02565201d11f)

<h3>&#9333; Set the Domain Controller's Private IP to static</h3>

- After the VM has been deployed, navigate to the VM's overview page and click on 'Network settings' in the left-hand menu.

![image](https://github.com/user-attachments/assets/8d3f9e05-d270-4ba6-8215-57fa5bb4d572)

- Select Network Interface Card -> IP configurations -> ipconfig1 and set Private IP address allocation to static.

![image](https://github.com/user-attachments/assets/e5d5f5a8-357c-42a8-af73-4abac75d07cb)

<h3>&#9334; Create the client VM</h3>

- Next, create a new virtual machine named Client-1. Choose Windows 10 as the image, and ensure the VM is configured with at least 2 vCPUs and 16 GiB of memory.

![image](https://github.com/user-attachments/assets/44ab5b02-e082-410e-931f-e9287aeaed23)

<p><strong>NOTE:</strong> Be sure to select the same resource group and virtual network used for the DC-1 VM.</p>

![image](https://github.com/user-attachments/assets/d49543ab-1d95-4e66-88a3-55794e33d0b3)

- Now finalize everything and wait for its deployment.

<h3>&#9335; Ensure connectivity between Domain Controller and Client</h3>

<p>
To verify connectivity between the two virtual machines, we’ll initiate a ping from the client to the domain controller.
</p>

- First, login to Client-1 using its public ip address and remote desktop

![image](https://github.com/user-attachments/assets/9c837a2b-3e0f-43c9-9d34-2d7c99acea4a)

![image](https://github.com/user-attachments/assets/80955032-b1b1-4c52-aaec-fe7a6ddd18ff)

<p>
Locate DC-1’s private IP address in the Azure Portal and copy it. Then, switch to Client-1, open the terminal, and enter the command: ping [DC-01 private IP address].
</p>

![image](https://github.com/user-attachments/assets/6dd5c51e-fc1e-4bbb-baaa-0b936b085bd7)

<p>
Notice that the ping request times out—this occurs because ICMPv4 traffic is blocked by default on DC-1’s firewall. To allow Client-1’s ping to go through, we’ll need to enable inbound ICMP traffic.
</p>

<p>
Log in to DC-1 via Remote Desktop, open Windows Defender Firewall, and navigate to Advanced Settings. Disable the firewall for the Domain, Private, and Public profiles. Click Apply, then OK to save the changes.
</p>

![image](https://github.com/user-attachments/assets/4fe9e17a-6fa1-4b75-acd1-7f970f2b0c40)

![image](https://github.com/user-attachments/assets/5d4e765f-20fa-4d05-a238-b1732ac59495)

<p>
Now once the traffic has been enabled, you can check back with Client-1 and notice that the ping is now successful.
</p>

<h2>Final Thoughts</h2>

<p>
We’ve finished setting up the foundation for our Azure and Active Directory project series. By configuring two virtual machines, a Domain Controller and a Client, we’ve created the base environment for what’s to come. This project covered remote access setup and a quick look at network traffic between the machines. With this groundwork in place, we’re ready to move on to more advanced configurations and hands-on scenarios in Azure and Active Directory.
</p>
