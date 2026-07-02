---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
# Triển khai hệ thống Project Management Dashboard lên đám mây AWS

#### Tổng quan

**Kiến trúc 3 lớp (3-Tier Architecture)** kết hợp với môi trường Cloud là một mô hình thiết kế kinh điển để xây dựng các ứng dụng Web có tính mở rộng, khả năng bảo trì và bảo mật cao.

Trong bài lab (workshop) này, chúng ta sẽ học cách đưa một ứng dụng Quản lý dự án (Project Management Dashboard) đã được phát triển hoàn thiện ở môi trường Local (máy cá nhân) lên môi trường đám mây thực tế (Production). Thay vì dùng các dịch vụ serverless đóng gói sẵn, chúng ta sẽ tự tay thiết lập một kiến trúc Enterprise trên Amazon Web Services (AWS) bao gồm:

+ **AWS VPC & Networking** - Khởi tạo Mạng riêng ảo với các Subnet Public/Private và Internet Gateway để cô lập và bảo mật tài nguyên.
+ **AWS EC2** - Máy chủ ảo đóng vai trò làm môi trường điện toán để chạy Backend API (Node.js/Express) xử lý logic nghiệp vụ.
+ **AWS RDS (PostgreSQL)** - Cơ sở dữ liệu quan hệ lưu trữ dữ liệu dự án, được bảo vệ nghiêm ngặt bên trong Private Subnet.
+ **AWS Amplify & API Gateway** - Tự động hóa quá trình triển khai Frontend (Next.js) ra môi trường mạng công cộng bằng Amplify, kết hợp dùng API Gateway để định tuyến proxy an toàn (chuyển đổi HTTPS sang HTTP) kết nối đến máy chủ EC2.
+ **AWS S3** - Không gian lưu trữ tĩnh dành cho các tệp phương tiện của dự án.
+ **AWS Cognito & Lambda** - Cung cấp luồng xác thực an toàn, kết hợp cùng Lambda Trigger để tự động đồng bộ hóa thông tin người dùng mới xuống cơ sở dữ liệu RDS.

#### Nội dung

1. [Giới thiệu kiến trúc hệ thống](5.1-Overview/)
2. [Chuẩn bị môi trường và Mã nguồn](5.2-Prerequisites/)
3. [Thiết lập Mạng lưới ảo (AWS VPC & Networking)](5.3-AWS-VPC/)
4. [Triển khai Máy chủ Backend (AWS EC2)](5.4-AWS-EC2/)
5. [Triển khai Cơ sở dữ liệu đám mây (AWS RDS)](5.5-AWS-RDS/)
6. [Hosting Frontend & Định tuyến (Amplify & API Gateway)](5.6-Frontend-Routing/)
7. [Lưu trữ tệp phương tiện (AWS S3)](5.7-AWS-S3/)
8. [Xác thực người dùng (AWS Cognito & Lambda)](5.8-AWS-Cognito-Lambda/)
9. [Dọn dẹp tài nguyên](5.9-Cleanup/)