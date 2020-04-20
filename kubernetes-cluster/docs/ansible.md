Ref:
[Setup Guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-18-04#step-1-%E2%80%94-installing-ansible)

```bash
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible

# List hosts
ansible-inventory --list -y
ansible-inventory --list -y -i ./hosts # from local hosts file

# Testing Connection
ansible all -m ping -u <username>
ansible all -m ping -u hvpulok -i ./hosts

# Running Ad-Hoc Commands 
ansible all -a "df -h" -u <username>
```