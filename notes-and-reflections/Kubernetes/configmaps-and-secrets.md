# ConfigMaps and Secrets in Kubernetes

This entry explores how Kubernetes handles application configuration and sensitive data using ConfigMaps and Secrets. These resources decouple configuration from your container images, promoting flexibility, security, and portability across environments.

---

## What is a ConfigMap?

A **ConfigMap** stores non-sensitive configuration data as key-value pairs. It can be consumed by Pods as:

- Environment variables
- Command-line arguments
- Mounted files inside containers

###  Example: ConfigMap YAML

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_MODE: production
  APP_DEBUG: "false"

```
##  What is a Secret?
A Secret stores sensitive data like credentials, tokens, or keys. All values must be base64 encoded.

 Example: Secret YAML
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
type: Opaque
data:
  DB_PASSWORD: cGFzc3dvcmQxMjM=     # password123 (encoded)
                                    
# To encode a string in base64 on Linux:

bash
echo -n 'password123' | base64

## Consuming Configs in Pods
You can mount ConfigMaps and Secrets into Pods as env vars:

yaml
spec:
  containers:
  - name: app-container
    image: myapp:1.0
    envFrom:
    - configMapRef:
  spec:
  containers:
  - name: app-container
    image: myapp:1.0
    envFrom:
    - configMapRef:
        name: app-config
    - secretRef:
        name: app-secret
      name: app-config
    - secretRef:
        name: app-secret
#Or as volume files:

yaml
volumes:
  - name: config-volume
    configMap:
      name: app-config

### Reflections

```ConfigMaps keep deployments flexible by separating logic from configurati
Secrets enforce basic security hygiene, but require further protection (e.g. RBAC, encryption at rest).

Minikube allows testing config injection easily with simple Pods and kubectl describe.

### References
```ConfigMap YAML: deployment-experiments/app-configmap.yaml

Secret YAML: deployment-experiments/app-secret.yaml

Pod YAML: deployment-experiments/app-with-config.yaml


