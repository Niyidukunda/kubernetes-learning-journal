markdown
# kubectl Installation Guide

This file documents how I installed and configured `kubectl`, the Kubernetes command-line tool, to interact with my Minikube cluster.

## Prerequisites

- Minikube already set up and running
- Access to a terminal with internet connection
- User account with sudo privileges

## Installation Steps

1. Download the latest `kubectl` binary:
   ```bash
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
Make the binary executable:

bash
chmod +x kubectl
Move it to your system path:

bash
sudo mv kubectl /usr/local/bin/
Verify installation:

bash
kubectl version --client
Initial Usage
To check node status:

bash
kubectl get nodes
To view running pods:

bash
kubectl get pods --all-namespaces
To inspect cluster components:

bash
kubectl cluster-info
Reflections
kubectl acts as the bridge between me (the user) and the Kubernetes API server. It interprets my commands and interacts with the cluster accordingly.

Each resource type in Kubernetes (pods, deployments, services) can be managed using kubectl through commands like apply, describe, and delete.

Troubleshooting
If kubectl isn't recognized, check that it's in your $PATH:

bash
echo $PATH
If the client can't connect to the cluster, verify that Minikube is running:

bash
minikube status

---
curl -LO combines two flags: -L follows URL redirects, and -O saves the file using its name from the server.

chmod +x ensures the downloaded binary can be executed as a program.

Moving it to /usr/local/bin/ places it in the system path, making it available from any terminal session.

