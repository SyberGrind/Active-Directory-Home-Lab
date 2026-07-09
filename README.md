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

⸻
>
<br>

**Step 1: I opened the Resource Manager in the Azure Portal to view my existing resource groups.**
<br>
<img width="1366" height="768" alt="Step 1  Resource Group Manager Portal" src="https://github.com/user-attachments/assets/c072ace4-753c-479b-80cc-a4b65a8aa158" />
>
<br>

**Step 2: I navigated to the Create a resource group screen.**
<br>
<img width="1366" height="768" alt="Step 2  Resource Group Creation Portal" src="https://github.com/user-attachments/assets/d255649a-78ae-4216-b0b8-93e3177198b5" />
>
<br>

**Step 3: I selected East Asia as the region and named the new resource group ADLab.**
<br>
<img width="1366" height="768" alt="Step 3  Resource Group Creation Portal - Selecting East Asia Zone   Naming it ADLab" src="https://github.com/user-attachments/assets/c95b35fa-e95e-4e1a-bbf7-9a683110b39f" />
>
<br>

**Step 4: I reviewed the configuration to confirm the name ADLab and the East Asia region.**
<br>
<img width="1366" height="768" alt="Step 4  Confirmation of East Asia Zone   ADLab name of Resouce Group" src="https://github.com/user-attachments/assets/24022d28-54e0-466c-a869-9908207fa402" />
>
<br>

**Step 5: I verified that the ADLab resource group was successfully created.**
<br>
<img width="1366" height="768" alt="Step 5   Resource Group ADLab Succesfully Created" src="https://github.com/user-attachments/assets/62219955-776c-44c2-ac95-53084197141b" />
>
<br>

**Step 6: I navigated to the Virtual Network creation portal.**
<br>
<img width="1366" height="768" alt="Step 6  Virtual Network Creation Portal" src="https://github.com/user-attachments/assets/f94a86ab-2f62-43fe-958a-e02a738a63d8" />
>
<br>

**Step 7: I selected the ADLab resource group to associate the new network.**
<br>
<img width="1366" height="768" alt="Step 7  Adding  Virtual Network to ADLab Resource Group" src="https://github.com/user-attachments/assets/040c8f64-0a8e-427e-ade0-ad0c96aac532" />
>
<br>

**Step 8: I named the virtual network ADVNET and ensured it was assigned to the East Asia region.**
<br>
<img width="1366" height="768" alt="Step 8  Naming Virtual Network ADVNET   adding it to East Asia Zone" src="https://github.com/user-attachments/assets/9abfd678-6c25-473a-b811-efc69e6e6d83" />
>
<br>

**Step 9: I reviewed the settings and initiated the creation of ADVNET.**
<br>
<img width="1366" height="768" alt="Step 9  Creating Virtual Newtwork ADVNET" src="https://github.com/user-attachments/assets/3595ff2e-f7ce-4f45-b06c-e650377fd06f" />
>
<br>

**Step 10: I confirmed that the virtual network ADVNET was successfully created.**
<br>
<img width="1366" height="768" alt="Step 10  Succefully Created Virtual Network ADVNET" src="https://github.com/user-attachments/assets/f6f9d15c-4743-4411-8660-3fa54dece8ba" />
>
<br>

**Step 11: I accessed the Virtual Machine creation portal.**
<br>
<img width="1366" height="768" alt="Step 11  Virtual Machine Creation Portal" src="https://github.com/user-attachments/assets/8ce62b90-9966-447b-a853-92676ea958d2" />
>
<br>

**Step 12: I began the configuration process for my first virtual machine.**
<br>
<img width="1366" height="768" alt="Step 12  Virtual Machine Creation Portal" src="https://github.com/user-attachments/assets/9c3ed475-0b89-4405-8869-f85936635f2b" />
>
<br>

**Step 13: I continued through the Virtual Machine deployment wizard.**
<br>
<img width="1366" height="768" alt="Step 13  Virtual Machine Creation Portal" src="https://github.com/user-attachments/assets/4e331d4a-a9ac-4a1b-80e3-c66b4d794514" />
>
<br>

**Step 14: I set the Resource Group to ADLab, the region to East Asia, and named the VM Domain-Controller.**
<br>
<img width="1366" height="768" alt="Step 14  Selecting ADLab as resource group, East Asia as zone and naming Domain Controller for Windows VM" src="https://github.com/user-attachments/assets/bddefe72-0e8e-453e-83ca-7c2f4a35c792" />
>
<br>

**Step 15: I selected the Windows Server 2022 image and the appropriate instance size.**
<br>
<img width="1366" height="768" alt="Step 15  Selecting Image   Size for Windows VM" src="https://github.com/user-attachments/assets/94332136-cc19-400a-8162-1217c9060c30" />
>
<br>

**Step 16: I defined the administrative Username and Password for the Domain Controller VM.**
<br>
<img width="1030" height="1280" alt="Step 16  Username   Passowrd for Windows VM" src="https://github.com/user-attachments/assets/7fd3d024-f207-4d79-adb6-6f39dca380cf" />
>
<br>

**Step 17: I input and confirmed the secure credentials for the Domain-Controller.**
<br>
<img width="1366" height="768" alt="Step 17  Inputting Username   Password for Windows VM" src="https://github.com/user-attachments/assets/1fa48548-b7e3-49d6-b846-1d6c50866874" />
>
<br>

**Step 18: I selected ADVNET as the Virtual Network for the Domain-Controller.**
<br>
<img width="1366" height="768" alt="Step 18  Selecting ADVNET as Network for Windows VM" src="https://github.com/user-attachments/assets/fbfe6fad-3789-4e16-93b2-c09274813c09" />
>
<br>

**Step 19: I completed the validation check to ensure the Domain-Controller was ready for deployment.**
<br>
<img width="1366" height="768" alt="Step 19  Validation for Windows VM for creation" src="https://github.com/user-attachments/assets/c12f4cba-86f7-44d1-bcaa-011f3df57c01" />
>
<br>

**Step 20: I confirmed that the Domain-Controller virtual machine was successfully created.**
<br>
<img width="1366" height="768" alt="Step 20  Domain Controller Windows VM Created" src="https://github.com/user-attachments/assets/37441618-f27b-486f-a2f5-0168fc52267b" />
>
<br>

**Step 21: I accessed the Virtual Machine creation portal to deploy my second VM.**
<br>
<img width="1366" height="768" alt="Step 21  Virtual Machine Creation Portal for Client - 1 VM" src="https://github.com/user-attachments/assets/cf17bdca-4654-42f1-82c9-1e1ba09362fb" />
>
<br>

**Step 22: I set the Resource Group to ADLab, the region to East Asia, and named the VM Client-1.**
<br>
<img width="1366" height="768" alt="Step 22  Selecting ADLab as resource group, East Asia as zone and naming Client - 1 for 2nd Windows VM" src="https://github.com/user-attachments/assets/4c045d9d-cae1-4df0-8ad1-5197cbd13960" />
>
<br>

**Step 23: I selected the Windows 11 Pro image and appropriate size for the client workstation.**
<br>
<img width="1366" height="768" alt="Step 23  Selecting Image   Size for 2nd Windows VM" src="https://github.com/user-attachments/assets/bb4f2a8c-1d5e-4c57-bb87-1c2384695cf6" />
>
<br>

