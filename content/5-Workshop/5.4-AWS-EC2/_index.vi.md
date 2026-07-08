---
title : "Triển khai Backend (AWS EC2)"
date : 2026-07-04
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

### Triển khai Backend trên AWS EC2

Trong phần này, chúng ta triển khai backend Node.js/Express lên **Amazon EC2** để ứng dụng có thể phục vụ API cho frontend. EC2 được đặt trong public subnet để dễ truy cập quản trị, còn database vẫn nằm ở private subnet nhằm đảm bảo an toàn dữ liệu.

EC2 phù hợp với bài toán này vì:

* **Toàn quyền cấu hình môi trường**: dễ cài Node.js, Prisma, PM2 và các thư viện phụ thuộc.
* **Chi phí thấp**: có thể dùng `t2.micro` hoặc `t3.micro` trong phạm vi Free Tier.
* **Dễ tích hợp**: backend trên EC2 có thể kết nối nội bộ tới RDS và được đặt sau API Gateway để cung cấp HTTPS cho frontend.

![EC2 launched successfully](/images/5-Workshop/5.4-AWS-EC2/z8007993502305_c977416dc91cb6dd7fa401b0e8741e0e.jpg)

#### Nội dung

1. [Khởi tạo EC2 Instance](5.4.1-launch-ec2/)
2. [Cài đặt môi trường và chuẩn bị backend](5.4.2-install-env/)