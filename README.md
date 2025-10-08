# Next.js Dockerized Application with Minikube

## Overview

This repository contains a **Next.js application** containerized using **Docker** and deployed on a local **Minikube** Kubernetes cluster. It uses **GitHub Actions** for continuous integration and delivery (CI/CD), automating the Docker image build and deployment process.

### Prerequisites

Make sure you have the following tools installed on your system:

* **Docker**: For building and running containers.
* **Minikube**: For running a local Kubernetes cluster.
* **kubectl**: Kubernetes CLI for interacting with the cluster.
* **GitHub Account**: For storing code and CI/CD using GitHub Actions.

---

## Setup Instructions

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/nextjs-devops-assessment.git
cd nextjs-devops-assessment
```

### Step 2: Build and Run the Application Locally

To run the application locally (before deploying to Kubernetes), follow these steps:

1. **Install dependencies**:

   ```bash
   npm install
   ```

2. **Start the development server**:

   ```bash
   npm run dev
   ```

3. Visit [http://localhost:3000](http://localhost:3000) in your browser to see the app in action.

---

## Deploy to Minikube

### Step 1: Start Minikube

If you don't have a Minikube cluster running, start one:

```bash
minikube start
```

### Step 2: Deploy Kubernetes Manifests

The necessary Kubernetes manifests are located in the `k8s/` directory. To deploy the application to Minikube:

1. Apply the **deployment** and **service** manifests:

   ```bash
   kubectl apply -f k8s/deployment.yaml
   kubectl apply -f k8s/service.yaml
   ```

### Step 3: Expose the Service

Minikube provides a way to expose services via a browser. To access the deployed application:

1. Get the URL of the service:

   ```bash
   minikube service nextjs-app-service --url
   ```

2. Open the provided URL in your browser to access the application.

   ```bash
   localhost 
   ```
    ```bash
   localhost:80 
   ```


---

## CI/CD with GitHub Actions

On each push to the `main` branch, the application Docker image is automatically built and pushed to GitHub Container Registry (GHCR) through a GitHub Actions workflow.

Ensure that:

* Your GitHub repository is connected to GitHub Actions.
* The `docker.yml` workflow in the `.github/workflows/` directory is configured to build and push the image upon every `main` branch push.

---

## Conclusion

By following these steps, you can:

1. Run the Next.js application locally using Docker.
2. Deploy the application to a Minikube Kubernetes cluster.
3. Automatically build and deploy updates using GitHub Actions.

For troubleshooting or further setup instructions, refer to the documentation in the repository or feel free to reach out for assistance.
