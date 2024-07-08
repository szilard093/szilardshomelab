# Proxmox Installation Guide

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Step 1: Prepare Installation Media](#step-1-prepare-installation-media)
- [Step 2: Boot from Installation Media](#step-2-configure-bios-(GPU-Passthrought))
- [Step 3: Install Proxmox VE](#step-3-install-proxmox-ve)
- [Step 4: Initial Configuration](#step-4-initial-configuration)
- [Step 5: Access the Proxmox Web Interface](#step-5-access-the-proxmox-web-interface)
- [Conclusion](#conclusion)

## Introduction

Proxmox Virtual Environment (VE) is an open-source server virtualization environment. It allows you to easily manage VMs, containers, storage, and networks using an integrated web interface.

## Prerequisites

Before you begin, ensure you have the following:

- A USB flash drive with at least 2GB capacity.
- Proxmox VE ISO image [Download here](https://www.proxmox.com/en/downloads).
- Internet connection for updates and package installation.

## Step 1: Prepare Installation Media

1. Download the Proxmox VE ISO image from the [Proxmox website](https://www.proxmox.com/en/downloads).
2. Use a tool like [Rufus](https://rufus.ie/) to create a bootable USB drive.

   **Using Rufus:**
   - Open Rufus and select your USB drive.
   - Select the Proxmox VE ISO file.
   - Click `Start` and wait for the process to complete.

## Step 2: Configure BIOS (GPU Passthrought)

1. 	Enable Virtualization Technology:

	•	Look for a setting named Intel VT-x, Intel Virtualization Technology, AMD-V, or something similar. This is usually found under the Advanced or CPU Configuration tab.

	•	Set it to Enabled.

2.	Enable IOMMU:

    •	Locate the IOMMU setting, which might be under Advanced, North Bridge, South Bridge, or AMD CBS depending on your motherboard.

	•	Set it to Enabled.

3. 	Enable PCIe ACS Override (if available):

	•	This setting may help with splitting IOMMU groups, necessary for successful GPU passthrough.
    
	•	It might be found under Advanced settings or similar.    

## Step 3: Install Proxmox VE

    •	Once booted from the USB, you will see the Proxmox installer boot menu.
	•	Select Install Proxmox VE and press Enter.
	•	Accept the End User License Agreement (EULA).
    • Select the target hard drive for the installation. 
        - During the disk selection process, you will be given the option to select the filesystem. It is recommended to choose `ZFS` for its advanced features like snapshots and data integrity protection.
        - Select `ZFS` as the file system type.
        - Choose the desired ZFS RAID level (e.g., RAID 1, RAID 10) based on your hardware configuration and redundancy needs.
	•	Configure the country, time zone, and keyboard layout. Click Next.
	•	Set a strong password for the root user and provide a valid email address. Click Next.
	•	Configure the network interface with a static IP address, netmask, gateway, and DNS server. Click Next.
	•	Review the installation summary and click Install.

The installation process will begin and may take several minutes to complete. Once finished, the system will prompt you to reboot.