**Step 24: I defined the administrative Username and Password for the Client-1 VM.**
<br>
<img width="995" height="1600" alt="Step 24  Username   Passowrd for 2nd Windows VM" src="https://github.com/user-attachments/assets/b6a22f0e-f848-43da-84ce-5b637b231956" />
>
<br>

**Step 25: I input and confirmed the secure credentials for the Client-1 VM.**
<br>
<img width="1366" height="768" alt="Step 25  Inputting Username   Password for 2nd Windows VM" src="https://github.com/user-attachments/assets/ce4b2105-4c80-45ae-8321-03dc7a51efcc" />
>
<br>

**Step 26: I selected ADVNET as the Virtual Network for the Client-1 VM.**
<br>
<img width="1366" height="768" alt="Step 26  Selecting ADVNET as Virtual Network for 2nd Windows VM" src="https://github.com/user-attachments/assets/0665d7c4-cc22-4aa2-aa7c-6605db1e7521" />
>
<br>

**Step 27: I ran the validation check to ensure Client-1 was ready for deployment.**
<br>
<img width="1366" height="768" alt="Step 27  Validation for 2nd Windows VM for creation" src="https://github.com/user-attachments/assets/96d28360-d068-453f-bdcc-2c96cfd79abe" />
>
<br>

**Step 28: I confirmed that the Client-1 virtual machine was successfully created.**
<br>
<img width="1366" height="768" alt="Step 28  Client - 1 Windows VM Created" src="https://github.com/user-attachments/assets/c2bc8ee2-d703-46e7-992b-54a9c18b4b0b" />
>
<br>

**Step 29: I located and copied the Public IP Address 104.214.185.151 assigned to the Domain-Controller VM.**
<br>
<img width="1366" height="768" alt="Step 29  Copying Domain Controller Public IP Address for Remote Desktop" src="https://github.com/user-attachments/assets/5745a9da-f905-4058-98ea-9702a32592d1" />
>
<br>

**Step 30: I launched Remote Desktop Connection and initiated a session using the copied Public IP Addresss 104.214.185.151.**
<br>
<img width="1366" height="768" alt="Step 30  Connecting to Domain Controller on Remote Desktop using Public IP" src="https://github.com/user-attachments/assets/cd76641f-0357-4ef9-932a-3ac3aa335924" />
>
<br>

**Step 31: I entered my administrative credentials to authenticate the remote session.**
<br>
<img width="1366" height="768" alt="Step 31  Inputting password for Domain Controller on Remote Desktop" src="https://github.com/user-attachments/assets/072d1102-43e4-4161-9a50-e53b8f7e74a5" />
>
<br>

**Step 32: I confirmed successful login and access to the Domain-Controller desktop.**
<br>
<img width="1366" height="768" alt="Step 32  Successfull Login to Domain Controller Windows VM" src="https://github.com/user-attachments/assets/1765b84a-668d-459f-82e3-0e9055dfcb07" />
>
<br>

**Step 33: I pressed Windows + R and typed wf.msc to launch the Windows Defender Firewall.**
<br>
<img width="1366" height="768" alt="Step 33  Openning Run program to launch Windows defender firewall" src="https://github.com/user-attachments/assets/beab9c46-00c4-40ab-950d-4b354d8051ed" />
>
<br>

**Step 34: I verified that the Windows Defender Firewall with Advanced Security console had opened.**
<br>
<img width="1366" height="768" alt="Step 34  Succesfull launch of Windows defender firewall" src="https://github.com/user-attachments/assets/98dc350a-de87-4c8a-ad5d-3c3d38260418" />
>
<br>

**Step 35: I accessed the Properties window and set the Domain Profile firewall state to off.**
<br>
<img width="1366" height="768" alt="Step 35  Acessing Windows defender firewall properties to alter domain profile to firewall state off" src="https://github.com/user-attachments/assets/cd1d3ac3-ddb2-49d4-84f8-aa77b43bba38" />
>
<br>

**Step 36: In the same Properties window, I set the Private Profile firewall state to off.**
<br>
<img width="1366" height="768" alt="Step 36  Acessing Windows defender firewall properties to alter private profile to firewall state off" src="https://github.com/user-attachments/assets/de6c36d8-a517-4a4a-ae3e-270f2a97c6be" />
>
<br>

**Step 37: I set the Public Profile firewall state to off.**
<br>
<img width="1366" height="768" alt="Step 37  Acessing Windows defender firewall properties to alter public profile to firewall state off" src="https://github.com/user-attachments/assets/f5e20376-825c-48fb-9d16-a2d0f0fd08a1" />
>
<br>

**Step 38: I confirmed and applied the changes to the firewall profiles.**
<br>
<img width="1366" height="768" alt="Step 38  Final Confirmation of Windows Defender Firewall Properties change" src="https://github.com/user-attachments/assets/531d0706-f2e4-412e-b4c2-8668ad7e84a6" />
>
<br>

**Step 39: I navigated to the Network Interface settings for the Domain-Controller and changed the Private IP allocation to Static.**
<br>
<img width="1366" height="768" alt="Step 39  Configuring Private IP Address of Domain Controller VM to static" src="https://github.com/user-attachments/assets/f426dcb9-6066-4651-a016-6abdafd2cda3" />
>
<br>

**Step 40: I verified that the internal IP address (10.0.0.4) was successfully set to Static.**
<br>
<img width="1366" height="768" alt="Step 40  Confirmation Domain Controller private IP address is static" src="https://github.com/user-attachments/assets/278c9322-feff-4451-89c0-2893f0e512b6" />
>
<br>

**Step 41: I copied the Private IP Address of the Domain-Controller for my next configuration step.**
<br>
<img width="1366" height="768" alt="Step 41  Copying Domain Controller Private IP Address" src="https://github.com/user-attachments/assets/a26493aa-aac4-45af-90a4-16d4d1045adb" />
>
<br>

**Step 42: I navigated to the Network settings for the Client-1 VM in the Azure portal.**
<br>
<img width="1366" height="768" alt="Step 42  Acessing Client - 1 VM Network Settings" src="https://github.com/user-attachments/assets/8162a511-1797-4fef-8b1e-b11cea002f99" />
>
<br>

**Step 43: I accessed the DNS server settings for the Client-1 network interface.**
<br>
<img width="1366" height="768" alt="Step 43  Accessing Client - 1 VM DNS server settings" src="https://github.com/user-attachments/assets/26bde0c8-d831-431c-93a3-0d30e540e7f6" />
>
<br>

**Step 44: I changed the DNS setting to Custom and entered the Domain-Controller’s private IP (10.0.0.4).**
<br>
<img width="1366" height="768" alt="Step 44  Altering Client - 1 VM Settings to Custom   using private ip of Domain controller" src="https://github.com/user-attachments/assets/082adbd9-d207-413d-8c3f-52ded8eb2393" />
>
<br>

**Step 45: I saved the changes and confirmed the DNS server update for Client-1.**
<br>
<img width="1366" height="768" alt="Step 45  Confirmation change of client - 1 VM dns server settings" src="https://github.com/user-attachments/assets/965ab40f-bfed-49f2-8139-81b13a9c6b9e" />
>
<br>

**Step 46: I located and copied the Public IP Address of the Client-1 VM.**
<br>
<img width="1366" height="768" alt="Step 46  Copying Public IP address of Client - 1 VM" src="https://github.com/user-attachments/assets/a88d337d-a6d9-4272-a81d-b8a72970914a" />
>
<br>

