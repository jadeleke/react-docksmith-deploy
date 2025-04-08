# react-docksmith-deploy

Kubernetes deployment configuration for the `react-docksmith` app.

## Overview

This repository contains the Kubernetes manifests required to deploy the `react-docksmith` Docker container on a local Kubernetes cluster using Minikube. We highly recommend using [Minikube](https://minikube.sigs.k8s.io/docs/start/) for local development and testing. All the deployment steps, including applying the manifest and accessing the app, are described below.

## Prerequisites

Make sure you have the following installed on your Windows system:

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

## Docker Image

- **Image:** `adeleke1/react-docksmith`
- **Tag:** `v1.1.0`
- **Docker Hub:** [adeleke1/react-docksmith](https://hub.docker.com/r/adeleke1/react-docksmith)

## Deployment Files

- `deployment.yaml`: Contains both the Deployment and the Service definitions for Kubernetes.

## How to Use

### 1. Start Minikube

Open your terminal (Command Prompt or PowerShell) and start Minikube by running:

```bash
minikube start
```

### 2. Apply the Deployment

In the repository directory (where your `deployment.yaml` is located), run:

```bash
kubectl apply -f deployment.yaml
```

This will create:

- A Deployment that pulls the Docker image `adeleke1/react-docksmith:v1.1.0`.
- A NodePort Service that exposes the app on port 3000 (and NodePort 32313 in this example).

### 3. Access the Application

After applying the deployment, access your app by running:

```bash
minikube service react-docksmith-service
```

This command will automatically open your default browser with the URL that routes to your application. If it does not open automatically, note the URL in the terminal output (for example, `http://127.0.0.1:51934` or similar) and open it manually.

## Notes

**Updating the Image:**  
If you build and push a new version of your Docker image, update the `image:` field in `deployment.yaml` to reflect the new tag and re-run:

```bash
kubectl apply -f deployment.yaml
```

**Debugging:**  
To see logs for troubleshooting, run:

```bash
kubectl logs deployment/react-docksmith
```

**Minikube Recommendation:**  
This deployment repository is configured with Minikube in mind. If deploying to another Kubernetes environment, you might need to adjust service types and NodePort settings accordingly.

## Additional Resources

- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [Docker Hub Repository](https://hub.docker.com/r/adeleke1/react-docksmith)

