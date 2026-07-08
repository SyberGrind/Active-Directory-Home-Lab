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
>
<br>
⸻

**Step 1: I opened the Resource Manager in the Azure Portal to view my existing resource groups.
<br>

**Step 2: I navigated to the Create a resource group screen.
<br>

**Step 3: I selected East Asia as the region and named the new resource group ADLab.
<br>

**Step 4: I reviewed the configuration to confirm the name ADLab and the East Asia region.
<br>

**Step 5: I verified that the ADLab resource group was successfully created.
<br>

**Step 6: I navigated to the Virtual Network creation portal.
<br>

**Step 7: I selected the ADLab resource group to associate the new network.
<br>

**Step 8: I named the virtual network ADVNET and ensured it was assigned to the East Asia region.
<br>

**Step 9: I reviewed the settings and initiated the creation of ADVNET.
<br>

**Step 10: I confirmed that the virtual network ADVNET was successfully created.
<br>

**Step 11: I accessed the Virtual Machine creation portal.
<br>

**Step 12: I began the configuration process for my first virtual machine.
<br>

**Step 13: I continued through the Virtual Machine deployment wizard.
<br>

**Step 14: I set the Resource Group to ADLab, the region to East Asia, and named the VM Domain-Controller.
<br>

**Step 15: I selected the Windows Server 2022 image and the appropriate instance size.
<br>

**Step 16: I defined the administrative Username and Password for the VM.
<br>

**Step 17: I input and confirmed the secure credentials for the Domain-Controller.
<br>

**Step 18: I selected ADVNET as the Virtual Network for the Domain-Controller.
<br>

**Step 19: I completed the validation check to ensure the Domain-Controller was ready for deployment.
<br>

**Step 20: I confirmed that the Domain-Controller virtual machine was successfully created.
<br>

**Step 21: I accessed the Virtual Machine creation portal to deploy my second VM.
<br>

**Step 22: I set the Resource Group to ADLab, the region to East Asia, and named the VM Client-1.
<br>

**Step 23: I selected the Windows 11 Pro image and appropriate size for the client workstation.
<br>

**Step 24: I defined the administrative Username and Password for the Client-1 VM.
<br>

**Step 25: I input and confirmed the secure credentials for the Client-1 VM.
<br>

**Step 26: I selected ADVNET as the Virtual Network for the Client-1 VM.
<br>

**Step 27: I ran the validation check to ensure Client-1 was ready for deployment.
<br>

**Step 28: I confirmed that the Client-1 virtual machine was successfully created.
<br>

**Step 29: I located and copied the Public IP Address 104.214.185.151 assigned to the Domain-Controller VM.
<br>

**Step 30: I launched Remote Desktop Connection and initiated a session using the copied Public IP Addresss 104.214.185.151.
<br>

**Step 31: I entered my administrative credentials to authenticate the remote session.
<br>

**Step 32: I confirmed successful login and access to the Domain-Controller desktop.
<br>

**Step 33: I pressed Windows + R and typed wf.msc to launch the Windows Defender Firewall.
<br>

**Step 34: I verified that the Windows Defender Firewall with Advanced Security console had opened.
<br>

**Step 35: I accessed the Properties window and set the Domain Profile firewall state to Off.
<br>

**Step 36: In the same Properties window, I set the Private Profile firewall state to Off.
<br>

**Step 37: I set the Public Profile firewall state to Off.
<br>

**Step 38: I confirmed and applied the changes to the firewall profiles.
<br>

**Step 39: I navigated to the Network Interface settings for the Domain-Controller and changed the Private IP allocation to Static.
<br>

**Step 40: I verified that the internal IP address (10.0.0.4) was successfully set to Static.
<br>

**Step 41: I copied the Private IP Address of the Domain-Controller for my next configuration step.
<br>

**Step 42: I navigated to the Network settings for the Client-1 VM in the Azure portal.
<br>

**Step 43: I accessed the DNS server settings for the Client-1 network interface.
<br>

**Step 44: I changed the DNS setting to Custom and entered the Domain-Controller’s private IP (10.0.0.4).
<br>

**Step 45: I saved the changes and confirmed the DNS server update for Client-1.
<br>

**Step 46: I located and copied the Public IP Address of the Client-1 VM.
<br>

**Step 47: I opened Remote Desktop, connected using the Client-1 Public IP Addresss 104.214.179.243, and input my credentials.
<br>

**Step 48: I confirmed successful launch and login to the Client-1 desktop.
<br>

**Step 49: I opened Settings from the Start menu to verify the system identity.
<br>

**Step 50: I searched for and launched Windows PowerShell with administrative privileges.
<br>

**Step 51: At the PowerShell prompt, I typed ping 10.0.0.4 to test the connection to the Domain Controller.
<br>

**Step 52: I observed the successful ping replies to confirm network connectivity.
<br>

**Step 53: I executed the ipconfig /all command to verify that the Client-1 VM was correctly using the Domain Controller for DNS resolution.
<br>

⸻
<br>

##🔹Phase 2: Active Directory Domain Services Configuration.

In this phase, I configured the Domain Controller and established a formal domain infrastructure within my Azure environment. My primary objective was to deploy and promote the Active Directory Domain Services Configuration role to create a new forest named mydomain.com. Following the domain promotion, I implemented organizational security and administration by creating custom organizational units (Employees/Staff and Admins) and provisioning an administrative user, Siyolo_Admin, with delegated domain administrative privileges. Finally, I successfully joined the Client-1 VM to the mydomain.com domain, confirming full connectivity and integration within the domain environment.
>
<br>
⸻

**Step 54: I logged back into the Domain-Controller virtual machine.
<br>

**Step 55: I input my password to authenticate the session.
<br>

**Step 56: I confirmed the successful launch of the Domain-Controller virtual machine.
<br>

**Step 57: I opened the Server Manager to begin the process of setting up Active Directory.
<br>

**Step 58: I verified the successful launch of Server Manager.
<br>

**Step 59: I initiated the Add Roles & Features wizard within Server Manager.
<br>

**Step 60: I navigated through the initial screens of the Add Roles & Features wizard.
<br>

**Step 61: I continued the setup process for the server roles.
<br>

**Step 62: I continued the setup process for the server roles.
<br>

**Step 63: I selected Active Directory Domain Services as the required role.
<br>

**Step 64: I confirmed the inclusion of required management tools for AD DS.
<br>

**Step 65: I verified the successful completion of the Add Roles & Features installation.
<br>

**Step 66: I proceeded to the Active Directory Configuration stage to promote the server.
<br>

**Step 67: I selected the option to Add a new forest for the deployment.
<br>

**Step 68: I specified the forest root domain name as mydomain.com.
<br>

**Step 69: I allowed the wizard to perform the Prerequisites check.
<br>

**Step 70: I proceeded with the installation, which triggered a mandatory reboot of the Domain-Controller.
<br>

**Step 71: I logged into the Domain-Controller using the new domain credentials (mydomain.com\Domain Controller).
<br>

**Step 72: I confirmed a successful login after the Active Directory installation.
<br>

**Step 73: I launched Server Manager to confirm the new role status.
<br>

**Step 74: I confirmed the successful launch of Server Manager.
<br>

**Step 75: I accessed the Active Directory Users and Computers (ADUC) tool via the Tools menu.
<br>

**Step 76: I verified the successful launch of ADUC.
<br>

**Step 77: I prepared to add a new organizational unit (OU) in ADUC.
<br>

**Step 78: I created an OU named Employees/Staff.
<br>

**Step 79: I created a second OU named Admins.
<br>

**Step 80: I initiated the creation of a new user within the Admins OU.
<br>

**Step 81: I entered the new user details for Siyolo_Admin.
<br>

**Step 82: I verified the Siyolo_Admin account details.
<br>

**Step 83: I created a secure password for the Siyolo_Admin account.
<br>

**Step 84: I confirmed the successful creation of the Siyolo_Admin user.
<br>

**Step 85: I accessed the Properties window for Siyolo_Admin to modify account permissions.
<br>

**Step 86: I navigated to the Member Of tab to manage group memberships.
<br>

**Step 87: I verified the initial Domain Users membership.
<br>

**Step 88: I added Domain Admins to the member list for Siyolo_Admin.
<br>

**Step 89: I confirmed the successful update of the user's account properties.
<br>

**Step 90: I logged into the Domain-Controller using the new Siyolo_Admin credentials.
<br>

**Step 91: I input the password for Siyolo_Admin.
<br>

**Step 92: I confirmed a successful login as the new domain administrator.
<br>

**Step 93: I logged into the Client-1 virtual machine.
<br>

**Step 94: I input my password to access the Client-1 desktop.
<br>

**Step 95: I confirmed a successful login to Client-1.
<br>

**Step 96: I navigated to the system settings to join the Client-1 machine to the domain.
<br>

**Step 97: I prepared to change the domain membership of the machine.
<br>

**Step 98: I entered mydomain.com as the target domain.
<br>

**Step 99: I confirmed the domain change request.
<br>

**Step 100: I entered the administrative credentials for Siyolo_Admin to authorize joining the domain.
<br>

**Step 101: I authorized the domain join with the Siyolo_Admin password.
<br>

**Step 102: I received the confirmation that Client-1 had successfully joined the mydomain.com domain.
<br>

**Step 103: I acknowledged the system prompt to restart Client-1 to apply the domain changes.
<br>

**Step 104: I initiated the login process for Client-1 after the restart.
<br>

**Step 105: I entered the credentials to log back into Client-1.
<br>

**Step 106: I confirmed a successful login to the Client-1 desktop within the domain.
<br>

**Step 107: I verified that Client-1 had correctly joined the mydomain.com domain via the System settings.
<br>

**Step 108: I logged back into the Domain-Controller using my administrative credentials.
<br>

**Step 109: I input the password for the Domain-Controller.
<br>

**Step 110: I confirmed a successful login to the Domain-Controller.
<br>

**Step 111: I launched Active Directory Users and Computers to check the domain status.
<br>

**Step 112: I verified the successful launch of the Active Directory management console.
<br>

**Step 113: I navigated to the Computers container to validate that Client-1 was now correctly registered as part of the mydomain.com domain.
<br>
>
<br>
⸻

##🔹 Phase 3: Client User Management & Group Policy Configuration.

In this phase, I focused on user administration and the implementation of Group Policy Objects (GPOs) to control environment security. My activities included enabling Remote Desktop access for users on the Client-1 VM, automating the bulk creation of user accounts using a PowerShell script, and enforcing security policies—specifically account lockout thresholds—via Group Policy Management. I validated these configurations by testing user access, account lockout behaviors, and administrative user account management tasks, including account enabling/disabling and password resets
>
<br>
⸻

Step 114: I logged into the Client-1 VM.

Step 115: I entered my credentials for the Client-1 VM.

Step 116: I successfully reached the desktop of the Client-1 VM.

Step 117: I opened the Windows Settings menu to modify system preferences.

Step 118: I navigated to the System menu within the settings interface.

Step 119: I located the Remote Desktop configuration page.

Step 120: I toggled the switch to enable Remote Desktop connections.

Step 121: I confirmed the system prompt to enable the feature.

Step 122: I selected the link to manage Remote Desktop users.

Step 123: I clicked the button to add new users to the Remote Desktop group.

Step 124: I typed "Domain Users" into the object selection field.

Step 125: I verified the user group was added and closed the settings window.

Step 126: I initiated my remote login to the Domain Controller VM.

Step 127: I typed my administrative password to gain access.

Step 128: I successfully established my desktop session on the Domain Controller.

Step 129: I launched the Windows PowerShell ISE application from the start menu.

Step 130: I verified that the PowerShell ISE interface loaded correctly.

Step 131: I opened the script file designed for automated user creation.

Step 132: I triggered the execution of the user creation script.

Step 133: I observed the terminal confirming the successful generation of user objects.

Step 134: I searched for and opened the Active Directory Users and Computers (ADUC) tool.

Step 135: I maximized the ADUC console to prepare for verification users have been created.

Step 136: I browsed the "Employees/Staff" folder to confirm the new accounts appeared in the list.

Step 137: I selected the specific user "Kufukos Bukohu" to prepare for an RDP test.

