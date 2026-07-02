---
title : "Giới thiệu"
date : 2026-07-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về Kiến trúc Web trên đám mây AWS

+ Hệ thống Quản lý dự án (Project Management Dashboard) là một ứng dụng Web toàn diện bao gồm 3 lớp (3-tier architecture): Frontend, Backend và Database. 
+ Thay vì chạy toàn bộ trên một máy chủ đơn lẻ, hệ thống này tận dụng hệ sinh thái các dịch vụ của AWS để đảm bảo tính mở rộng, khả năng bảo mật và tính sẵn sàng cao. Các thành phần chính bao gồm: AWS EC2, AWS RDS, AWS Cognito, AWS S3, AWS Lambda và AWS Amplify. Việc phân tách các dịch vụ giúp quản lý linh hoạt và tối ưu hóa hiệu suất cho từng tác vụ chuyên biệt.

#### Tổng quan về workshop
Trong workshop này, bạn sẽ thực hành quá trình chuyển đổi và triển khai toàn bộ ứng dụng từ môi trường máy cá nhân (Local) lên đám mây AWS. Quá trình triển khai sẽ xoay quanh hai môi trường chính:

+ **"Môi trường Local"**: Nơi bạn thiết lập mã nguồn dự án bằng Next.js (Client) và Node.js (Server), chạy thử nghiệm giao diện và kết nối với cơ sở dữ liệu PostgreSQL cục bộ. 
+ **"Môi trường Cloud (AWS)"**: Mô phỏng môi trường vận hành thực tế (Production). Tại đây, bạn sẽ từng bước khởi tạo và cấu hình các dịch vụ AWS cốt lõi:
    - **AWS RDS (PostgreSQL)**: Cơ sở dữ liệu đám mây lưu trữ dữ liệu dự án, người dùng và công việc.
    - **AWS EC2**: Máy chủ ảo đóng vai trò chạy Backend API (Node.js) để xử lý logic hệ thống.
    - **AWS Cognito**: Dịch vụ quản lý danh tính, chịu trách nhiệm cho luồng đăng nhập, đăng ký và bảo mật phiên người dùng.
    - **AWS S3**: Không gian lưu trữ tĩnh dành cho các tệp phương tiện (ví dụ: hình ảnh avatar, tệp đính kèm).
    - **AWS Amplify**: Nền tảng lưu trữ và phân phối tự động mã nguồn Frontend (Next.js) ra môi trường mạng công cộng.

Mục tiêu cuối cùng là kết nối thông suốt Frontend (trên AWS Amplify) với Backend (trên EC2) và Database (trên RDS), đảm bảo toàn bộ hệ thống hoạt động hoàn hảo và có thể truy cập public.
![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)
