# Overview of Kubernetes

- Kubernetes is an opensource container orchestration tool, which is managed by CNCF (cloud native computing foundation). Google has developed it and given to CNCF.

It works in a distributed architecutre, where a group of compute instance work together to run applications with high availability, scalability, self healing and easy to monitor capabilities.

Compute instance in kubernetes are know as nodes. Nodes are of two types Master Node and Worker Node.

Master Node contains kubernetes control plane, it controls and schedules the workloads on the worker nodes.
Worker nodes connects to control plane and runs the containers also knows as pods.

Kubeadm is the kubernetes administrative tool which runs on all nodes and manages the worker nodes to connect to control plane.
- Below are kubeadm commands
    - kubeadm init # to bootstrap a kubernetes control plane node
    - kubeadm join  # to connect a worker node to control plane node
    - kubeadm --help # to learn more commands

kubelet is the node agent one which runs on every node for running the pods on the worker nodes.



## Task (To create custom kubernetes cluster)

We are going to create a new kubernetes cluster with control plane and single worker node, we can add more worker nodes if required.


### Setting up Master Node

- We are using Virtual Machines to create the kubernetes cluster, you can also use Virtual Machines available over Cloud environments like AWS, Azure, GCP and so on.
- Using Ubuntu OS for setting up the cluster.
- First step is to install the required packages to the OS.
    - apt install kubeadm, kubelet, crio, 



kubeadm link :- https://dl.k8s.io/v1.31.3/bin/linux/amd64/kubeadm
kubelet link :- https://dl.k8s.io/v1.31.3/bin/linux/amd64/kubelet


VERSION="v1.31.1" # check latest version in /releases page
wget https://github.com/kubernetes-sigs/cri-tools/releases/download/$VERSION/crictl-$VERSION-linux-amd64.tar.gz
sudo tar zxvf crictl-$VERSION-linux-amd64.tar.gz -C /usr/local/bin
rm -f crictl-$VERSION-linux-amd64.tar.gz