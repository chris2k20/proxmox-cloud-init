# Proxmox: Use Custom Cloud-Init File (User-Data)

How to use a custom Cloud-Init YAML-File with Proxmox: 

*Assumption: In your proxmox environment is a VM with ID 9001 and cloud-init installed (run [Ubuntu Cloud Image Template on Proxmox](https://gist.github.com/chris2k20/dba14515071bd5a14e48cf8b61f7d2e2) & create VM from template & come back:)*

1. Enable `Snippets` in Datacenter -> Storage -> local -> mark `Snippets`
2. `cd` into `/var/lib/vz/snippets`
3. Download the example [cloud-init.yml](./cloud-init.yml) file and save it to 9001-cloud-init.yml: `wget https://raw.githubusercontent.com/chris2k20/proxmox-cloud-init/main/cloud-init.yml -O 9001-cloud-init.yml`
4. Customize it: `nano 9001-cloud-init.yml` (See [official cloud-init Documentation](https://cloudinit.readthedocs.io/en/latest/topics/examples.html))
5. Update the VM settings to use your default cloud-init: `qm set 9001 --cicustom "user=local:snippets/9001-cloud-init.yml"`
6. *Optional* Create from VM 9001 Template.
7. Start VM: `qm start 9001`

I used Ubuntu 20.04 Cloud Image to test it out (see my little gist on: [How to install a Ubuntu Cloud Image Template on Proxmox](https://gist.github.com/chris2k20/dba14515071bd5a14e48cf8b61f7d2e2)). 

Feel free to comment or send a pull request. Thank you :hugs:
