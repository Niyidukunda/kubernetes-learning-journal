# NGINX Deployment and NodePort Service

This entry documents the creation of a basic NGINX Deployment with two replicas and exposes it externally using a NodePort Service — ideal for running on Minikube during local testing.

---

## 📄 Manifest Location

See `deployment-experiments/nginx-deployment.yaml` for the raw Kubernetes configuration.

---

## ⚙️ Commands to Apply in Minikube

```bash
kubectl apply -f deployment-experiments/nginx-deployment.yaml
kubectl get pods,svc
minikube service nginx-service
