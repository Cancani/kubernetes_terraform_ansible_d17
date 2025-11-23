🚀 Install Kubernetes Cluster Using Ansible on Ubuntu 24.04

📝 Introduction

Setting up a Kubernetes cluster on Ubuntu 24.04 manually can be a time-consuming and error-prone task. Ansible—a powerful open-source automation tool—simplifies this process by automating the provisioning and configuration of all required components. This guide will walk you through deploying a production-ready Kubernetes cluster on Ubuntu 24.04 using Ansible roles. This guide should show you how to setup the Kubernetes cluster on a AWS infrastructure setup by this [Terraform Manifest](../terraform/)

✅ Prerequisites

Before proceeding, ensure the following requirements are met:

    A stable internet connection

    A control node (Ubuntu 24.04) with Ansible installed

    At least two Ubuntu 24.04 nodes (1 Master + 1 Worker)

    SSH access from the control node to all target nodes

    A non-root user with sudo privileges on all nodes

    Basic knowledge of Ansible and Kubernetes

⚙️ System Preparation

Perform these steps on all nodes unless specified otherwise.
Step 1: Update Packages

```
sudo apt-get update
sudo apt-get install -y python3 python3-pip
```

🛠️ Install Ansible (Control Node Only)

python -m venv ansible_aws
source ansible_aws/bin/activate
pip3 install --upgrade pip
pip3 install ansible-core boto3 awscli
ansible-galaxy collection install amazon.aws

▶️ Run the Ansible Playbook

Execute the playbook to deploy the Kubernetes cluster:

ansible-playbook -i 03amazon.aws_ec2.yml cluster-setup.yml -u ubuntu

🔍 Validate the Cluster

Check the file /tmp/mastersummary.txt for the passwords of the Apps and Ports to connect.

📌 Conclusion

You’ve successfully deployed a Kubernetes cluster on Ubuntu 24.04 using Ansible. This automated method ensures consistency, reduces manual errors, and accelerates future scaling or changes.

Feel free to contribute or expand this setup by adding roles for monitoring, logging, ingress controllers, or Helm.
