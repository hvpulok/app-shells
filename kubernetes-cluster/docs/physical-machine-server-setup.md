In Physical machine

# Check external IP address
```bash
curl ifconfig.me
```

# Virtual Box VM Setup

## Install
Ref: https://vitux.com/how-to-install-virtualbox-on-ubuntu/

```bash
sudo add-apt-repository multiverse && sudo apt-get update
sudo apt install virtualbox
sudo apt install virtualbox-ext-pack
```
## Configure Network Mode and port forwarding
Ref: https://www.howtogeek.com/122641/how-to-forward-ports-to-a-virtual-machine-and-use-it-as-a-server/
### Checklist:
Remember that this is only part of the process of making the server software inside a virtual machine reachable. You’ll also need to ensure that:

- The firewall software running inside your virtual machine isn’t blocking the connections. (You may need to allow the server program in the guest operating system’s firewall.)
- The firewall software on your host computer isn’t blocking the connections. (This only applies to NAT mode with port forwarding – the host computer’s firewall doesn’t interfere in bridged networking mode.)
- Your router is forwarding ports correctly – this is only necessary if you want to access the virtual machine from the Internet. (Consult our guide to forwarding ports on routers here.)

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

# SSH setup in server
Ref: https://help.ubuntu.com/lts/serverguide/openssh-server.html

## Useful cmds
```bash
ssh-keygen -t rsa
ssh-copy-id username@remotehost

# Login to remote host
ssh username@remotehost

# Login to remote host using port
ssh -p <portnumber> username@remotehost

# Disable password based login - ChallengeResponseAuthentication no
sudo nano /etc/ssh/sshd_config
sudo systemctl reload ssh
```

## Add host names and ip address mapper in clients for easy ssh

```bash
sudo nano /etc/hosts
```

## Add client ssh public key in **Google Cloud VM** instance
- Edit VM instance
- At the bottom click on SSH Keys and add the key
- Save the changes

## In VM servers, make sudoers password less - suitable for Ansible playbook
Ref: https://code-maven.com/enable-ansible-passwordless-sudo

```bash
ssh foo@192.168.56.11   # ssh to the remote VM server
sudo visudo
# We need to edit the line "%sudo   ALL=(ALL:ALL) ALL" as below
%sudo  ALL=(ALL:ALL) NOPASSWD: ALL
logout
```