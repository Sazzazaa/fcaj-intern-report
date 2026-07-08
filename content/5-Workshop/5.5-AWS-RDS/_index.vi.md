---
title : "Triển khai Cơ sở dữ liệu (AWS RDS)"
date : 2026-07-04
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Trong phần này, chúng ta triển khai **Amazon RDS for PostgreSQL** để lưu trữ toàn bộ dữ liệu cho ứng dụng. Database sẽ được đặt trong private subnet để không lộ trực tiếp ra Internet, và chỉ cho phép backend EC2 truy cập thông qua Security Group.

Mục tiêu của phần này gồm:

* Tạo một RDS PostgreSQL mới.
* Cấu hình Security Group để EC2 có thể kết nối qua cổng `5432`.
* Thực hiện `Prisma generate`, `migrate` và `seed` dữ liệu ban đầu từ máy chủ EC2.

#### Nội dung

1. [Tạo RDS PostgreSQL](5.5.1-create-rds/)
2. [Cấu hình Security Group RDS](5.5.2-config-sg/)
3. [Migrate và seed dữ liệu](5.5.3-migrate-seed/)