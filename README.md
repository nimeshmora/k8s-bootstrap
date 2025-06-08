🐳 Local Kubernetes Cluster Bootstrap with Vagrant & VirtualBox
===============================================================

This project is a **modified and enhanced version** of the open-source project [techiescamp/kubeadm-vagrant](https://github.com/techiescamp/kubeadm-vagrant).It allows you to create a **multi-node Kubernetes cluster locally** on your machine using Vagrant and VirtualBox.

You can use it for:

*   Learning Kubernetes
    
*   Testing Kubernetes tools
    
*   Practicing for CKA/CKAD/CKS exams
    
*   Experimenting with cluster setups — without needing cloud resources.
    

⚖️ License and Attribution
--------------------------

This project is a fork / modified version of [techiescamp/kubeadm-vagrant](https://github.com/techiescamp/kubeadm-vagrant), which is licensed under GPL-3.0.

My modifications are also licensed under GPL-3.0.See LICENSE.md for full license text.

✨ Improvements in This Version
------------------------------

*   Added requirements checker (scripts/check-requirements.sh)
    
*   Added cleanup script (scripts/cleanup.sh)
    
*   Configurable number of worker nodes via settings.yaml
    
*   Version pinning for Vagrant
    
*   Improved and updated documentation
    
*   Simplified usage flow for beginners
    

⚙️ Architecture
---------------
```
+-----------------------+
| VirtualBox VMs |
| |
| +-------------------+ |
| | controlplane | |
| | (master node) | |
| +-------------------+ |
| |
| +-------------------+ |
| | node01 | |
| +-------------------+ |
| |
| +-------------------+ |
| | node02 (optional) | |
| +-------------------+ |
+-----------------------+
```

Number of worker nodes is configurable in settings.yaml.

📋 Requirements
---------------

Before starting, make sure you have:

*   Vagrant >= 2.2.0
    
*   VirtualBox
    

Verify requirements:

``` ./scripts/check-requirements.sh ```

🚀 How to Run
-------------

1️⃣ Clone the Repo

``` git clone cd k8s-bootstrap ```

2️⃣ Start the Cluster

``` vagrant up ```

Vagrant will:

*   Spin up VirtualBox VMs
    
*   Provision control plane & worker nodes
    
*   Configure Kubernetes
    

🕹️ Access the Cluster
----------------------

SSH into Control Plane

``` vagrant ssh controlplane ```

Check Kubernetes Nodes

``` kubectl get nodes ```

Load kubeconfig (optional)

You can also use kubeconfig.txt to connect from your host machine (adjust path if needed):

``` export KUBECONFIG=./kubeconfig.txtkubectl get nodes ```

🛠️ Configuration
-----------------

The number of worker nodes is configurable:

settings.yaml
=============

worker\_nodes: 2

Change the value and run:

``` vagrant up --provision ```

🧹 Cleanup
----------

To destroy the cluster and clean up:

``` ./scripts/cleanup.sh ```

💡 Useful Tips
--------------

Reload Configurations

If you change Vagrantfile or scripts:

``` vagrant reload --provision ```

Access Dashboard

Run inside controlplane node
============================

``` ./scripts/dashboard.sh ```

🗂 Project Structure
--------------------
```
k8s-bootstrap/
├── configs/ # K8s configs (join script, tokens, etc.)
├── scripts/ # Provisioning scripts
│ ├── check-requirements.sh
│ ├── cleanup.sh
│ ├── common.sh
│ ├── dashboard.sh
│ ├── master.sh
│ ├── node.sh
├── settings.yaml # Number of worker nodes
├── Vagrantfile # Main Vagrant config
├── README.md # This file
└── kubeconfig.txt # Optional Kubeconfig
```

🤝 Contributions
----------------

Feel free to fork, improve, and PR!

📄 License
----------

This project is licensed under the GPL-3.0 License.See LICENSE.md for full details.

Original Project: [techiescamp/kubeadm-vagrant](https://github.com/techiescamp/kubeadm-vagrant)