---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Deploying the Project Management Dashboard System to AWS Cloud

#### Overview

**The 3-Tier Architecture** is a classic and highly effective software design pattern for building scalable, maintainable, and highly secure web applications.

In this lab (workshop), we will learn how to take a fully developed Project Management Dashboard application from a Local environment (personal computer) and deploy it to an actual cloud environment (Production) by leveraging the Amazon Web Services (AWS) ecosystem.

We will break down and deploy each core component of the system onto specialized AWS services, including:
+ **AWS Cognito** - An Identity Provider that offers secure login/sign-up flows and issues security tokens for users without the need to build a complex Auth system from scratch.
+ **AWS RDS (PostgreSQL)** - Provisioning a relational Managed Database to securely store all data related to projects, tasks, and users.
+ **AWS EC2 & S3** - Utilizing EC2 virtual servers as the computing environment to run the Backend API (Node.js/Express) for processing business logic, combined with an S3 bucket for storing static files (e.g., avatar images).
+ **AWS Amplify** - A hosting platform that automates the build and deployment process for the Frontend (Next.js), providing a public domain with a built-in security certificate (HTTPS) for end-user access.

#### Table of Contents


1. [Giới thiệu kiến trúc hệ thống](5.1-Overview/)
2. [Chuẩn bị môi trường và Mã nguồn](5.2-Prerequisites/)
3. [Thiết lập Mạng lưới ảo (AWS VPC & Networking)](5.3-AWS-VPC/)
4. [Triển khai Máy chủ Backend (AWS EC2)](5.4-AWS-EC2/)
5. [Triển khai Cơ sở dữ liệu đám mây (AWS RDS)](5.5-AWS-RDS/)
6. [Hosting Frontend & Định tuyến (Amplify & API Gateway)](5.6-Frontend-Routing/)
7. [Lưu trữ tệp phương tiện (AWS S3)](5.7-AWS-S3/)
8. [Xác thực người dùng (AWS Cognito & Lambda)](5.8-AWS-Cognito-Lambda/)
9. [Dọn dẹp tài nguyên](5.9-Cleanup/)