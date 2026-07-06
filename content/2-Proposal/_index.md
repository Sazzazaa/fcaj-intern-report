---
title: "Proposal"
date: 2026-06-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Project Management Dashboard on AWS Cloud
## Proposed Deployment of a 3-Tier Web Application Architecture

### 1. Project Overview
The **Project Management Dashboard** is a comprehensive full-stack web application designed to help individuals and teams track progress, manage tasks, and allocate resources efficiently. Instead of simply running locally, this project focuses on designing the infrastructure architecture and deploying the entire system (Next.js Frontend, Node.js Backend, PostgreSQL Database) to the Amazon Web Services (AWS) cloud ecosystem following Enterprise standards.

### 2. Objectives
* **Comprehensive Cloud Migration:** Successfully transition the application from a local development environment to a Production environment (AWS Cloud).
* **High Availability & Scalability:** Ensure the application can handle incoming traffic efficiently and operate 24/7 by decoupling core services.
* **Security Enhancement:** Isolate the database from the public Internet using a Virtual Private Cloud (VPC) and implement secure identity management with Amazon Cognito.
* **Cost Optimization:** Design an architecture that maximizes the use of the AWS Free Tier (750 hours of EC2/RDS free per month) to keep maintenance budgets to an absolute minimum.

### 3. Problem Statement
* **Current Issues:** Traditional self-hosted (on-premise) or Monolithic project management systems struggle to scale as data and user volume grow. Building a secure custom Authentication flow from scratch is time-consuming and highly vulnerable to security flaws. Furthermore, hosting the database on the same server as the application creates a severe risk of complete data loss if the server is compromised.
* **Proposed Solution:** Decouple the system into a 3-tier architecture. Utilize a Managed Database (AWS RDS) for data safety; employ a dedicated identity provider (AWS Cognito) to offload security burdens; and automate the frontend delivery to end-users globally via AWS Amplify.

### 4. Solution Architecture
The platform adopts a 3-Tier Architecture (Frontend - Backend - Database) distributed across specialized AWS services, residing inside a Virtual Private Cloud (VPC) with clear Subnet segmentation.

![Project Architecture](/images/2-Proposal/aws-architecture.png)
*(Note: Insert your AWS architecture diagram here)*

*Component Design & AWS Services Used:*
- **AWS VPC (Virtual Private Cloud):** Provision 1 Public Subnet (for EC2) to connect to the Internet via an Internet Gateway, and 2 Private Subnets (for RDS) for strict data isolation.
- **Amazon Cognito:** Provides a secure Sign-in/Sign-up interface, email verification, and JWT Token issuance. Integrated with an **AWS Lambda Trigger** to automatically synchronize new user data to the RDS database upon successful registration.
- **AWS RDS (PostgreSQL):** A fully managed relational database storing all core business data (Projects, Tasks, Users).
- **AWS EC2 (Ubuntu):** A virtual server acting as the compute environment running Node.js/Express (Backend), using PM2 for process management. It communicates with the Database securely via internal ports.
- **Amazon API Gateway:** An intermediary gateway acting as a secure proxy to convert HTTPS requests (from Frontend) to HTTP requests (for the EC2 Backend).
- **Amazon S3:** An independent storage bucket for static media files (e.g., user avatars, project attachments).
- **AWS Amplify:** A CI/CD hosting platform that automatically pulls the Next.js Frontend code from GitHub, builds it, and distributes it with a built-in HTTPS SSL certificate.

### 5. Timeline & Milestones
The project is planned to be executed in 5 phases:
* **Phase 1: Preparation & Assessment (Week 1):** Prepare the local source code, design the AWS architecture diagram, estimate costs, and set up the AWS account.
* **Phase 2: Security & Database Setup (Week 2):** Provision the VPC (Subnets, Route Tables, Internet Gateway). Create the AWS RDS PostgreSQL instance and set up Amazon Cognito alongside the Lambda trigger.
* **Phase 3: Backend & Storage Deployment (Week 3):** Launch the EC2 instance, install the Node.js environment. Run seed data into RDS. Create an S3 bucket and grant Public Access for static media files.
* **Phase 4: Frontend Deployment & Routing (Week 4):** Push source code to GitHub and connect to AWS Amplify. Configure API Gateway to ensure seamless communication between the Frontend and Backend.
* **Phase 5: Testing & Handover (Week 5):** Perform End-to-End testing (Create new projects, update tasks via Drag & Drop). Finalize Workshop documentation and prepare Clean-up instructions.

### 6. Budget
The project is deployed in the **Asia Pacific (Singapore)** region using On-Demand pricing. While a new account can heavily leverage the **AWS Free Tier** to minimize expenses, the breakdown below represents the actual estimated cost without Free Tier (useful for budgeting with AWS Credits):

* **Amazon EC2 (t3.micro):** ~$10.41 / month (Includes 24/7 instance uptime and EBS storage).
* **Amazon RDS for PostgreSQL (db.t3.micro - Single-AZ):** ~$23.20 / month (Includes database instance and 20GB of storage).
* **Amazon Cognito:** ~$5.01 / month (User authentication and access management).
* **AWS Amplify:** ~$1.80 / month (Build minutes and hosting/bandwidth).
* **Amazon API Gateway:** ~$0.42 / month (REST API gateway routing).
* **Amazon S3:** ~$0.25 / month (Object storage for images and static files).
* **AWS Lambda:** $0.00 / month (Fully covered under the Always Free tier limits).

* **Estimated Total Budget:** **~$41.09 / month** (Approx. ~$493.08 / year).

### 7. Risk Assessment
*Risk Matrix & Mitigation Strategies:*
1. **Unexpected Billing Charges (Risk: High):** Due to accidental misconfigurations (e.g., enabling RDS Multi-AZ or allocating unused Elastic IPs).
   * *Mitigation:* Mandate the setup of AWS Budgets (zero-spend alert). Carefully review pricing and ensure the "Free tier eligible" tag is visible before provisioning services. Perform a complete Clean-up immediately after the final presentation.
2. **Service Connectivity Errors (Risk: Medium):** Frontend fails to call the API; Backend is denied access to the Database.
   * *Mitigation:* Carefully map out **Security Groups**. Ensure RDS opens port 5432 strictly for the EC2 internal IP, and EC2 opens its inbound port to allow access solely from the API Gateway.
3. **Security/Credential Leaks (Risk: High):** Accidentally committing connection strings (Database URL) or Secret Keys to public GitHub repositories.
   * *Mitigation:* Store all sensitive credentials in local `.env` files and add them to `.gitignore`. Utilize the built-in Environment Variables feature in AWS Amplify and EC2 to securely manage production keys.