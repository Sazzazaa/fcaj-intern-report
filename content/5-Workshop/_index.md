---
title: "Workshop"
date: 2026-07-04
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Deploying the Project Management Dashboard to AWS

#### Overview

This workshop explains how to deploy the **Project Management Dashboard** from a local development environment to AWS using a 3-tier architecture:

+ **Frontend**: Next.js deployed with **AWS Amplify**
+ **Backend**: Node.js/Express running on **AWS EC2**
+ **Database**: PostgreSQL hosted on **AWS RDS**

The system also uses:

+ **AWS API Gateway** to expose a public HTTPS endpoint for the frontend
+ **AWS S3** to store images and static files
+ **AWS Cognito** to manage sign-in, sign-up, and authentication tokens
+ **AWS Lambda Trigger** to synchronize newly confirmed Cognito users into the application database

#### Table of Contents

1. [System Architecture Overview](5.1-Workshop-overview/)
2. [Environment Preparation and Source Code](5.2-Prerequiste/)
3. [AWS VPC and Networking Setup](5.3-AWS-VPC/)
4. [Deploying the Backend Server on EC2](5.4-AWS-EC2/)
5. [Deploying the Cloud Database on RDS](5.5-AWS-RDS/)
6. [Frontend Hosting and HTTPS Routing](5.6-Frontend-Routing/)
7. [Media Storage with AWS S3](5.7-AWS-S3/)
8. [User Authentication with Cognito and Lambda](5.8-AWS-Cognito-Lambda/)
9. [Resource Cleanup](5.9-Cleanup/)