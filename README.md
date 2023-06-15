# Overview
This repository is designed to facilitate the automation of secure cloud infrastructure on Google Cloud Platform (GCP) using Kubernetes (GKE) and HashiCorp Vault. It enables a seamless Continuous Delivery (CD) pipeline using Terraform, offering a fully automated setup for diverse environments including development, staging, and production.

# Key Objectives
- Automate the creation of robust GCP infrastructure stacks.
- Enable seamless promotion of code changes across environments using Git.
- Simplify cloud infrastructure management across different development phases (Dev, Staging, Production).

## Project Highlights
This project focuses on deploying HashiCorp Vault on a private GCP Kubernetes cluster (GKE), incorporating critical security components for secrets management, CI/CD, and high availability.

## Core Components
1. **Infrastructure as Code (IaC) with Terraform:**
   - Automates provisioning of GCP resources like VPCs, GKE clusters, and Vault storage.
   - Deploys Vault using Terraform scripts and Helm charts.

2. **CI/CD Pipeline with Google Cloud Build:**
   - Integrates Terraform and Helm for seamless deployment of GCP resources and Kubernetes applications.
   - Manages continuous delivery of Vault configurations including policies, mounts, and authentication methods.

3. **High Availability & Security Testing:**
   - Validates the deployment of Vault failover, RAFT replication, and authentication mechanisms.
   - Ensures secure secrets management across multiple environments.

## GCP Services Used
- **GKE (Kubernetes Engine):** Hosts Vault and manages Kubernetes workloads.
- **Dataproc:** Integrates with Apache Spark for scalable data processing.
- **Certificate Authority:** Enables root CA management for secure communication.
- **Cloud KMS:** Manages encryption keys for Vault.
- **Cloud Build:** Manages CI/CD pipelines.
- **IAM Custom Roles:** Defines custom roles for granular access control.
- **Cloud DNS & Logging:** Manages DNS and logging for GCP services.
- **GCE OS Patch Policies:** Automates weekly OS patching.

## Deployment Environments
This setup supports different environments like development, staging, and production, using consistent configurations across all. The deployment follows a predefined IP schema for seamless cloud management.

## How to Deploy
Deployment is modular, allowing users to execute scripts independently or as part of a full CI/CD pipeline.

### Deployment Steps
1. **Set Up Credentials:**
   ```bash
   gcloud auth application-default login
## How to Deploy
Deployment is modular, allowing users to execute scripts independently or as part of a full CI/CD pipeline.

### Deployment Steps
1. **Set Up Credentials:**
   ```bash
   gcloud auth application-default login

   # Run Deployment Scripts
   # Initialize GCP infrastructure
   cd <git_repository_root>
   ./scripts/gcp-deploy.sh -p <google_project>

   # Deploy Vault with Helm
   cd <git_repository_root>
   ./scripts/vault-deploy.sh -p <google_project> -n <vault_dns_name> -a

   # Configure and Test Vault
   # Initialize Vault
   ./scripts/vault-init.sh -p <google_project> -n <vault_dns_name>

   # Apply Vault configuration
   ./scripts/vault-config.sh -p <google_project> -n <vault_dns_name> -a

   # Test High Availability
   ./scripts/vault-test-gke.sh -p <google_project> -n <vault_dns_name>
