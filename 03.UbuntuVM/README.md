# Installing Ubuntu 24.04 Server on Proxmox

## Steps

### 1. Download Ubuntu 24.04 Server ISO

1. Go to the [official Ubuntu download page](https://ubuntu.com/download/server).
2. Download the Ubuntu 24.04 Server ISO image.

### 2. Upload the ISO to Proxmox

1. Open your Proxmox web interface.
2. Navigate to `Your Node` -> `local` where you want to upload the ISO.
. Choose `ISO Image` as the content type and upload the downloaded Ubuntu 24.04 Server ISO.

### 3. Create a New Virtual Machine

1. In the Proxmox web interface, go to `Datacenter` -> right clcik on the`Node` -> and click on `Create VM`.
2. Fill in the basic configuration:
   - **VM ID**: Choose a unique ID. ex. 100
   - **Name**: Provide a name for your VM. ex Ubuntu24.04
   - Check the start at boot.
3. Click `Next`.

### 4. Configure VM Settings

1. **OS**:
   - Select `Linux` as the operating system.
   - Choose `Version` from the version dropdown, and select `6.x - 2.6 Kernel`.
   - Choose `ISO image` what You downloaded.
   - Click `Next`.

2. **System**:
   - Choose `Graphic card`: Default
   - Choose `SCSI Controller`: VirtlO SCSI Single
   - Choose `Machine`: q35 - if You want GPU passthroug
   - Check the `Qemu Agent`
   - Click `Next`.

3. **Disk**:
   - Choose the storage location and size for your VM disk.
   - Use the default settings or adjust as needed.
   - If You are using an SSD check the SSD emulation and Discard.
   - Click `Next`.

4. **CPU**:
   - Configure the number of cores and type of CPU (I prefer HOST).
   - Click `Next`.

5. **Memory**:
   - Allocate memory (RAM) for your VM.
   - Click `Next`.

6. **Network**:
   - Choose the network bridge and configure network settings.
   - Click `Next`.

7. **Confirm**:
   - Review the settings and click `Finish` to create the VM.

### 5. Start the VM and Install Ubuntu

1. Go to the `Summary` tab and click `Start` to power on the VM.
2. Open the `Console` tab to view the VM console.
3. Follow the on-screen instructions to install Ubuntu 24.04 Server:
   - Choose the language and keyboard layout.
   - Select `Install Ubuntu Server`.
   - Follow the prompts to configure network settings, disk partitioning, and user account setup.
   - Complete the installation and reboot the VM when prompted.

### 7. Post-Installation

1. Remove the Ubuntu ISO from the VM’s CD/DVD drive:
   - Go to the `Hardware` tab.
   - Click on `CD/DVD Drive`, then `Edit`.
   - Choose `Do not use any media`.
   - Click `OK`.

2. Restart the VM to boot into the newly installed Ubuntu 24.04 Server.

In the next step we will run my custom installer menu [Step 04](../04.Installer/README.md).