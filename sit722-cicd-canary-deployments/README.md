# SIT722: CI/CD, Infrastructure as Code and Canary Deployments

**Unit:** Software Deployment and Operation, Deakin University
**Type:** Individual unit project built up over the trimester on one application

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
I took a containerised microservices application from local Docker through to a fully automated delivery platform on Azure Kubernetes Service (AKS). The final piece was a canary release process that uses live monitoring data to decide whether a release is safe, and rolls back automatically if it isn't.

## What I built
- **Containers and microservices:** Dockerised multi-service app with PostgreSQL, environment-variable configuration and automated tests.
- **Kubernetes on AKS:** Deployments, Services, persistent storage, LoadBalancers, scaling and recovery. First run locally, then on AKS.
- **Infrastructure as Code:** Terraform to create, plan and destroy cloud resources repeatably. It ended up running inside the CI/CD pipeline rather than as a separate exercise.
- **CI/CD with GitHub Actions:** automated tests, image builds and pushes to Azure Container Registry, then staging validation and automatic deployment to production.
- **Monitoring:** Prometheus and Grafana for the Kubernetes environment and application behaviour.
- **Security scanning:** Docker Scout to find image vulnerabilities and apply remediation advice. This was later integrated with Terraform, Prometheus and Grafana in the main workflow.

## Highlight: progressive canary deployment with automatic rollback
- Implemented with **Argo Rollouts** and **Prometheus**.
- The user service is introduced to traffic in controlled stages. A dedicated canary Service lets Prometheus watch only the candidate version.
- A healthy release was **promoted automatically**.
- A deliberately defective release (`v3-bad`) passed Kubernetes readiness checks but **failed the application-level Prometheus check and was automatically rejected**.
- The key design decision was separating `/health` (is the pod running?) from `/canary-check` (is the release actually good?). A pod can be "Ready" and still be wrong for production, so monitoring data became part of the release decision.

## Problems I solved
- Azure lab subscription limits blocked my original design, so I changed VM sizes, storage classes and AKS configuration to get it deployed.
- Terraform state and resource-deletion problems.
- Pods not starting, environment variable and persistent volume issues, Azure authentication, Prometheus configuration and Argo Rollouts integration.
- My first idea for the advanced task was too close to the weekly CI work. After feedback I changed it to canary deployment with monitoring-driven rollback, which was a much stronger result.

## Skills shown
CI/CD design, Kubernetes operations, Terraform, observability, release safety, and troubleshooting cloud constraints.

**Tools:** GitHub Actions, Docker, Docker Scout, Kubernetes, AKS, Azure Container Registry, Terraform, Argo Rollouts, Prometheus, Grafana.