**Step 47: I opened Remote Desktop, connected using the Client-1 Public IP Addresss 104.214.179.243, and input my credentials.**
<br>
<img width="1366" height="768" alt="Step 47  Logging in to Client - 1 VM - inputting password" src="https://github.com/user-attachments/assets/2917b81d-dde0-4272-9447-a07ac7119921" />
>
<br>

**Step 48: I confirmed successful launch and login to the Client-1 desktop.**
<br>
<img width="1366" height="768" alt="Step 48  Successfull launch of Client - 1 VM" src="https://github.com/user-attachments/assets/fc1d37fd-26b4-47e1-b470-d667276e94f2" />
>
<br>

**Step 49: I opened Settings from the Start menu to verify the system identity.**
<br>
<img width="1366" height="768" alt="Step 49  Comfirming again i have logged in Client - 1 VM by clicking windows key   accessing settings" src="https://github.com/user-attachments/assets/42a78e4e-b7f1-49c2-a69c-905ae1c3225d" />
>
<br>

**Step 50: I searched for and launched Windows PowerShell with administrative privileges.**
<br>
<img width="1366" height="768" alt="Step 50  Launching Windows Powershell" src="https://github.com/user-attachments/assets/82f91d28-5816-4ae7-8159-8207725b37f3" />
>
<br>

**Step 51: At the PowerShell prompt, I typed ping 10.0.0.4 to test the connection to the Domain Controller.**
<br>
<img width="1366" height="768" alt="Step 51  Successfull launch of Windows Powersshell   prompt to ping private ip address to check it is using Domain Controller as its DNS Server" src="https://github.com/user-attachments/assets/5a0b4ae8-ed89-43e9-9a54-06d7e985f904" />
>
<br>

**Step 52: I observed the successful ping replies to confirm network connectivity.**
<br>
<img width="1366" height="768" alt="Step 52  Succesfull ping to check Client - 1 VM is using Domain Controller as its DNS Server" src="https://github.com/user-attachments/assets/74b1ec45-1f98-4449-9bc1-6e9af2096d4a" />
>
<br>

**Step 53: I executed the ipconfig /all command to verify that the Client-1 VM was correctly using the Domain Controller for DNS resolution.**
<br>
<img width="1366" height="768" alt="Step 53  Succesfull prompt of ipconfig all command to check if Client - 1 VM is using Domain Controller as its DNS Server" src="https://github.com/user-attachments/assets/9d3f000b-5951-43e8-8496-922540b20060" />
>
<br>
⸻
<br>

##🔹Phase 2: Active Directory Domain Services Configuration.

In this phase, I configured the Domain Controller and established a formal domain infrastructure within my Azure environment. My primary objective was to deploy and promote the Active Directory Domain Services Configuration role to create a new forest named mydomain.com. Following the domain promotion, I implemented organizational security and administration by creating custom organizational units (Employees/Staff and Admins) and provisioning an administrative user, Siyolo_Admin, with delegated domain administrative privileges. Finally, I successfully joined the Client-1 VM to the mydomain.com domain, confirming full connectivity and integration within the domain environment.
>
<br>
⸻

**Step 54: I went back to my Domain Controller virtual machine to set up Active Directory.**
<br>
<img width="1366" height="768" alt="Step 56  Succesfull launch of Domain Controller VM" src="https://github.com/user-attachments/assets/85241414-f962-4114-990d-bb1bd382e46b" />
>
<br>

**Step 55: I opened the Server Manager to begin the process of setting up Active Directory.**
<br>
<img width="1366" height="768" alt="Step 57  Prompt of Server Manager to set up Active Directory" src="https://github.com/user-attachments/assets/e17b6ee5-206c-43ed-a724-4ce5be37333e" />
>
<br>

**Step 56: I verified the successful launch of Server Manager.**
<br>
<img width="1366" height="768" alt="Step 58  Successful launch of Server Manager on Domain Controller" src="https://github.com/user-attachments/assets/10154a93-2d9e-401f-8903-5a0f68c3f73f" />
>
<br>

**Step 57: I initiated the Add Roles & Features wizard within Server Manager.**
<br>
<img width="1366" height="768" alt="Step 59  Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/b17f9790-9971-4a67-84be-5bd1f333f73c" />
>
<br>

**Step 58: I navigated through the initial screens of the Add Roles & Features wizard.**
<br>
<img width="1366" height="768" alt="Step 60   Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/451a2b76-bd08-4421-a9d7-d69ddec49381" />
>
<br>

**Step 59: I continued the setup process for the server roles.**
<br>
<img width="1366" height="768" alt="Step 61   Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/74229cda-b0c2-4670-9876-a3a1ae93628d" />
>
<br>

**Step 61: I continued the setup process for the server roles.**
<br>
<img width="1366" height="768" alt="Step 62   Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/be5c75c5-9720-41c4-8594-0cede5d78658" />
>
<br>

**Step 62: I selected Active Directory Domain Services as the required role.**
<br>
<img width="1366" height="768" alt="Step 63  Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/84bccf2a-eeaf-450e-a3cd-c968b5a63970" />
>
<br>

**Step 63: I confirmed the inclusion of required management tools for Active Directory Services.**
<br>
<img width="1366" height="768" alt="Step 64  Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/04d26928-3f72-4074-86da-2d4c1f8d5b43" />
>
<br>

**Step 64: I verified the successful completion of the Add Roles & Features installation.**
<br>
<img width="1366" height="768" alt="Step 65   Successful Active Directory Setup - Add Roles   Features" src="https://github.com/user-attachments/assets/fa4e181d-f846-4e78-97f6-9704c9259715" />
>
<br>

**Step 65: I proceeded to the Active Directory Configuration stage to promote the server.**
<br>
<img width="1366" height="768" alt="Step 66  Active Diretory Configuration   Installation" src="https://github.com/user-attachments/assets/1ca2d645-b557-484d-b54d-5c0ccc96b21b" />
>
<br>

**Step 66: I selected the option to Add a new forest for the deployment.**
<br>
<img width="1366" height="768" alt="Step 67  Active Diretory Configuration   Installation Adding New Forest" src="https://github.com/user-attachments/assets/395b83ac-c87c-43eb-bbce-aa26e97b604d" />
>
<br>

**Step 67: I specified the forest root domain name as mydomain.com.**
<br>
<img width="1366" height="768" alt="Step 68  Active Diretory Configuration   Installation -  Forest name mydomain com" src="https://github.com/user-attachments/assets/d836449c-cf6e-4c82-88b7-cbf25e1fc594" />
>
<br>

**Step 68: I allowed the wizard to perform the Prerequisites check.**
<br>
<img width="1366" height="768" alt="Step 69  Active Diretory Configuration   Installation - Preresiquisites check" src="https://github.com/user-attachments/assets/c3c04e11-c8de-48a1-819e-c5b1ebc62cd1" />
>
<br>

**Step 69: I proceeded with the installation, which triggered a mandatory reboot of the Domain-Controller.**
<br>
<img width="1366" height="768" alt="Step 70  Active Diretory Configuration   Installation cauing reboot of Domain Controller" src="https://github.com/user-attachments/assets/1c0ace0d-e6c4-44ea-b95b-f1bfbe1e09f7" />
>
<br>

**Step 70: I logged into the Domain-Controller using the new domain credentials (mydomain.com\Domain Controller).**
<br>
<img width="1366" height="768" alt="Step 71  Log in to Domain Controller with new name mydomain com Domain Controller" src="https://github.com/user-attachments/assets/f66eb50c-6915-4f01-8c7d-fd949b0c795c" />
>
<br>

**Step 71: I confirmed a successful login after the Active Directory installation.**
<br>
<img width="1366" height="768" alt="Step 72  Successful login to Domain Controller after setup, configuration   installation of Active Directory" src="https://github.com/user-attachments/assets/9a5239bb-a4df-4dde-8349-bbe2772d82a3" />
>
<br>

**Step 72: I launched Server Manager to confirm the new role status.**
<br>
<img width="1366" height="768" alt="Step 73  Prompt to Launch Server Manager" src="https://github.com/user-attachments/assets/ac1e7a7e-c3b2-419d-bbac-9c9184df2b38" />
>
<br>

**Step 73: I confirmed the successful launch of Server Manager.**
<br>
<img width="1366" height="768" alt="Step 74  Successful Launch of Server Manager" src="https://github.com/user-attachments/assets/10b0da62-597c-4b6f-8d54-7c0170a13a59" />
>
<br>

**Step 74: I accessed the Active Directory Users and Computers (ADUC) tool via the Tools menu.**
<br>
<img width="1366" height="768" alt="Step 75  Accessing ADUC on Server Manager" src="https://github.com/user-attachments/assets/2eb2c360-3eb0-4502-bdd3-7aabc8d3c629" />
>
<br>

**Step 75: I verified the successful launch of Active Directory Users & Computers.**
<br>
<img width="1366" height="768" alt="Step 76  Succesful Launch of ADUC" src="https://github.com/user-attachments/assets/bfe73e05-066f-44b7-8a2e-7b3cad533b1e" />
>
<br>

**Step 76: I prepared to add a new organizational unit (OU) in ADUC.**
<br>
<img width="1366" height="768" alt="Step 77  Adding an organisational unit in ADUC" src="https://github.com/user-attachments/assets/9f571465-1bb0-46ef-b66d-64bdc388f167" />
>
<br>

**Step 77: I created an OU named Employees/Staff.**
<br>
<img width="1366" height="768" alt="Step 78  Adding an organisational unit in ADUC - Employees Staff" src="https://github.com/user-attachments/assets/4f39f770-9564-46d5-a470-cb503e501270" />
>
<br>

**Step 78: I created a second OU named Admins.**
<br>
<img width="1366" height="768" alt="Step 79  Adding an organisational unit in ADUC - Admins" src="https://github.com/user-attachments/assets/d031f823-8802-4a07-8794-3475562b95ed" />
>
<br>

**Step 79: I initiated the creation of a new user Siyolo Kamisa/Siyolo_Admin within the Admins OU.**
<br>
<img width="1366" height="768" alt="Step 80  Creating a new user in ADUC within Admins" src="https://github.com/user-attachments/assets/c6507690-8d95-46cb-b8d1-cf2005ca7dcc" />
>
<br>

**Step 80: I entered the new user details for Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 81  Creating a new user in ADUC within Admins - Siyolo _ Admin" src="https://github.com/user-attachments/assets/17c92cda-e079-4503-9265-ffebf3bbe564" />
>
<br>

**Step 81: Siyolo_Admin account details ie password.**
<br>
<img width="1128" height="1600" alt="Step 82  Siyolo Admin details for ADUC Admins" src="https://github.com/user-attachments/assets/2117d2c5-19cc-4bbe-9059-5e9159e4922a" />
>
<br>

**Step 82: I created a secure password for the Siyolo_Admin account.**
<br>
<img width="1366" height="768" alt="Step 83  Creating password for Siyolo Kamisa admin" src="https://github.com/user-attachments/assets/a5535c0e-32fc-427c-a71f-409e99dcf8eb" />
>
<br>

**Step 83: I confirmed the successful creation of the Siyolo_Admin user.**
<br>
<img width="1366" height="768" alt="Step 84  Succesfully Created new admin Siyolo Kamisa for ADUC" src="https://github.com/user-attachments/assets/75a58624-0820-4fc5-bd84-93d76db0ad94" />
>
<br>

**Step 84: I accessed the Properties window for Siyolo_Admin to modify account permissions.**
<br>
<img width="1366" height="768" alt="Step 85  Alerting properties of Siyolo Kamisa for admin powers" src="https://github.com/user-attachments/assets/3df008ab-5430-4bf6-9eae-e8917a70d5c0" />
>
<br>

**Step 85: I navigated to the Member Of tab to manage group memberships for Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 86  Alerting properties of Siyolo Kamisa for admin powers - member of" src="https://github.com/user-attachments/assets/393525e2-4d9e-4f6b-ab37-4e22b360ab4f" />
>
<br>

**Step 86: I verified the initial Domain Users membership.**
<br>
<img width="1366" height="768" alt="Step 87  Alerting properties of Siyolo Kamisa for admin powers - member of Domain Users" src="https://github.com/user-attachments/assets/d08d1b99-4d6a-4b6d-8b75-5922ed78269c" />
>
<br>

**Step 87: I added Domain Admins to the member list for Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 88  Alerting properties of Siyolo Kamisa for admin powers - member of Domain Users   Domain Admins" src="https://github.com/user-attachments/assets/a90edb94-cce8-4730-858e-22049f4d4e99" />
>
<br>

**Step 88: I confirmed the successful update of the user's account properties for Siyolo_Admin - added to domain admin & domain users.**
<br>
<img width="1366" height="768" alt="Step 89  Successful change of Siyolo Kamisa properties" src="https://github.com/user-attachments/assets/1bb54388-651a-49e3-921b-226bb032ffaf" />
>
<br>

**Step 89: I logged into the Domain-Controller using the new credentials Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 90  Logging into Siylo Kamisa as Domain Controller Admin" src="https://github.com/user-attachments/assets/73251bbc-1c58-4412-8b06-d9dab56d7d8c" />
>
<br>

**Step 90: I input the password for Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 91  Inputting Password for Siyolo Kamisa - Domain Controller" src="https://github.com/user-attachments/assets/3f96a55b-3bab-455c-b7f0-37a9dfb22546" />
>
<br>

**Step 91: I confirmed a successful login as the new domain administrator Siyolo_Admin.**
<br>
<img width="1366" height="768" alt="Step 92  Succesfull login to Siyolo Kamisa Domain Controller" src="https://github.com/user-attachments/assets/86f0ac3b-f128-4164-9519-5006cf35bf77" />
>
<br>

**Step 92: I went back to my Client-1 VM to start process of joining it the domain mydomain.com.**
<br>
<img width="1366" height="768" alt="Step 95  Successfully log into Client - 1 VM" src="https://github.com/user-attachments/assets/ad8af516-c43e-4292-8fcb-491394b2cfe6" />
>
<br>

**Step 93: I navigated to the system settings to join the Client-1 machine to the domain mydomain.com.**
<br>
<img width="1366" height="768" alt="Step 96  Adding Client - 1 VM to mydomain com domain" src="https://github.com/user-attachments/assets/14b3aafb-777f-4e41-8fc2-76d2219710d6" />
>
<br>

**Step 94: I prepared to change the domain membership of the machine.**
<br>
<img width="1366" height="768" alt="Step 97  Adding Client - 1 VM to mydomain com domain" src="https://github.com/user-attachments/assets/a4474788-62ac-40d4-ae81-56b9c3059990" />
>
<br>

**Step 95: I entered mydomain.com as the target domain.**
<br>
<img width="1366" height="768" alt="Step 98  Adding Client - 1 VM to mydomain com domain" src="https://github.com/user-attachments/assets/aafa3663-25f7-4426-b1e7-0c54e5a06bf4" />
>
<br>

**Step 96: I confirmed the domain change request.**
<br>
<img width="1366" height="768" alt="Step 99  Adding Client - 1 VM to mydomain com domaincasasc" src="https://github.com/user-attachments/assets/8c9ee92c-656b-4985-831e-9456105d5461" />
>
<br>

**Step 97: I entered the administrative credentials for Siyolo_Admin to authorize joining the domain.**
<br>
<img width="1366" height="768" alt="Step 100  Adding Client - 1 VM to mydomain com domainscss" src="https://github.com/user-attachments/assets/69897216-24ca-492a-aea8-d2a2a531a6e7" />
>
<br>

**Step 98: I authorized the domain join with the Siyolo_Admin password.**
<br>
<img width="1366" height="768" alt="Step 101  Adding Client - 1 VM to mydomain com domaincscsasac" src="https://github.com/user-attachments/assets/c12f1652-b4f3-42a8-8a83-87e4e545793a" />
>
<br>

**Step 99: I received the confirmation that Client-1 had successfully joined the mydomain.com domain.**
<br>
<img width="1366" height="768" alt="Step 102  Successfully added Client - 1 to mydomain com domain" src="https://github.com/user-attachments/assets/18017ce4-3d21-4570-87be-1662b859ec14" />
>
<br>

**Step 100: I acknowledged the system prompt to restart Client-1 to apply the domain changes.**
<br>
<img width="1366" height="768" alt="Step 103  Restart of Client - 1 VM to apply changes" src="https://github.com/user-attachments/assets/2f3430ce-5402-4c8c-82ae-fe94d16ef5c8" />
>
<br>

**Step 101: I initiated the login process for Client-1 after the restart.**
<br>
<img width="1366" height="768" alt="Step 104  Logging in Client 1 VM" src="https://github.com/user-attachments/assets/a31a83e1-1caf-4b32-bcaa-0d295549e0bc" />
>
<br>

**Step 102: I entered the credentials to log back into Client-1.**
<br>
<img width="1366" height="768" alt="Step 105  Inputting password to log in  Client - 1 VM" src="https://github.com/user-attachments/assets/4fbf35a8-9178-48ce-9c64-ad53e754debd" />
>
<br>

**Step 103: I confirmed a successful login to the Client-1 desktop within the domain.**
<br>
<img width="1366" height="768" alt="Step 106  Successfull log in to Client - 1 VM" src="https://github.com/user-attachments/assets/f7502288-516c-4486-83a0-75cac632aa42" />
>
<br>

**Step 104: I verified that Client-1 had correctly joined the mydomain.com domain via the System settings.**
<br>
<img width="1366" height="768" alt="Step 107  Validating Client - 1 has joined mydomain com domain" src="https://github.com/user-attachments/assets/4443c22a-7bf6-42d4-849c-3273e6418610" />
>
<br>

**Step 105: I went back to my Domain-Controller VM.**
<br>
<img width="1366" height="768" alt="Step 110  Succesfull login to Domain Controller" src="https://github.com/user-attachments/assets/6184bd18-8884-4292-9d3f-d84f53e9cf99" />
>
<br>

**Step 106: I launched Active Directory Users and Computers to check the domain status.**
<br>
<img width="1366" height="768" alt="Step 111  Launching Active Directory" src="https://github.com/user-attachments/assets/de2ff9f8-0820-4cd7-9305-9d01b4bb1991" />
>
<br>

**Step 107: I verified the successful launch of the Active Directory management console.**
<br>
<img width="1366" height="768" alt="Step 112  Successful launch of Active Directory" src="https://github.com/user-attachments/assets/8a55dca5-8303-49f8-98b4-eeee4c87ca30" />
>
<br>

**Step 108: I navigated to the Computers container to validate that Client-1 was now correctly registered as part of the mydomain.com domain.**
<br>
<img width="1366" height="768" alt="Step 113  Validating Client - 1 is part of mydomain com on Domain Controller" src="https://github.com/user-attachments/assets/31043e6b-820e-49e1-ad0e-a7bc03f91a30" />

>
<br>
⸻

##🔹 Phase 3: Client User Management & Group Policy Configuration.

In this phase, I focused on user administration and the implementation of Group Policy Objects (GPOs) to control environment security. My activities included enabling Remote Desktop access for users on the Client-1 VM, automating the bulk creation of user accounts using a PowerShell script, and enforcing security policies—specifically account lockout thresholds—via Group Policy Management. I validated these configurations by testing user access, account lockout behaviors, and administrative user account management tasks, including account enabling/disabling and password resets
>
<br>
⸻

**Step 109: I went back to my Client-1 VM to start process of joining users to Remote Desktop mydomain.com.**
<br>
<img width="1366" height="768" alt="Step 116  Successful login to Client - 1 VM" src="https://github.com/user-attachments/assets/2bc1c66f-7822-457d-9506-992cec177f23" />
>
<br>

**Step 110: I opened the Windows Settings menu to modify system preferences.**
<br>
<img width="1366" height="768" alt="Step 117  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/f2a797cd-7f0b-413e-8f4d-2d82fa99b187" />
>
<br>

**Step 111: I navigated to the System menu within the settings interface.**
<br>
<img width="1366" height="768" alt="Step 118  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/c670e97e-810e-4f2c-bb17-a015c8f2cf78" />
>
<br>

**Step 112: I located the Remote Desktop configuration page.**
<br>
<img width="1366" height="768" alt="Step 119  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/3f081008-eca6-486c-94fc-c00504463fdd" />
>
<br>

**Step 113: I toggled the switch to enable Remote Desktop connections.**
<br>
<img width="1366" height="768" alt="Step 120  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/5933a75b-f4c6-4151-ba03-d7557dcaf370" />
>
<br>

**Step 114: I confirmed the system prompt to enable the feature.**
<br>
<img width="1366" height="768" alt="Step 121  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/483755e1-427d-4e4e-b1ae-a6dbff9812eb" />
>
<br>

**Step 115: I selected the link to manage Remote Desktop users.**
<br>
<img width="1366" height="768" alt="Step 122  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/d4204b80-5e17-46a2-a3c0-77edb127bc0e" />
>
<br>

**Step 116: I clicked the button to add new users to the Remote Desktop group.**
<br>
<img width="1366" height="768" alt="Step 123  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/65f99168-8ab4-4ad0-a60c-47a97f6c73cb" />
>
<br>

**Step 117: I typed "Domain Users" into the object selection field.**
<br>
<img width="1366" height="768" alt="Step 124  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/0c09eda8-38de-4b96-89de-db3eef1db62d" />
>
<br>

**Step 118: I verified the user group was added and closed the settings window.**
<br>
<img width="1366" height="768" alt="Step 125  Accessing Remote Desktop Settings on Client - 1 to allow users to join Remote Desktop" src="https://github.com/user-attachments/assets/4c5fef45-eda8-4a8a-8704-c435bc4c3929" />
>
<br>

**Step 119: I went back to my Domain Controller VM. to start process of creating users**
<br>
<img width="1366" height="768" alt="Step 128  Successful log in to Domain Controller" src="https://github.com/user-attachments/assets/c463b5e5-0f5a-4233-92c9-1e8169310478" />
>
<br>

**Step 120: I launched the Windows PowerShell ISE application from the start menu.**
<br>
<img width="1366" height="768" alt="Step 129  Launching Windows Powershell ISE on Domain Controller to create users" src="https://github.com/user-attachments/assets/ae2ed801-c159-4648-9416-55e2469b6de2" />
>
<br>

