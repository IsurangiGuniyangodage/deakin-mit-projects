# SIT706: Cloud Computing on AWS

**Unit:** Cloud Computing, Deakin University
**Type:** Individual unit projects and final project (two phases)

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
This covers AWS from core services to a production-style, highly available application, then a serverless redesign for a growing e-commerce business.

## Final project, phase 1: highly available WordPress on AWS
- **EC2** web servers behind an **Application Load Balancer**.
- **Auto Scaling Groups** with CPU-based scaling policies.
- **RDS** with **Multi-AZ** failover and a **read replica**.
- **Private S3** for media, with **least-privilege IAM** access.
- The whole stack automated with **CloudFormation**, split into a networking template and an application template.

## Final project, phase 2: serverless e-commerce architecture
I designed an architecture for a rapidly scaling online store that addressed each stated requirement:
- **Global latency:** CloudFront and Route 53.
- **Scalable data tier:** DynamoDB in place of the relational database.
- **Sessions:** ElastiCache.
- **Event-driven processing:** Lambda.
- **Security:** KMS encryption at rest and in transit.
- **Disaster recovery:** a plan meeting a **15 minute RPO and 1 hour RTO**.
- I also recorded a video presentation explaining each design decision.

## Earlier tasks
- **Storage and data:** Amazon EFS and RDS.
- **Networking:** VPC creation, multi-subnet environments with NAT gateways, routing and security groups, and VPC peering.
- **IAM:** users, roles and policies.
- **High availability and scaling:** load-balanced, auto-scaled environments for a café scenario.
- **Automation:** CloudFormation labs and automated infrastructure deployment.

## Skills shown
AWS architecture, high availability and scaling, network design, Infrastructure as Code, cost-aware and secure design, and technical communication.

**Tools:** EC2, RDS, ALB, Auto Scaling, S3, IAM, VPC, CloudFormation, CloudFront, Route 53, DynamoDB, ElastiCache, Lambda, KMS.
