# Proxmox: Use Custom Cloud-Init File (User-Data)

How to use a custom Cloud-Init YAML-File with Proxmox: 

1. Create a folder in the default proxmox path on the host: `mkdir /var/lib/cloud-init/`
2. Save the example [cloud-init.yml](cloud-init.yml) file to the new folder, eg: `/var/lib/vz/cloud-init/1001-cloud-init.yml` (1001 is my VM ID)
3. Customize it: See [official cloud-init Documentation](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)
4. Update the VM to use your default cloud-init: `qm set 1001 --cicustom "user=local:cloud-init/1001-cloud-init.yml"`
5. Start VM: `qm start 1001`

I used Ubuntu 20.04 Cloud Image to test it out (see my little gist on: [How to install a Ubuntu Cloud Image Template on Proxmox](https://gist.github.com/chris2k20/dba14515071bd5a14e48cf8b61f7d2e2)). 

Feel free to comment or send a pull request. Thank you :hugs:
