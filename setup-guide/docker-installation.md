# Docker Installation on Ubuntu

This guide documents the steps I followed to install Docker Engine on my Ubuntu VM, preparing for container-based development with Kubernetes.

##  Prerequisites

- Ubuntu 20.04 or later
- `sudo` access
- Internet connection

##  Installation Steps

1. **Update system packages**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install dependencies**
   ```bash
   sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release -y
   ```

3. **Add Docker’s GPG key**
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/docker-archive-keyring.gpg > /dev/null
   ```

4. **Add Docker’s APT repository**
   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
   https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
   | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

5. **Install Docker Engine**
   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io -y
   ```

6. **Verify installation**
   ```bash
   docker --version
   sudo systemctl status docker
   ```

7. **(Optional) Run Docker as non-root**
   ```bash
   sudo usermod -aG docker $USER
   newgrp docker
   ```

## What I Learned

- Docker runs as a system service — use `systemctl` to check its status or enable it at boot.
- The `dpkg --print-architecture` command ensures compatibility with your CPU architecture.
- If `docker` requires `sudo`, user group permissions likely need to be updated.

## Troubleshooting Notes

- After installing, I had to **restart my terminal** to activate group changes.
- On one attempt, the Docker binary was broken — fixed by reinstalling and verifying the repo’s GPG key.

---
