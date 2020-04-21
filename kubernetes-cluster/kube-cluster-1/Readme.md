Ref:
https://www.digitalocean.com/community/tutorials/how-to-create-a-kubernetes-cluster-using-kubeadm-on-ubuntu-18-04

# Ansible cmds
```bash
ansible all -m ping -u admin -i ./hosts # Ping

ansible-playbook -i hosts ./initial.yml
ansible-playbook -i hosts ./kube-dependencies.yml
ansible-playbook -i hosts ./master.yml
```

# Kube cmds
```bash
ssh -p 2200 admin@hvserver1         # Login to master node
kubectl get nodes                   # Get kube nodes
```