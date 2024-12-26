# Update kubernetes cluster to next version

Updating kubernetes cluster version is part of the yearly activity carried out by DevOps or kubernetes admins across organisations. Some updates of kubernetes will bring changes to the api versions and it might break our application.

### Task

My custom kubenetes cluster is running on 1.31.3, Update it to the next version available and make sure all the components running as expected. In my case next version available is 1.31.4.


### Steps to update the kubernetes cluster

```
# First we need to update the control plane node

# getting the kubeadm package
apt-mark unhold kubeadm kubelet
apt upgrade kubeadm=1.31.4-1.1

# Unschedule the control plane node and upgrading it
kubectl drain master
kubectl cordon master --ignore-deamonsets=true --empty-data-dir=true
kubeadm upgrade apply 1.31.4

# restart kubelet and uncordon the master node
systemctl restart kubeadm
kubectl uncordon master

# repeat similar steps in worker nodes, except kubeadm
kubeadm upgrade node # it should be run inside worker nodes
```

Before upgrade

```
root@master:/home/master# kubectl get nodes
NAME      STATUS   ROLES           AGE     VERSION
master    Ready    control-plane   6d16h   v1.31.3
worker1   Ready    <none>          6d16h   v1.31.3
```

After upgrade

```
root@master:/home/master# k get nodes
NAME      STATUS   ROLES           AGE     VERSION
master    Ready    control-plane   6d17h   v1.31.4
worker1   Ready    <none>          6d17h   v1.31.4
```