 This is the contains config file of  k8s clsuter with Vagrant and ansible.

Getting started
--------------
- Prerequisite
- Vagrant
- Virtualbox
- Ansible

Setup
-----
We will start by creating an empty folder that will contain all required files to quickly start and create local kubernetes cluster

Provisioning nodes using Vagrant
--------------------------------
We will be setting up a Kubernetes cluster that will consist of one master and two worker nodes. To accomplish that, we will be using Vagrant and VirtualBox to quickly provision virtual machines.

Create a dedicated SSH key pair to connect to the VMs:

ssh-keygen -b 4096

agrantfile
Create Vagrantfile [use repo Vagrantfile script]

To provision one master node with 2 CPU and 2GB of RAM, and two worker nodes with 1 CPU and 2GB RAM each, add the following to the newly created Vagrantfile:

Ansible
Once we have virtual machines ready, we can start configuring them installing the required packages. Before we begin looking at the Ansible Playbooks, we must first configure Ansible to interact with the VMs (Kubernetes nodes).

Create a hosts.yml file that will contain IP addresses and SSH credentials to VMs

touch hosts.yml[use repo IP_hosts.yml script]

Configure nodes and install kubernetes

ist of actions that the playbook will do:

Install required apt packages
Disable swap
Enable and load Kernel modules
Add Kernel settings
Install containerd runtime
Add apt repo for kubernetes
Install Kubernetes components

Initialize master node
Create playbook for master node

touch master-node-init.yml[use repo master-node-init.yml]

Initialize worker nodes
Create playbook for worker nodes

touch worker-node-init.yml [use repo worker-node-init.yml]

To configure k8s dashboard and metrix server[use repo Install_Kubernetes_Dashboard]
for exposing as nodePortwith RBAC [use repo dashboard-service.yaml] 
