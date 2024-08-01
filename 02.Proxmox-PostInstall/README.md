After rebooting Proxmox and successfully logging into the GUI (https://yourIP:8006), open a shell by clicking on your server and then clicking on the `>_Shell` button in the top right corner.

I think it's very useful to run ttech's scripts. (Thank you, ttech, for this excellent work.)

Just copy and paste the following line into the shell window:

```sh
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
It is recommended to answer yes (y) to everything.


Optionally, to reduce the power consumption of the server, you can run the following script from ttech as well:

```sh
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/scaling-governor.sh)"
```

Again optionally, if you want to use hardware transcoding in the future, for example, for Jellyfin or Plex (and you have compatible hardware with Intel QuickSync) or if you want to virtualize a NAS, it is recommended to enable PCI Passthrough.

First, you need to add intel_iommu=on to the /etc/kernel/cmdline. You can do this by running the following command in the shell:

```sh
sudo sed -i 's/$/ intel_iommu=on/' /etc/kernel/cmdline
```

After editing the /etc/kernel/cmdline file, refresh the boot tool by running:

```sh
proxmox-boot-tool refresh
```

And reboot.

