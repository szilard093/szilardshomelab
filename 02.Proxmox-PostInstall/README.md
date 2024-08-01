Setting Up Proxmox Post-Installation

After rebooting Proxmox and successfully logging into the GUI (https://yourIP:8006), follow these steps to configure your server:

1. Access the Shell

	1.	Open the Proxmox web interface.
	2.	Click on your server in the left sidebar.
	3.	Click the >_ Shell button in the top right corner.

2. Run ttech’s Scripts (Thank you, ttech, for this excellent work.)

Run the Post-Installation Script:

Copy and paste the following line into the shell window:

```sh
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
It is recommended to answer yes (y) to everything.

(Optional) Optimize Power Consumption:

If you want to reduce the power consumption of your server, you can run this script:


```sh
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/scaling-governor.sh)"
```

3. Enable PCI Passthrough (Optional)

Add IOMMU Support:


	1.	Edit the /etc/kernel/cmdline file to include intel_iommu=on. Run:


If you plan to use hardware transcoding (e.g., for Jellyfin or Plex with Intel QuickSync) or virtualize a NAS, enabling PCI Passthrough is recommended.


```sh
sudo sed -i 's/$/ intel_iommu=on/' /etc/kernel/cmdline
```


	2.	Refresh the boot configuration with:

```sh
proxmox-boot-tool refresh
```

	3.	Reboot the server.


Verify IOMMU Support:

After rebooting, check if IOMMU is enabled by running:

```sh
dmesg | grep -i IOMMU
```

If you see relevant output, IOMMU is successfully enabled!


![Screenshot 2024-08-01 at 20 26 44](https://github.com/user-attachments/assets/48251fad-2c9c-4afe-8960-50f605e72776)

