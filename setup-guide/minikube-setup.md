# Minikube Setup Guide

This guide explains how I installed and configured Minikube to run a local Kubernetes cluster on my Ubuntu system.

## Prerequisites

- Ubuntu 20.04 or newer
- Docker Engine installed and running
- Virtualization enabled in BIOS (VT-x or AMD-v)
- Terminal access with curl and sudo available

## Installation Steps

1. Download the Minikube binary:
   ```bash
   curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
Install the binary to your system path:

bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
Verify that Minikube is accessible:

bash
minikube version
Starting the Cluster
Start Minikube using Docker as the driver:

bash
minikube start --driver=docker
Confirm cluster status:

bash
minikube status
Check active node:

bash
kubectl get nodes
Notes and Reflections
The --driver=docker option avoids the need for VirtualBox or KVM. Since Docker was already installed, this was the smoothest integration.

The first startup took a few minutes and required an internet connection to download necessary images.

I realized that Minikube creates a VM-like environment managed by Docker, which acts as a single-node Kubernetes cluster.

Troubleshooting
If minikube start fails, check Docker's status:

bash
sudo systemctl status docker
If kubectl is not recognized, ensure it is installed and in your $PATH.


---
