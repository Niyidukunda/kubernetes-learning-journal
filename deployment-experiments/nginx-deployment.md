    markdown
# NGINX Deployment Experiment

This file documents how I deployed a basic NGINX web server to my Minikube cluster using a Kubernetes Deployment manifest.

## Objective

Demonstrate how to create and apply a deployment manifest in YAML format using `kubectl`, and observe how Kubernetes manages pods through declarative instructions.

## Deployment Manifest

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
Steps to Deploy
Save the YAML manifest to a file:

bash
touch deployment-experiments/nginx-deployment.yaml
Paste the above YAML content into the file and save it.

Apply the manifest to your cluster:

bash
kubectl apply -f deployment-experiments/nginx-deployment.yaml
Verify the deployment:

bash
kubectl get deployments
kubectl get pods
Optionally expose the deployment:

bash
kubectl expose deployment nginx-deployment --type=NodePort --port=80
minikube service nginx-deployment
This command creates a NodePort service and opens it in your default browser.

Reflections
The YAML manifest defines the desired state of the deployment.

Kubernetes automatically creates and maintains two NGINX pods (as specified in replicas: 2).

The kubectl apply command allows declarative resource management.

Label matching ensures the deployment knows which pods it controls.

Exposing the deployment creates a service so I can access it externally from the browser.

Troubleshooting
If the YAML file isn’t recognized, verify its path with:

bash
ls deployment-experiments/
If pods don’t start, check:

bash
kubectl describe deployment nginx-deployment
kubectl get events
If minikube service fails to launch in browser, inspect port binding and try:

bash
minikube service nginx-deployment --url




