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