**Step 121: I verified that the PowerShell ISE interface loaded correctly.**
<br>
<img width="1366" height="768" alt="Step 130  Successful launch of Windows Powershell ISE to create users on Domain Controller" src="https://github.com/user-attachments/assets/5ed23947-0811-4bc1-b87a-c869c9942cf0" />
>
<br>

**Step 122: I opened the script file designed for automated user creation.**
<br>
<img width="958" height="1600" alt="Step 131  Script to create users" src="https://github.com/user-attachments/assets/010a2466-af36-4333-a9d9-356463c87dca" />
>
<br>

**Step 123: I triggered the execution of the user creation script.**
<br>
<img width="1366" height="768" alt="Step 132  Promtp of script to create users on Windows Powershell ISE - Domain Controller VM" src="https://github.com/user-attachments/assets/6ea6b41d-14f7-4c4f-af18-88069d025200" />
>
<br>

**Step 124: I observed the terminal confirming the successful generation of user objects.**
<br>
<img width="1366" height="768" alt="Step 133  Successful prompt of user script on Domain Controller" src="https://github.com/user-attachments/assets/b2f9dea1-8204-41cd-a396-9aabdc8f50a3" />
>
<br>

**Step 126: I searched for and opened the Active Directory Users and Computers (ADUC) tool.**
<br>
<img width="1366" height="768" alt="Step 134  Opening  Active Directory to verify users have been created" src="https://github.com/user-attachments/assets/eb36e451-3cc5-4baa-8416-709ddf6aa3fb" />
>
<br>

**Step 127: I maximized the ADUC console to prepare for verification users have been created.**
<br>
<img width="1366" height="768" alt="Step 135  Succesful launch of Active Directory to verify users have been created" src="https://github.com/user-attachments/assets/174eaf8b-d374-4d32-ba02-af6452714d6a" />
>
<br>

**Step 128: I browsed the "Employees/Staff" folder to confirm the new accounts appeared in the list.**
<br>
<img width="1366" height="768" alt="Step 136  Users created confirmed on ADUC of Domain Controller" src="https://github.com/user-attachments/assets/e31c95cb-0c1c-45ad-ba4f-fb8413aeb0be" />
>
<br>

**Step 129: I selected the specific user "Kufukos Bukohu" to prepare for an RDP test.**
<br>
<img width="1366" height="768" alt="Step 137  Selecting one of the user accounts (Kufukos Bukohu) I created to log into Client - 1 VM" src="https://github.com/user-attachments/assets/8cf6bacb-8d04-4796-b2b5-d954829b3758" />
>
<br>

**Step 130: I reviewed the user account properties to ensure correct configuration.**
<br>
<img width="1366" height="768" alt="Step 138  Verifying Kufukos Bukohu is a user" src="https://github.com/user-attachments/assets/c14c09ef-d29c-43df-bb49-aeb6739980cf" />
>
<br>

**Step 131: I initiated an RDP connection to Client-1 using the selected account "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 139  Selecting Kufukos Bukohu I to log into Client - 1 VM" src="https://github.com/user-attachments/assets/4d8fe99a-833b-4090-88cc-87a169927f93" />
>
<br>

**Step 132: I provided the password for the user "Kufukos Bukohu" account.**
<br>
<img width="1366" height="768" alt="Step 140  Inputting password for Kufukos Bukohu" src="https://github.com/user-attachments/assets/b5cc552f-102c-4bb2-ad8d-2cc6d5c7e019" />
>
<br>

**Step 133: I successfully logged into the user "Kufukos Bukohu" on the Client-1 VM.**
<br>
<img width="1366" height="768" alt="Step 141  Successful log in to Kufukos Bukohu" src="https://github.com/user-attachments/assets/aef4e610-1d25-4794-906b-c2b339b65588" />
>
<br>

**Step 134: I verified my identity "Kufukos Bukohu" by checking the logged-in user profile on Client-1.**
<br>
<img width="1366" height="768" alt="Step 142  Verifying I am in Kufukos Bukohu Account" src="https://github.com/user-attachments/assets/9b0166b4-6659-469a-8a9d-823ff83c6a12" />
>
<br>

**Step 135: I went back to my Domain Controller VM to start process of Group Policy Management.**
<br>
<img width="1366" height="768" alt="Step 145  Successfull login" src="https://github.com/user-attachments/assets/08f8343e-6d4a-44cc-963c-a12fb5d78053" />
>
<br>

**Step 136: I opened the Group Policy Management console.**
<br>
<img width="1366" height="768" alt="Step 146  Accessing Group Policy Management of Active Directory - Domain Controller" src="https://github.com/user-attachments/assets/fa9a223b-52fe-470d-91a2-49893692194f" />
>
<br>

**Step 137: I succesfully initialized correctly Group Policy Management console.**
<br>
<img width="1366" height="768" alt="Step 147  Successful Launch of Group Policy Management of Active Directory" src="https://github.com/user-attachments/assets/a27e43f4-c4cc-4e6a-8566-7dacdcb2ef77" />
>
<br>

**Step 138: I expanded the "mydomain.com" tree in the left navigation pane to set Group Police Rules.**
<br>
<img width="1366" height="768" alt="Step 148  Setting Group Policy Rules of mydomain com" src="https://github.com/user-attachments/assets/f3f2bcda-8165-410d-9825-a5c7f22ac6c1" />
>
<br>

**Step 139: I selected the Default Domain Policy object.**
<br>
<img width="1366" height="768" alt="Step 149  Setting Group Policy Rules of mydomain com" src="https://github.com/user-attachments/assets/08483a23-c8ef-42ce-a2bb-a65bcef8db87" />
>
<br>

**Step 140: I selected the "Edit" function to modify policy rules.**
<br>
<img width="1366" height="768" alt="Step 150  Setting Group Policy Rules of mydomain com" src="https://github.com/user-attachments/assets/2997c4f9-4da9-4df1-9062-149bd22a3089" />
>
<br>

**Step 141: I expanded the policy tree to reach the Account Lockout settings.**
<br>
<img width="1366" height="768" alt="Step 151  Setting Group Policy Rules of mydomain com Setting Group Policy Rules of mydomain com (Account Lockout)" src="https://github.com/user-attachments/assets/894f662c-3be6-48a5-b864-cb9e151615c4" />
>
<br>

**Step 142: I set the Lockout Policy to 45 Minutes.**
<br>
<img width="1366" height="768" alt="Step 152  Setting Group Policy Rules of mydomain com Setting Group Policy Rules of mydomain com (Account Lockout)" src="https://github.com/user-attachments/assets/9ee6b57c-1cb1-4c3f-8c53-e7a1f5829263" />
>
<br>
**Step 143: I opened the Account Lockout Duration properties window.**
<br>
<img width="1366" height="768" alt="Step 153   Setting Group Policy Rules of mydomain com Setting Group Policy Rules of mydomain com (Account Lockout)" src="https://github.com/user-attachments/assets/2a33207e-3cac-423c-9dc3-2f9100241066" />
>
<br>

**Step 144: I opened the Account Lockout Threshold & set to lock out after 3 failed attempts.**
<br>
<img width="1366" height="768" alt="Step 154   Setting Group Policy Rules of mydomain com Setting Group Policy Rules of mydomain com (Account Lockout)" src="https://github.com/user-attachments/assets/80ed4b7a-e16d-4982-a0a4-ef90139ba134" />
>
<br>

