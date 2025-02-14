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
   


4. **Install Windows Server on Domain Controller:**
   - Install Windows Server (2019 or 2022) on the Domain Controller VM.
   - Configure it as the primary Domain Controller for your AD setup.




 
