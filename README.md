#Kubernetes Learning Journal

An interactive learning journal documenting my journey into Kubernetes, containers, and Linux.

Welcome to my technical learning journal — a personal record of my practical exploration into Kubernetes, containers, and Linux system administration.

This repository captures my practical experience, challenges, and achievements as I explore concepts like containerization, orchestration, and command-line tools.

#Mission

This repository serves as a resource for anyone looking to understand Kubernetes and its ecosystem. It aims to provide:

Step-by-step guides for setting up and using Kubernetes tools

Reflections on challenges and solutions encountered during the learning process

Practical examples and use cases for Kubernetes in real-world scenarios

#Tech Stack

Kubernetes: For container orchestration

Minikube: To create a local Kubernetes cluster

Linux: As the foundational operating system

kubectl: The command-line tool for interacting with Kubernetes

kubectl Installation Guide

This file documents how I installed and configured kubectl, the Kubernetes command-line tool, to interact with my Minikube cluster.

##Prerequisites

Minikube already set up and running

Access to a terminal with internet connection

User account with sudo privileges

Installation Steps

##Download the latest kubectl binary:

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
# -L tells curl to follow redirects
# -O saves the file with its original name

Make the binary executable:

chmod +x kubectl
# Makes the binary executable

Move it to your system path:

sudo mv kubectl /usr/local/bin/
# Moves kubectl into your system path so it’s accessible globally

Verify installation:

kubectl version --client

Initial Usage

To check node status:

kubectl get nodes

To view running pods:

kubectl get pods --all-namespaces

To inspect cluster components:

kubectl cluster-info

##Reflections

kubectl acts as the bridge between me (the user) and the Kubernetes API server. It interprets my commands and interacts with the cluster accordingly.

Each resource type in Kubernetes (pods, deployments, services) can be managed using kubectl through commands like apply, describe, and delete.

curl -LO combines two flags: -L follows URL redirects, and -O saves the file using its name from the server.

chmod +x ensures the downloaded binary can be executed as a program.

Moving it to /usr/local/bin/ places it in the system path, making it available from any terminal session.

Troubleshooting

If kubectl is not found after installation, ensure /usr/local/bin/ is in your system PATH.

Check for typos in commands or missing dependencies.

Verify that the downloaded binary matches your system architecture (e.g., amd64 for 64-bit systems).