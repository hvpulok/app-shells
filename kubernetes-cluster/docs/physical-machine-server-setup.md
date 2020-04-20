In Physical machine

# Virtual Box VM Setup

## Install
Ref: https://vitux.com/how-to-install-virtualbox-on-ubuntu/

```bash
sudo add-apt-repository multiverse && sudo apt-get update
sudo apt install virtualbox
sudo apt install virtualbox-ext-pack
```

## Uninstall
```bash
sudo apt remove virtualbox
# If you have made any configurations, such as installed an extension package, you can remove VirtualBox and all those by using the following command:
sudo apt purge virtualbox
```

## Useful cmds
```bash
virtualbox
exit

# List virtual machines
VBoxManage list vms

# Start VM in headless mode
VBoxManage startvm <vmName> --type headless

# Power off VM
VBoxManage controlvm <vmName> poweroff
```