Step 138: I reviewed the user account properties to ensure correct configuration.

Step 139: I initiated an RDP connection to Client-1 using the selected account "Kufukos Bukohu".

Step 140: I provided the password for the "Kufukos Bukohu" account.

Step 141: I successfully logged into the user "Kufukos Bukohu" on the Client-1 VM.

Step 142: I verified my identity "Kufukos Bukohu" by checking the logged-in user profile on Client-1.

Step 143: I returned to the Domain Controller desktop for policy configuration.

Step 144: I authenticated into the Domain Controller session.

Step 145: I confirmed my access to the domain administrative tools.

Step 146: I opened the Group Policy Management console.

Step 147: I ensured the management snap-in initialized correctly.

Step 148: I expanded the "mydomain.com" tree in the left navigation pane.

Step 149: I selected the Default Domain Policy object.

Step 150: I selected the "Edit" function to modify policy rules.

Step 151: I expanded the policy tree to reach the Account Lockout settings.

Step 152: I set the Lockout Policy to 45 Minutes.

Step 153: I opened the Account Lockout Duration properties window.

Step 154: I entered the value to trigger account locks after 3 failed attempts.

Step 155: My account lockout policy rules.

Step 156: I opened the Command Prompt as an administrator.

Step 157: I verified the command console was ready for my input.

Step 158: I ran whoami to ensure I was executing commands in the correct domain context.

Step 159: I initiated the group policy update process.

Step 160: I received the system confirmation that the policy update succeeded.

Step 161: I prepared the gpresult command to check the effective policy sets.

Step 162: I executed the diagnostic tool to review applied policies.

Step 163: I reviewed the command output to verify the policy application status.

Step 164: I returned to Client-1 to test the new lockout policy.

Step 165: I entered the credentials for the test user.

Step 166: I intentionally provided an incorrect password to trigger the policy.

Step 167: I repeated the incorrect login attempts.

Step 168: I observed the system lock the account due to the repeated failed attempts.

Step 169: I moved back to the Domain Controller to perform the manual unlock.

Step 170: I opened the ADUC console to manage the locked user.

Step 171: I located the "Kufukos Bukohu" account in the directory.

Step 172: I accessed the properties of the locked user object.

Step 173: I navigated to the Account tab in the properties window.

Step 174: I checked the box to unlock the user account.

Step 175: I applied the changes to release the account lock.

Step 176: I returned to the Client-1 VM for a final login test.

Step 177: I entered the password for the now-unlocked account.

Step 178: I verified that the account was accessible again.

Step 179: I confirmed the successful login to the user desktop.

Step 180: I switched back to the Domain Controller to manage further user settings.

Step 181: I launched the ADUC tool to perform a password management task.

Step 182: I navigated to the "Employees/Staff" organizational unit.

Step 183: I selected the "Sadagid Nisud" account from the user list.

Step 184: I opened the context menu to select the password reset option.

Step 185: I set a new password for the selected user.

Step 186: I transitioned to the next administrative task: disabling a user account.

Step 187: I opened the ADUC console to modify account status.

Step 188: I selected "Demoxome Sukud" for the disable operation.

Step 189: I right-clicked the object to reveal management options.

Step 190: I triggered the action to disable the account and confirmed the success message.

Step 191: I tested the restriction by attempting a login with the disabled account.

Step 192: I entered the credentials for the disabled user.

Step 193: I observed the system error message indicating the account was disabled.

Step 194: I returned to the Domain Controller to re-enable the account.

Step 195: I accessed the user account within the ADUC console.

Step 196: I selected the option to enable the user account.

Step 197: I confirmed the change for the "Demoxome Sukud" account.

Step 198: I received the system notification that the object was successfully enabled.

Step 199: I switched to the Client-1 VM to verify the account was active.

Step 200: I entered the password to log in.

Step 201: I reached the desktop to confirm access was restored.

Step 202: I verified the user profile of the account.

Step 203: I opened the PowerShell terminal to perform a final confirmation.

Step 204: I typed the whoami command into the terminal.

Step 205: I viewed the output confirming the correct user session was active.

Step 206: I returned to the Domain Controller desktop

