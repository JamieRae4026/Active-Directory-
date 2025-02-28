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
     When the installation is complete, 




 
