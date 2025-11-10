# System Overview

The **Deployment Pipeline** automates the process of building, deploying, and hosting frontend applications directly from GitHub repositories.  
It enables users to go from source code to a live, shareable URL without manual setup or server configuration.

---

## Workflow Summary

When a user provides a GitHub repository URL and triggers deployment, the system executes a series of automated functions that ensure seamless application delivery.

### End-to-End Deployment Flow

1. **Repository Cloning**  
   - The API server authenticates the GitHub URL provided by the user.  
   - The build server securely clones the source code repository into an isolated environment.  
   - Only the latest branch or commit is fetched to optimize performance and reduce build time.

2. **Automated Build Process**  
   - A build server, running as an ECS task, builds the project using pre-defined Docker images stored in AWS ECR.  
   - The environment includes dependencies such as Node.js to compile React applications.  
   - Once the build completes, the system generates production-ready files (HTML, CSS, JS).

3. **Artifact Upload to AWS S3**  
   - The built static files are uploaded to a designated S3 bucket.  
   - The system assigns each deployment a unique directory or version ID for organized storage and rollback capability.  
   - Appropriate access policies are applied to ensure security and isolation per project.

4. **Serving via Reverse Proxy**  
   - A custom reverse proxy fetches files from S3 in real time and streams them to clients.  
   - It ensures low latency, caching, and HTTPS support.  
   - This allows users to instantly access the deployed application via a generated live URL.

---

## Core Functional Modules

The system is divided into several modules that work together to achieve complete automation:

### 1. **User Authentication and Autherization**
Handles secure access to the system.  
- Users can sign up, log in, and manage their profiles.  
- Passwords are encrypted before storage.  
- JWT (JSON Web Tokens) or session-based authentication ensures secure API communication.

### 2. **Project Management**
Links user accounts to their GitHub repositories.  
- Users can create, view, and manage projects.  
- Each project record stores metadata such as repository URL, project name, and user ID.  
- A single user can have multiple projects.

### 3. **Automated Build & Deployment**
Responsible for compiling and preparing production builds.  
- The API server triggers a build job using AWS ECS tasks.  
- Each build is isolated and stateless, ensuring consistency and reproducibility.  
- Logs, build status, and progress are tracked and linked to a specific deployment record.

### 4. **File Hosting and Delivery**
Ensures fast and reliable access to deployed applications.  
- Build artifacts are uploaded to AWS S3 with public-read or signed URL access.  
- A reverse proxy layer retrieves and streams these files to users in real time.  
- This design supports horizontal scaling for high-traffic applications.

### 5. **Database Management**
Stores essential project data and deployment history.  
- **PostgreSQL** is used for relational data storage.  
- Contains three main tables:
  - **Users** → Authentication and user profiles.  
  - **Projects** → Repository and configuration details.  
  - **Deployments** → Build metadata, status, and generated URLs.  
- The database enables tracking deployment versions, history, and ownership.

---

## Functional Flow Summary

User → API Server → Build Server (ECS) → AWS S3 → Reverse Proxy → Live App
