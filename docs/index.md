# Deployment Pipeline 

A **cloud-based deployment pipeline** that automatically builds and deploys **React.js applications** directly from GitHub repositories.

This system acts as a simplified version of **Vercel**, providing developers with continuous deployment, instant hosting, and automatic build management — all integrated with GitHub.

---

## Overview

The **Deployment Pipeline** automates the process of deploying frontend web applications by connecting to a user’s GitHub repository, building the source code, and hosting the final output on the cloud.

Once a user signs up, connects a repository, and triggers deployment, the system performs the following steps:

1. **Clone Repository** – The system fetches the codebase from the provided GitHub repository URL.  
2. **Build Process** – Code is built inside a secure containerized environment (AWS ECS) using pre-configured Docker images stored in AWS ECR.  
3. **Artifact Storage** – The build artifacts (production-ready files) are uploaded to an **AWS S3** bucket.  
4. **Reverse Proxy Serving** – A custom reverse proxy retrieves files from S3 and streams them to end users via a public deployment URL.  

This provides an end-to-end automated workflow — from source code to live hosting.

---

## System Architecture

The project consists of multiple interconnected services:

- **API Server** – Handles authentication, authorization, deployment requests, and manages project metadata.  
- **Build Servers (AWS ECS Tasks)** – Containerized workers that perform the build and upload artifacts to S3.  
- **Reverse Proxy Server** – Streams built files from S3 to the user’s browser for live preview or production hosting.  
- **Database (PostgreSQL)** – Stores users, projects, and deployment metadata.  
- **Cloud Storage (AWS S3)** – Holds final build outputs.  


User → API Server → Build Server (ECS) → S3 Bucket → Reverse Proxy → Live URL


