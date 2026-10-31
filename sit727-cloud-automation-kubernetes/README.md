# SIT727: Cloud Automation Technologies

**Unit:** Cloud Automation Technologies, Deakin University
**Type:** Individual unit projects

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
A progression from containerising a first app to running stateful, autoscaling and IoT workloads on Kubernetes, plus written evaluations of cloud options for business and regulatory needs.

## Technical work
- **Clinic-booking application on Kubernetes:** containerised a Django app with Docker and deployed it with a Deployment, Service, PersistentVolumeClaim, ConfigMap and Secret. The final version added liveness and readiness probes and a **Horizontal Pod Autoscaler (2 to 5 pods)** on CPU and memory.
- **MongoDB replica set:** deployed from scratch with **StatefulSets, headless Services and PersistentVolumeClaims**, without Helm or operators, then verified replication and tested failover.
- **Resource management:** set CPU and memory limits to reach specific QoS classes and used an HPA to scale under load.
- **IoT backends:** deployed an **EMQX MQTT broker**, monitored resource use with `kubectl top` and configured autoscaling.

## Evaluation and communication work
- **Cost comparison:** in-house hosting vs cloud VMs vs cloud Kubernetes using the AWS Pricing Calculator, with the operational and uptime benefits as the deciding factors.
- **Cloud-edge IoT deployment for a city council:** security and regulatory implications written for a non-technical audience, referencing the Privacy Act 1988 and the ACSC Essential Eight.
- **Explanations** of how companies like Netflix split compute across microservices, how MongoDB replicates data, and how Kubernetes reduces vendor lock-in.
- A concept map of how Kubernetes components fit together.

## Skills shown
Kubernetes deployment and operations, stateful workloads, autoscaling, cost and risk evaluation, and explaining cloud decisions to different audiences.

**Tools:** Docker, Kubernetes, HPA, StatefulSets, PVC, ConfigMap, Secret, MongoDB, EMQX.
