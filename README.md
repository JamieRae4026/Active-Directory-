# Active-Directory-Home-Lab-VirtualBox
Creating my Active Directory Home Lab
Welcome to my repository where I document my journey in setting up an Active Directory (AD) home lab using VirtualBox. This repository contains the step-by-step process, configuration details, and challenges I encountered while building and managing a virtualized Active Directory environment for learning and experimentation.
## Overview
This project involves setting up a fully functional Active Directory environment within VirtualBox. The primary goal is to replicate an enterprise-like AD infrastructure in a controlled, local lab to experiment with various AD concepts, configurations, and tools.
## Lab Setup
The home lab consists of the following components(Disclaimer: Due to limited resources this specs are not ideal):
**Host Machine:** [
CPU: Intel Corei7-6600u 2.60 GHz
RAM:8GB 
Disk Space: 500 HD]
- **Operating Systems:**
  - **Domain Controller (DC):** Windows Server 2016
  - **Client Machine:** Windows 10(for client-side AD operations)
 ### Network Configuration

- The machines are configured on an internal network in VirtualBox to simulate a local environment.
- The domain controller is set up as the primary DNS server.
- All machines are configured with static IPs for ease of management.
## Getting Started

To replicate this setup in your own VirtualBox environment, follow these steps:

1. **Install VirtualBox:**
   - Download VirtualBox from the official site: [https://www.virtualbox.org/](https://www.virtualbox.org/)
   - Install VirtualBox on your machine. (Mine Already Installed)
2. **Create Virtual Machines:**
   - Set up VMs for the Domain Controller, Member Server, and Client Machine.
   - Allocate resources based on your system's capability (e.g., 2-4 GB RAM for each machine).
  
    In this scenario I will only showcase creating a VM for the Domain Controller and Member Server as I already have a Widnows VM which I will use as the client Machine.

   **First step is create a new VM**
   
   ![image](https://github.com/user-attachments/assets/4d12070a-fe96-4a5e-ba5b-9cde7b2f88dc)
   
   Here you provide your name, where you want to store your VM, the type(Microsoft Windows) and version(Windows 2016 64bit)

   **Assign Hardware Configuration**
   
   ![image](https://github.com/user-attachments/assets/98e3e7b2-6a27-4d2e-94c9-026eb92f0644)
   
   I chose 3GB as my base memory because I only have  8GB in my host machine and I don't want to overwhelm it.

   
   **Allocate the size you want it to take**
   
   ![image](https://github.com/user-attachments/assets/c235b16c-1bac-461b-b96e-6a474c1a46c6)

   Here I gave mine 30GB, you can assign yours according to the size of disk you have.
   Click Finish to proceed.


   **Adding the ISO image**
   Before starting the VM you need to add the ISO image that you downloaded. Go to the settings tab and select the storage section.
   Add the ISO image in the Storage Devices.
   
   ![image](https://github.com/user-attachments/assets/01e6eba2-4f0e-477a-b7bc-7e81ec8ba229)

   You can change the network settings to suit your environment but mine remained NAT so that it can communicate with the other VMs.
   You can now click Start to start the VM.
   
   ![image](https://github.com/user-attachments/assets/e65a30d6-d310-41fb-9d2e-9fce7eba6c6d)


   **Installing the WindowsServer**
   This is abit similar to how you will install your Windows 10 with a few tweaks.
   Click Next in the 1st window that you are shown.
   Select te 4th option for Datacentre but with the desktop environment or you will be stuck with the terminal and if you are a beginner it will be very difficult to navigate.
   
   ![image](https://github.com/user-attachments/assets/5a6d7391-bd50-4793-9ecc-8ea5e29f6208)
   
   Accept the License Agreement to proceed.
   Select the Custom Install to do a fresh install.
   Select the storage and click Next, the install will begin.

  ![image](https://github.com/user-attachments/assets/93325e5d-eeea-4003-9d97-c87db87780f4)

  After it is done installing we will br prompted to create a passsword for the administrator account to proceed.
  ![image](https://github.com/user-attachments/assets/e714e065-2b7d-465f-a4d4-06097e54ae42)

  Proceed to Log in

  ![image](https://github.com/user-attachments/assets/485cd36f-6d94-4b78-acd0-78043df5911f)

 And we are in!! Successfully installed!
 ![image](https://github.com/user-attachments/assets/b9f87498-a8b3-4e48-b883-184f4f70fddf)

 Repeat the process to create a 2nd server which we will use as member server.


**Configuring the DC-1**
when the Server powers up a server manager window will open.
Navigate to the Local Server where you will see some information.

![image](https://github.com/user-attachments/assets/6d104699-f7ec-4ef7-86f1-ee0e51cfaff8)


We will start by renaming this to DC-1

![image](https://github.com/user-attachments/assets/2acec078-c42e-4e7a-a397-a84818ac87a8)

Next we enabled Remote Desktop Connection so that we can access the Server through RDP.

![image](https://github.com/user-attachments/assets/511e8fc0-811e-4dc2-80cb-d83db9e67c85)

We can later come and specify which users can connect to the server through RDP.

Next we change the time zone so as to allign with the other servers and client computers.

![image](https://github.com/user-attachments/assets/f3202d96-0c71-4fa8-bc56-554296d32c3b)

Next we change the IP address setting to static IPs.
You can do this through the control panel and set the DBS server to 8.8.8.8 to be able to communicate with the internet.

![image](https://github.com/user-attachments/assets/6ea5acc7-9d5c-40ba-8835-13ff02987b12)

 **Install and Configure Active Directory:**
   - Install the Active Directory Domain Services (AD DS) role.
     Begin by logging into the server you intend to configure. Open Server Manager, which will be your central hub for managing server settings.
     In Server Manager, go to the Dashboard and select Add Roles and Features to initiate the installation of new server roles and features.
     
     ![image](https://github.com/user-attachments/assets/a29e096d-4445-4bfd-9dc3-7791f6f1fab9)

     The Installation Type screen will appear. Choose Role-based or feature-based installation and click Next to proceed.

     ![image](https://github.com/user-attachments/assets/20e11b96-4a26-4a48-ad52-fdfc44f9763e)

     On the Server Selection page, you will be asked to choose a server from your local pool. In this scenario, we only have one server available for selection, which is the server you are currently working on—       DC-01.


     ![image](https://github.com/user-attachments/assets/2f767996-9325-406f-93ac-1ba3abb458a1)

     On the Server Roles tab, find and select Active Directory Domain Services. This option will allow the server to function as the domain controller. Once selected, a prompt will appear, asking to add         
     additional features that are required for the role. Click on Add Features, then click Next.

     ![image](https://github.com/user-attachments/assets/535072f5-b735-4a46-b6ca-71886478e59c)

     Continue clicking Next through the subsequent windows, reviewing the role and feature selections, until you reach the Install button. Once you’re ready, click Install to begin the installation process.
     Allow the installation process to complete. This may take some time, depending on your server’s performance and network speed. Once the installation is finished, your server will be ready for further   
     configuration, including promoting it to a domain controller.


     ![image](https://github.com/user-attachments/assets/c4e5aa8b-da46-49b5-a3f8-07231fce2b07)

    
   - Promote the server to a Domain Controller (e.g., `lab.local`).
     Once the AD DS installation completes, you will see an option to Promote this server to a      domain controller. Click on this option to begin the promotion process.

     ![image](https://github.com/user-attachments/assets/23b6f23d-decb-4325-8c80-44b3933ac01e)

     This action will take you to the Deployment Configuration page. In this tab, you will be       asked to specify the configuration for the domain controller.
     1. **Select "Add a new forest"**
        Since this is a new environment and there is no existing Active Directory domain, we need to create a new forest. The forest is the highest-level container in Active Directory, and it holds one or more           domains. By choosing the Add a new forest option, we are essentially setting up a brand-new Active Directory environment from scratch.

     **Why are we choosing this option?**
     We are selecting Add a new forest because there is no existing domain or Active Directory infrastructure. If you were adding a domain controller to an existing forest, you would choose the Add a domain           controller to an existing domain option instead. Since we’re starting a fresh environment, creating a new forest allows us to establish the root domain of the forest, which will later be used for our             network's domain structure.

     **Configure Domain Name**
     After selecting Add a new forest, you will be prompted to provide a Root Domain Name. In this example, we will use lab.local, but you should choose a domain name that aligns with your organization’s naming       conventions.

     ![image](https://github.com/user-attachments/assets/0c20c09d-3916-4d6f-a064-e025c363f145)

     **Domain Controller Options**
      In this tab, you will configure the core settings of your domain controller.
     **Domain Controller Capabilities**:
     **Global Catalog**
     A Global Catalog server stores a partial replica of all objects in the forest, which helps with quick searches and logon operations across the domain. It's typically enabled for the first domain controller       in the forest.

     **Domain Name System Server**
     If you selected DNS server as an option, the domain controller will also act as a DNS server, which is necessary for Active Directory to function properly (as DNS is required for domain controllers to            locate each other and the resources in the domain).

      **Read-Only Domain Controller (RODC):**
      This option allows you to promote a Read-Only Domain Controller, which is typically used for remote or branch offices that need domain services but don't require the full Active Directory write access.
     
      **Directory Services Restore Mode (DSRM) password:**
      DSRM is a special mode used to restore Active Directory. The DSRM password is required to boot into this mode. You will need to enter a secure password to ensure the safety of the system in case of a             directory recovery.

     ![image](https://github.com/user-attachments/assets/4a85606b-5b49-4738-93b5-c56d4a37e35b)

     **DNS Options Tab:**
     This tab is relevant if you're also configuring the server to act as a DNS server (which is recommended).
     **DNS Delegation:**
     If this is the first domain controller in your environment, the server will automatically create a DNS delegation. This is used for forward lookup zones to resolve domain names within the network.
     Important Note: If you are setting up DNS on this server, ensure that the DNS server checkbox is selected in the Domain Controller Options tab.

     ![image](https://github.com/user-attachments/assets/91e3b156-75e6-4124-b0de-378783408bd9)


 ** Additional Options Tab:**
  This tab is where you configure additional settings related to replication and domain controller options.
  **Site Name**
  Active Directory uses Sites to define physical locations or network segments where domain controllers are located. Typically, the default Default-First-Site-Name will be selected unless you have created custom   sites for your network.

  ![image](https://github.com/user-attachments/assets/c9554ee7-b9cd-4d69-be61-a0129d5eb142)

**Paths Tab:**
This tab lets you specify where the Active Directory database and log files will be stored.

Database, Log Files, SYSVOL:

Database: The NTDS.dit file, where the Active Directory database is stored.
Log Files: Files used to track changes to Active Directory data, ensuring that the database can be replicated correctly.
SYSVOL: A shared folder that stores server logon scripts, Group Policy objects, and other data that must be replicated to other domain controllers.
Important Note: By default, these are stored in C:\Windows\NTDS for the database, C:\Windows\NTDS\Logs for logs, and C:\Windows\SYSVOL for SYSVOL. You can choose custom paths, especially if you are setting up a large Active Directory environment and want to optimize disk performance.

![image](https://github.com/user-attachments/assets/a1f0dbe1-7914-4124-b8f5-9a79dbc9b94b)


** Review Tab:**
In this tab, you will see a summary of all the configuration settings you’ve chosen so far. It is important to review these settings before proceeding to ensure everything is set up correctly.

![image](https://github.com/user-attachments/assets/1ae709b1-1468-4aef-a2d7-6781bfdcf929)


Verify Settings:
Double-check your selected options, such as the domain name (lab.local), DNS settings, the DSRM password, and paths for the database and logs.
7. Install Tab:
Once all options have been reviewed and confirmed, you can click the Install button. The server will then begin the process of promoting itself to a domain controller.

![image](https://github.com/user-attachments/assets/347366f1-cc0f-4cbd-a975-41c14d7c7803)

Progress and Completion:
The promotion process may take several minutes, depending on your server's performance and configuration. Once complete, the server will restart, and you will have a fully functioning domain controller for your lab.local domain.
