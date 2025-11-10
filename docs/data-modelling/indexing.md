# Indexing in the Project Database

This section explains the single indexes currently implemented in the project’s PostgreSQL database using Prisma ORM.  
Indexes improve database performance by enabling faster lookups and filtering during common query operations.

---

## User Table

### **Single Index**
```prisma
@@index([email])
```
#### Explanation:

The email field is indexed because it’s frequently queried during authentication.
Whenever a user signs up or logs in, the system checks if the email exists — this index makes that process significantly faster.
It complements the @unique constraint on email, ensuring quick lookups and preventing duplicates efficiently.

#### Performance Benefit:

Faster user retrieval and validation during login or registration.


## Project Table

### **Single Index**
```prisma
@@index([gitUrl])
```
#### Explaination:

The gitUrl field (mapped to git_url in the database) is indexed to speed up queries that search for projects by their linked GitHub repository.
It’s commonly used when creating or managing deployments based on a repository URL.

#### Performance Benefit:

Improves performance for operations that fetch projects or deployments using the repository link.


## Deployment Table

### **Single Index**
```prisma
@@index([status])
```
#### Explanation

The status field is indexed because it’s frequently used for filtering deployments based on their lifecycle state (e.g., QUEUED, RUNNING, COMPLETED).
This index helps quickly retrieve all deployments in a particular status for monitoring or background processing tasks.

#### Performance Benefit:

Enhances efficiency of dashboard and worker queries that rely on deployment status filters.


