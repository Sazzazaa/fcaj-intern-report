---
title : "Cấu hình Security Group RDS"
date : 2026-07-04
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

### Mở kết nối từ EC2 tới RDS

Để backend truy cập được PostgreSQL, chúng ta chỉ cần cho phép **Security Group của EC2** truy cập tới **Security Group của RDS** qua cổng `5432`.

#### 1. Kiểm tra các Security Group đang dùng

Trong danh sách Security Groups, xác nhận đã có:

* `pm-ec2-sg`: dùng cho backend EC2
* `pm-rds-sg`: dùng cho RDS

![Security groups](/images/5-Workshop/5.5-AWS-RDS/z8007929031359_78ceac77af5643bd71396e152859972c.jpg)

#### 2. Cấu hình inbound rule cho `pm-rds-sg`

Mở Security Group `pm-rds-sg` và thêm inbound rule:

* **Type**: PostgreSQL
* **Protocol**: TCP
* **Port range**: `5432`
* **Source**: Security Group `pm-ec2-sg`

Điều này đảm bảo:

* RDS **không mở public** ra Internet.
* Chỉ máy backend bên trong VPC mới có thể truy cập cơ sở dữ liệu.

#### 3. Kiểm tra outbound rule của EC2

Thông thường outbound mặc định của `pm-ec2-sg` đã cho phép kết nối ra ngoài. Nếu bạn siết outbound, cần đảm bảo EC2 vẫn được phép truy cập tới địa chỉ private của RDS qua cổng `5432`.

#### 4. Kiểm tra thực tế

Sau khi cấu hình xong Security Group, ta sẽ xác minh bằng cách chạy:

* `npx prisma generate`
* `npx prisma migrate deploy`
* `npm run seed`

ở bước kế tiếp. Nếu các lệnh chạy thành công thì rule mạng giữa EC2 và RDS đã chính xác.