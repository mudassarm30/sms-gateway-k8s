# SMS Gateway Kubernetes Deployment

This repository contains the Kubernetes deployment configuration and GitHub Actions CI/CD pipeline for the SMS Gateway project.

## Components

The system is composed of:
1. `sms-gateway-backend`
2. `sms-gateway-worker`
3. `sms-gateway-frontend`
4. PostgreSQL Database

## CI/CD Pipeline

The `.github/workflows/deploy.yml` automates the build and deployment process:
1. It pulls the source code for all three components from their respective repositories.
2. It builds Docker images and pushes them to Docker Hub.
3. It connects to an Ubuntu machine via SSH and applies the Kubernetes manifests located in the `k8s/` directory.

### Prerequisites

To use the CI/CD pipeline, you must configure the following Secrets in your GitHub repository settings:

- `DOCKERHUB_USERNAME`: Your Docker Hub username.
- `DOCKERHUB_TOKEN`: An access token for Docker Hub.
- `SSH_HOST`: The IP address of the target Ubuntu server running Kubernetes.
- `SSH_USER`: The SSH username for the Ubuntu server.
- `SSH_PRIVATE_KEY`: The SSH private key to access the Ubuntu server.
- `POSTGRES_USER`: The username for the PostgreSQL database (e.g., `smsgateway_user`).
- `POSTGRES_PASSWORD`: The secure password for the PostgreSQL database.
- `POSTGRES_DB`: The name of the PostgreSQL database (e.g., `smsgatewaydb`).

*Note: You must also update the repository URLs in `.github/workflows/deploy.yml` and `k8s/*.yaml` files to match your actual GitHub and Docker Hub organization/username.*