**Step 145: My fianl account lockout policy rules.**
<br>
<img width="1366" height="768" alt="Step 155   Setting Group Policy Rules of mydomain com Setting Group Policy Rules of mydomain com (Account Lockout)" src="https://github.com/user-attachments/assets/a0bfabe3-4509-46b0-852c-d2ae0325ff23" />
>
<br>

**Step 146: I opened the Command Prompt as an administrator to enforce new group policy rules.**
<br>
<img width="1366" height="768" alt="Step 156  Accessing Comand Line to enforce New Group Policy Rules" src="https://github.com/user-attachments/assets/f7a0f971-bcdb-4583-afcc-bd1f7f4d9a4d" />
>
<br>

**Step 147: I verified the command console was ready for my input.**
<br>
<img width="1366" height="768" alt="Step 157  Successful launch of Comand Line" src="https://github.com/user-attachments/assets/c20836a1-1e25-4040-bcf9-f4e67b9139a0" />
>
<br>

**Step 148: I ran whoami to ensure I was executing commands in the correct domain context Siyolo Admin of Domain Controller.**
<br>
<img width="1366" height="768" alt="Step 158  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/94d224dd-b577-486c-983b-a6ed2213bb65" />
>
<br>
**Step 149: I initiated the group policy update process by utilizing the command gpupdate /force.**
<br>
<img width="1366" height="768" alt="Step 159  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/aecda100-6fce-4689-801a-71364832df4b" />
>
<br>

**Step 150: I received the system confirmation that the policy update succeeded.**
<br>
<img width="1366" height="768" alt="Step 160  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/9b2cf0a7-adae-4db9-96a7-81b96e321acc" />
>
<br>

**Step 151: I utilozed the gpresult command to check the effective policy sets.**
<br>
<img width="1366" height="768" alt="Step 161  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/70042e7d-977c-4a4c-a447-f653a7fe9925" />
>
<br>

**Step 152: I executed the diagnostic tool to review applied policies.**
<br>
<img width="1366" height="768" alt="Step 162  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/5c179e78-3c79-47d7-b5ef-25fc51f940ab" />
>
<br>

**Step 153: I reviewed the command output to verify the policy application status.**
<br>
<img width="1366" height="768" alt="Step 163  Enforcing New Group Policy Rules on Command Line for mydomain com" src="https://github.com/user-attachments/assets/a5237f98-2a23-43f6-8914-5ae26bd8779b" />
>
<br>

**Step 154: I returned to Client-1 to test the new lockout policy using the user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 164  Attempting to login Kufukos Bukohu with new Group Policy Rules" src="https://github.com/user-attachments/assets/06060a2d-7a73-49ab-9c55-71411f0de40b" />
>
<br>

**Step 155: I entered the credentials for the user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 165  Attempting to login Kufukos Bukohu with new Group Policy Rules" src="https://github.com/user-attachments/assets/c3462369-3097-40f4-9320-ba4613b89df8" />
>
<br>

**Step 156: I intentionally provided an incorrect password to trigger the policy.**
<br>
<img width="1366" height="768" alt="Step 166  Attempting to login Kufukos Bukohu with new Group Policy Rules" src="https://github.com/user-attachments/assets/8efa67b6-fae4-48ab-82f2-346852223020" />
>
<br>

**Step 157: I repeated the incorrect login attempts.**
<br>
<img width="1366" height="768" alt="Step 167  Attempting to login Kufukos Bukohu with new Group Policy Rules" src="https://github.com/user-attachments/assets/0f25b1a8-4170-479b-ad03-624855d07229" />
>
<br>

**Step 158: I observed the system lock the account due to the repeated failed attempts.**
<br>
<img width="1366" height="768" alt="Step 168  Kufukos Bukohu account lock due to new Group Policy Rules" src="https://github.com/user-attachments/assets/5095e80a-937e-421f-8082-664d12d0ead8" />
>
<br>

**Step 159: I navigated back to the Domain Controller VM to perform the manual unlock of user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 169  Back to Domain Controller portal to unlock Kufukos Bukohu&#39;s account" src="https://github.com/user-attachments/assets/199674d3-42c1-408e-93b1-f7bf36a2b4dc" />
>
<br>

**Step 160: I opened the ADUC console to manage the locked user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 170  Accessing Active Directory to unlock Kufukos Bukohu&#39;s account on Domain Controller VM" src="https://github.com/user-attachments/assets/fc9e8409-3a49-4e51-9e92-afb2324c0498" />
>
<br>

**Step 161: I located the "Kufukos Bukohu" account in the directory.**
<br>
<img width="1366" height="768" alt="Step 171   Locating Kufukos Bukohu&#39;s account on Active Directory on Domain Controller VM" src="https://github.com/user-attachments/assets/2c7564a0-1aa9-4fea-84bb-cf62c9dddc8f" />
>
<br>

**Step 162: I accessed the properties of the locked user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 172  Located Kufukos Bukohu&#39;s account on ADUC - Domain Controller" src="https://github.com/user-attachments/assets/569c7a3f-c12f-45ce-96fb-7cdc15d736ec" />

**Step 163: I navigated to the Account tab in the properties window.**
<br>
<img width="1366" height="768" alt="Step 173  Unlocking Kufukos Bukohu&#39;s account on Active Directory - Domain Controller" src="https://github.com/user-attachments/assets/9617418d-eabc-4d9d-8d3b-063e85ed6423" />
>
<br>

**Step 164: Loocked for a box to check unlock the user account.**
<br>
<img width="1366" height="768" alt="Step 174  Unlocking Kufukos Bukohu&#39;s account on Active Directory - Domain Controller" src="https://github.com/user-attachments/assets/223ec085-7283-4d03-a60c-150e8c2c453f" />
>
<br>

**Step 165: I applied the changes to release the account lock by ticking the box unlock account for the user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 175  Unlocking Kufukos Bukohu&#39;s account on Active Directory - Domain Controller" src="https://github.com/user-attachments/assets/608ab888-4734-4af9-9765-636d47b51802" />
>
<br>

**Step 166: I returned to the Client-1 VM for a final login test "Kufukos Bukohu" user.**
<br>
<img width="1366" height="768" alt="Step 176  Attempting to log in Kufukos Bukohu&#39;s account after unlocking it" src="https://github.com/user-attachments/assets/5a5d4e7a-b1ec-45b3-a1c1-c79247e9aabf" />
>
<br>

**Step 167: I entered the password for the now unlocked account user "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 177  Inputting password to Kufukos Bukohu&#39;s account after unlocking it" src="https://github.com/user-attachments/assets/9b6cb6a2-0214-493a-b96e-8916f30d19ad" />
>
<br>

**Step 168: I verified that the user "Kufukos Bukohu" was accessible again.**
<br>
<img width="1366" height="768" alt="Step 178  Succesfull login to Kufukos Bukohu&#39;s account" src="https://github.com/user-attachments/assets/3beec862-2fd2-48a5-b360-6241101dc6a3" />
>
<br>

**Step 169: I confirmed the successful login to the user desktop "Kufukos Bukohu".**
<br>
<img width="1366" height="768" alt="Step 179  Confirming  Kufukos Bukohu&#39;s account" src="https://github.com/user-attachments/assets/0f0c15d9-ed0a-4b24-a0c0-20886adf463d" />
>
<br>

