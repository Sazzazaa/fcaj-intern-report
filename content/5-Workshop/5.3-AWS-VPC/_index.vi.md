---
title : "Thiết lập Mạng lưới ảo (AWS VPC)"
date : 2026-07-04 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

### Cô lập tài nguyên mạng bằng VPC

Trong phần này, chúng ta sẽ tự tay khởi tạo một **Mạng riêng ảo (VPC)** từ đầu để cung cấp môi trường mạng an toàn cho toàn bộ dự án. Thay vì sử dụng Default VPC (VPC mặc định của AWS), chúng ta sẽ thiết kế một kiến trúc mạng phân tầng bao gồm: **Public Subnet** (mạng công cộng) dành cho máy chủ Backend (EC2) để có thể giao tiếp với mạng Internet thông qua **Internet Gateway**, và các **Private Subnets** (mạng nội bộ) dành riêng cho cơ sở dữ liệu (RDS) nhằm bảo vệ dữ liệu nghiệp vụ của hệ thống khỏi các truy cập trái phép từ bên ngoài.

![VPC Architecture](/images/5-Workshop/5.3/vpc-architecture.png)

#### Nội dung (Content)

- [Khởi tạo VPC & Subnets](5.3.1-create-vpc-subnets/)
- [Cấu hình Internet Gateway & Route Tables](5.3.2-igw-route-tables/)