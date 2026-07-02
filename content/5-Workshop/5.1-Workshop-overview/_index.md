---
title : "Introduction"
date : 2026-07-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to Web Architecture on AWS Cloud

+ The Project Management Dashboard is a comprehensive web application based on a 3-tier architecture: Frontend, Backend, and Database. 
+ Instead of running entirely on a single server, this system leverages the AWS service ecosystem to ensure scalability, security, and high availability. Key components include: AWS EC2, AWS RDS, AWS Cognito, AWS S3, AWS Lambda, and AWS Amplify. Decoupling these services enables flexible management and performance optimization for specific, specialized tasks.

#### Workshop Overview
In this workshop, you will practice the process of migrating and deploying the entire application from a local environment (personal computer) to the AWS cloud. The deployment process will revolve around two main environments:

+ **"Local Environment"**: Where you set up the project source code using Next.js (Client) and Node.js (Server), test the user interface, and connect to a local PostgreSQL database. 
+ **"Cloud Environment (AWS)"**: Simulates the actual operational environment (Production). Here, you will step-by-step provision and configure core AWS services:
    - **AWS RDS (PostgreSQL)**: A cloud database for storing project, user, and task data.
    - **AWS EC2**: A virtual server acting as the computing environment to run the Backend API (Node.js) for processing system logic.
    - **AWS Cognito**: An identity management service responsible for login, sign-up flows, and user session security.
    - **AWS S3**: Static storage space for media files (e.g., avatar images, attachments).
    - **AWS Amplify**: A hosting and automated delivery platform for deploying the Frontend source code (Next.js) to the public internet.

The ultimate goal is to seamlessly connect the Frontend (on AWS Amplify) with the Backend (on EC2) and the Database (on RDS), ensuring the entire system operates perfectly and is publicly accessible.
![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)