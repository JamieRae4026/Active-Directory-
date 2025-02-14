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

  






4. **Install Windows Server on Domain Controller:**
   - Install Windows Server (2019 or 2022) on the Domain Controller VM.
   - Configure it as the primary Domain Controller for your AD setup.




 
