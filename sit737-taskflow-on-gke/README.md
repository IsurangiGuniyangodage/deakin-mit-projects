# SIT737: TaskFlow, a Cloud-Native Application on Google Kubernetes Engine

**Unit:** Cloud Native Application Development, Deakin University
**Type:** Individual unit project

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
**TaskFlow** is an original two-tier task management application that I designed, built and deployed on Google Kubernetes Engine (GKE). I treated it as a reliability project, not just a deployment: each stage of the build fixed weaknesses found in the previous stage.

## Architecture
- **Stateless frontend pods** served through **Nginx**, which proxies `/api/` requests to the backend over cluster-internal DNS.
- **Backend on a ClusterIP Service**, so it is never exposed directly to the internet.
- **Public LoadBalancer** as the only entry point.
- **PVC-backed persistent storage**, so data survives pod restarts.
- **Security layers:** non-root containers, internal-only backend, resource limits, SHA-256 password hashing and Bearer-token authentication.

## Deployment, in three stages
1. Deployed to GKE using **Docker Hub**, because Google Artifact Registry was blocked by the university's IAM policy.
2. Added a **ReadWriteOnce persistent volume** and limited the backend to a single replica to avoid write conflicts. I documented this trade-off openly.
3. Added a **7-step Google Cloud Build CI/CD pipeline**: retrieve credentials, rolling restart, check rollout status, then verify pods and services.

## Reliability and observability work
- **Failure analysis:** a forensic review of a replica-loss event. I found three missing safeguards (PodDisruptionBudget, health probes, a single-node point of failure), proposed concrete YAML for each, then implemented and verified the fixes with `kubectl describe`.
- **Metrics analysis:** time-series analysis showing the link between log activity and CPU, a four-metric monitoring plan with thresholds (CPU, memory, restart count, HTTP rate), and an explanation of why memory stayed flat while CPU rose.
- **Self-healing:** after deleting all pods, Kubernetes restored the desired replica count with no manual action. I traced the sequence, including the temporary error states during recovery.
- **Three pillars of observability:** why logs alone are not enough, and how metrics and traces add to them.

## Problems I solved
- A `PermissionError` on the backend volume.
- Kubernetes image caching caused by the `latest` tag.
- A Dockerfile `COPY` pattern that left pages out of the image.
- Tuning startup, liveness and readiness probes so they neither restart healthy pods nor miss failures.
- Kubernetes networking and DNS resolution between Nginx and the backend.

## Skills shown
Cloud-native architecture, Kubernetes on GKE, CI/CD with Cloud Build, reliability engineering and observability, and independent research (I applied SRE and Kubernetes literature to thresholds, probes and storage decisions).

**Tools:** GKE, Kubernetes, Docker, Google Cloud Build, Nginx, Python Flask.
