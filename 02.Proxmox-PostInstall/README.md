After rebooting Proxmox and successfully logging into the GUI (https://yourIP:8006), open a shell by clicking on your server and then clicking on the `>_Shell` button in the top right corner.

I think it's very useful to run ttech's scripts. (Thank you, ttech, for this excellent work.)

Just copy and paste the following line into the shell window:

```sh
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
It is recommended to answer yes (y) to everything.


Optionally, to reduce the power consumption of the server, you can run the following script from ttech as well:

sh

bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/scaling-governor.sh)"