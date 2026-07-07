<img width="588" height="330" alt="WhatsApp Image 2026-07-07 at 10 47 58" src="https://github.com/user-attachments/assets/b669e404-dc73-43ee-ac7f-160735db617b" />

# Active Directory Home Lab
📌 Project Overview
This project demonstrates the deployment and administration of an Active Directory environment using Windows Server in a virtual lab. The objective was to gain practical experience managing a Windows domain, creating user accounts, configuring organizational units (OUs), applying Group Policy, and understanding how Active Directory is used in enterprise environments.
This lab simulates the responsibilities of an IT Support Technician or Junior System Administrator in a real-world business network.

⸻

🎯 Objectives
* Install and configure Active Directory Domain Services (AD DS)
* Promote a Windows Server to a Domain Controller
* Create a new Active Directory domain
* Join a client computer to the domain
* Configure Organizational Units (OUs)
* Create and manage users
* Explore Group Policy management

⸻

🛠️ Technologies Used
* Windows Server 2022 & Windows Pro 11
* DNS
* Active Directory Domain Services (AD DS)
* PowerShell 

⸻

##🔹Phase 1: Foundation – Environment Provisioning & Connectivity.

I established the core infrastructure for the lab environment within the Microsoft Azure ecosystem. My primary objective was to create a logically isolated network environment and deploy two virtual machines: a Windows Server 2022 virtual machine acting as the Domain Controller and a Windows 11 Pro virtual machine functioning as a Client workstation. I performed key configurations by optimizing security settings on the Domain Controller through altered firewall profiles and established internal network connectivity by configuring the Client workstation to use the Domain Controller's private IP as its DNS server, ensuring readiness for Active Directory domain services creation.
