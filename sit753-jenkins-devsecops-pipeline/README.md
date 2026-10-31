# SIT753: Jenkins CI/CD and DevSecOps Pipeline

**Unit:** Professional Practice in IT (DevOps focus), Deakin University
**Type:** Individual unit projects, with team and professional-practice components

> **Note:** This folder contains a write-up only. In line with Deakin University's academic integrity rules, I have not published assessment code or solutions. I'm happy to walk through the work in an interview.

## Overview
I built an end-to-end Jenkins pipeline for a Node.js and Express web application backed by MongoDB (with Mongo Express), run through Docker Compose. The pipeline moves each change through seven stages.

## Pipeline stages
1. **Build:** Jenkins pulls the code from GitHub and installs dependencies with `npm ci`.
2. **Test:** automated unit and integration tests with Jest and Supertest, covering routes such as `/health`, `/sum`, `/items` and authentication on secured routes. JUnit reports and coverage are published.
3. **Code quality:** SonarQube / SonarCloud analysis for code smells, duplication and maintainability, using the Jest coverage report.
4. **Security:** `npm audit` for dependency vulnerabilities and **Trivy** for the Docker image (libraries, OS packages, configuration).
5. **Deployment:** Jenkins builds the Docker image with Docker Compose, pushes it to Docker Hub, and deploys to a staging environment, where a health check confirms the app is live.
6. **Release:** a successful staging deployment pauses at a **manual approval gate**. Once approved, the identical image is promoted to production, giving controlled and auditable releases.
7. **Monitoring:** smoke tests against the `/health` endpoint after each run, plus health checks and logs.

I also wrote up how I would add the security tools (SonarQube for static analysis, OWASP ZAP for dynamic testing, Trivy for dependencies and containers) and where each fits in the pipeline.

## Professional-practice work in the same unit
Git version control with branching (Sprint 1), sprint planning in Trello, agile methodology research, cybersecurity and IP case studies, a SWOT analysis, a team contract, a SFIA skills assessment, leadership and inclusion reflections, a design-thinking exercise, and a career plan with a reflection on an industry interview.

## Skills shown
CI/CD pipeline design, shift-left testing and security scanning, containerised delivery, agile practice and professional communication.

**Tools:** Jenkins, Node.js, Express, MongoDB, Jest, Supertest, SonarQube/SonarCloud, Trivy, npm audit, Docker, Docker Compose, Docker Hub, GitHub, Trello.
