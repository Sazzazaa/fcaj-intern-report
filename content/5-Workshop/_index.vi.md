---
title: "Workshop"
date: 2026-07-04
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai hệ thống Project Management Dashboard lên AWS

#### Tổng quan

Workshop này mô tả quá trình đưa ứng dụng **Project Management Dashboard** từ môi trường local lên hạ tầng AWS theo mô hình 3 lớp:

+ **Frontend**: Next.js được deploy bằng **AWS Amplify**.
+ **Backend**: Node.js/Express chạy trên **AWS EC2**.
+ **Database**: PostgreSQL đặt trên **AWS RDS** trong private subnet.

Ngoài ra, hệ thống còn sử dụng:

+ **AWS API Gateway** để cung cấp endpoint HTTPS công khai cho frontend.
+ **AWS S3** để lưu ảnh và các tệp tĩnh.
+ **AWS Cognito** để quản lý đăng nhập, đăng ký và cấp token xác thực.
+ **AWS Lambda Trigger** để đồng bộ người dùng mới từ Cognito vào cơ sở dữ liệu ứng dụng.

#### Nội dung

1. [Giới thiệu kiến trúc hệ thống](5.1-Workshop-overview/)
2. [Chuẩn bị môi trường và Mã nguồn](5.2-Prerequiste/)
3. [Thiết lập Mạng lưới ảo (AWS VPC & Networking)](5.3-AWS-VPC/)
4. [Triển khai Máy chủ Backend (AWS EC2)](5.4-AWS-EC2/)
5. [Triển khai Cơ sở dữ liệu đám mây (AWS RDS)](5.5-AWS-RDS/)
6. [Hosting Frontend & Định tuyến (Amplify & API Gateway)](5.6-Frontend-Routing/)
7. [Lưu trữ tệp phương tiện (AWS S3)](5.7-AWS-S3/)
8. [Xác thực người dùng (AWS Cognito & Lambda)](5.8-AWS-Cognito-Lambda/)
9. [Dọn dẹp tài nguyên](5.9-Cleanup/)