**Step 170: I switched back to the Domain Controller to manage further user settings.**
<br>
<img width="1366" height="768" alt="Step 180  Back to Domain Controller portal to attempt to change password of a user" src="https://github.com/user-attachments/assets/a4bd9a1f-f652-406c-8261-e97d1600833d" />
>
<br>

**Step 171: I launched the ADUC tool to perform a password management task.**
<br>
<img width="1366" height="768" alt="Step 181  Accessing ADUC on Domain Controller to attemp to change password of a user" src="https://github.com/user-attachments/assets/66d4955d-b172-4f06-9847-7b49c8423f04" />
>
<br>

**Step 172: I navigated to the "Employees/Staff" organizational unit.**
<br>
<img width="1366" height="768" alt="Step 182  Openining Employees-Staff OU to select a user account to attempt to change password" src="https://github.com/user-attachments/assets/9163cf04-c0c1-4185-bfd1-081168c3884e" />
>
<br>

**Step 173: I selected the "Sadagid Nisud" account from the user list.**
<br>
<img width="1366" height="768" alt="Step 183  Selected Sadagid Nisud for password reset in ADUC - Domain Controller" src="https://github.com/user-attachments/assets/ca7b8775-72b3-46f1-9b7c-a64eb110c8d8" />
>
<br>

**Step 174: I opened the context menu to select the password reset option.**
<br>
<img width="1366" height="768" alt="Step 184  Selected Sadagid Nisud for password reset in ADUC - Domain Controller" src="https://github.com/user-attachments/assets/3808c60f-6ade-4b6d-a663-855b8347108b" />
>
<br>

**Step 175: I set a new password for the selected user "Sadagid Nisud".**
<br>
<img width="1366" height="768" alt="Step 185  Selected Sadagid Nisud for password reset in ADUC - Domain Controller" src="https://github.com/user-attachments/assets/cdd88e92-1da7-4f7b-a369-83ad8491ba51" />
>
<br>

**Step 176: I transitioned to the next administrative task: disabling a user account.**
<br>
<img width="1366" height="768" alt="Step 186  Back to Domain Controller portal to disable a user account" src="https://github.com/user-attachments/assets/85fa320f-753e-45cb-8f5c-052bdfa886b8" />
>
<br>

**Step 177: I opened the ADUC console to modify account status.**
<br>
<img width="1366" height="768" alt="Step 187  Accessing ADUC to disable a user account - Domain Controller" src="https://github.com/user-attachments/assets/5bafbc17-3b09-40da-b356-904591b3832b" />
>
<br>

**Step 178: I selected the user "Demoxome Sukud" for the disable operation.**
<br>
<img width="1366" height="768" alt="Step 188  Selecting Demoxome Sukud to disable thier account" src="https://github.com/user-attachments/assets/ab7df80d-343c-4205-87d4-90baf67900ef" />
>
<br>

**Step 179: I right-clicked the object to reveal management options.**
<br>
<img width="1366" height="768" alt="Step 189  Selecting Demoxome Sukud to disable thier account" src="https://github.com/user-attachments/assets/8f034079-75ba-4c6e-8d1b-e95352bb9548" />
>
<br>

**Step 180: I triggered the action to disable the account and confirmed the success message.**
<br>
<img width="1366" height="768" alt="Step 190  Demoxome Sukud account successfully  disabled" src="https://github.com/user-attachments/assets/ade498f9-6af7-4eef-8c8b-b718dc2f7384" />
>
<br>

**Step 181: I tested the restriction by attempting a login with the disabled account "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 191  Attempting to login Demoxome Sukud account after disabling it" src="https://github.com/user-attachments/assets/752cf604-7a55-4dcd-a1eb-a945e441f28a" />
>
<br>

**Step 182: I entered the credentials for the disabled user "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 192  Inputting Password Demoxome Sukud account" src="https://github.com/user-attachments/assets/5d768ac5-a0e8-44e3-8461-6b4c8267d010" />
>
<br>

**Step 183: I observed the system error message indicating the account was disabled of "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 193  Demoxome Sukud account is disabled" src="https://github.com/user-attachments/assets/7305ca70-095b-48c8-b848-83caa92341b6" />
>
<br>

**Step 184: I returned to the Domain Controller to re-enable the account "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 194  Back to Domain Controller portal to enable Demoxome Sukud Account" src="https://github.com/user-attachments/assets/84ae5bcf-b8ab-4c66-aa46-42da63969f20" />
>
<br>

**Step 185: I accessed the user account "Demoxome Sukud" within the ADUC console.**
<br>
<img width="1366" height="768" alt="Step 195  Accesing ADUC to enable Demoxome Sukud Account" src="https://github.com/user-attachments/assets/f0919019-1811-4c44-9ccd-9109947cf2a5" />
>
<br>

**Step 186: I selected the option to enable the user account "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 196  Enabling Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/113fee02-b072-4aee-8919-f57ff50062cd" />
>
<br>

**Step 187: I confirmed the change for the "Demoxome Sukud" account.**
<br>
<img width="1366" height="768" alt="Step 197  Enabling Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/6d4e25d9-d141-4981-b6a9-24cf7aaeffd7" />
>
<br>

**Step 188: I received the system notification that the object was successfully enabled.**
<br>
<img width="1366" height="768" alt="Step 198  Demoxome Sukud&#39;s account enabled" src="https://github.com/user-attachments/assets/77ca232e-08ae-40ae-b18d-9530cf6854ba" />
>
<br>

**Step 189: I switched to the Client-1 VM to verify the account was active.**
<br>
<img width="1366" height="768" alt="Step 199  Attempting to log in Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/ae239e08-2649-42f2-ab08-2b9a549d6971" />
>
<br>

**Step 190: I entered the password to log in "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 199  Attempting to log in Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/9be33949-36c4-4bf8-bce5-160e9390798b" />
>
<br>

**Step 191: I reached the desktop to confirm access was restored of "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 201  Successful log in Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/ac1df2e0-83f0-49f0-8595-3f1d3518c1d3" />
>
<br>

**Step 192: I verified the user profile of the account "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 202  Confirming it is Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/de23e763-962c-46bf-9498-79565d2a919f" />
>
<br>

**Step 193: I opened the PowerShell terminal to perform a final confirmation.**
<br>
<img width="1366" height="768" alt="Step 203  Accessing Powershell to confirm Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/70131157-8bb5-4a54-9ab9-aace547f33cf" />
>
<br>

**Step 194: I typed the whoami command into the terminal.**
<br>
<img width="1366" height="768" alt="Step 204  Prompting whoami to confirm Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/638ba4f4-666b-4a29-a91a-e7419baa6600" />
>
<br>

**Step 195: I viewed the output confirming the correct user session was active of "Demoxome Sukud".**
<br>
<img width="1366" height="768" alt="Step 205  Successful Prompt of whoami command  to confirm Demoxome Sukud&#39;s account" src="https://github.com/user-attachments/assets/eb788999-918c-4998-a3d4-75cfd07fb94d" />
>
<br>

**Step 196: I returned to the Domain Controller desktop to conclude the lab.**
<br>
<img width="1366" height="768" alt="Step 206  Back to Domain Controller to access Event Viewer" src="https://github.com/user-attachments/assets/0385cc6a-021c-4bc4-a92a-57408d59023c" />
>
<br>


⸻

#🏁Conclusion 

Successfully deployed a fully functional Active Directory environment capable of authenticating users, managing computers, and providing centralized administration similar to what is used in enterprise IT environments.

