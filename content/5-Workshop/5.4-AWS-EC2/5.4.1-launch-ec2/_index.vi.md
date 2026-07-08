---
title : "Khởi tạo EC2 Instance"
date : 2026-07-04
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

### Khởi tạo máy chủ EC2 cho backend

Ở bước này, chúng ta tạo một máy chủ EC2 để chạy backend Node.js. Hãy sử dụng **cùng Region với VPC và RDS** đã tạo trước đó. Trong kết quả thực tế của workshop này, region được dùng là **us-east-2 (Ohio)**.

#### 1. Truy cập dịch vụ EC2

1. Đăng nhập vào AWS Management Console.
2. Tìm kiếm `EC2` trên thanh Search.
3. Chọn **Instances** và nhấn **Launch instance**.

![Access EC2](/images/5-Workshop/5.4-AWS-EC2/access-ec2.png)

#### 2. Cấu hình cơ bản

Điền các thông tin chính:

* **Name**: `project-management-api` hoặc tên tương tự.
* **Amazon Machine Image**: Amazon Linux 2023.
* **Instance type**: `t2.micro` hoặc `t3.micro`.

![Config EC2 OS](/images/5-Workshop/5.4-AWS-EC2/config-os.png)

#### 3. Tạo Key Pair

1. Ở mục **Key pair (login)**, chọn **Create new key pair**.
2. Đặt tên, ví dụ: `pm-key`.
3. Chọn định dạng `.pem`.
4. Tải file key về máy để dùng khi SSH vào EC2.

![Create Key Pair](/images/5-Workshop/5.4-AWS-EC2/create-key-pair.png)

#### 4. Cấu hình mạng và Security Group

1. Trong **Network settings**, nhấn **Edit**.
2. Chọn đúng **VPC** đã tạo ở bước 5.3.
3. Chọn **Public Subnet** cho EC2.
4. Bật **Auto-assign public IP**.
5. Tạo Security Group `pm-ec2-sg`.

Các rule tối thiểu nên có:

* **SSH (22)**: chỉ mở cho IP của bạn.
* **Custom TCP (8000)**: cho backend API.
* **HTTP (80)**: nếu cần test nhanh hoặc reverse proxy.

![Config Security Group](/images/5-Workshop/5.4-AWS-EC2/config-sg.png)

#### 5. Launch instance

1. Kiểm tra lại phần **Summary**.
2. Nhấn **Launch instance**.
3. Chờ vài phút để instance chuyển sang trạng thái **Running**.

![Launch Summary](/images/5-Workshop/5.4-AWS-EC2/launch-summary.png)

#### 6. Kết quả thực tế

Sau khi tạo thành công, AWS sẽ hiển thị mã instance và thông báo khởi tạo hoàn tất.

![EC2 launch success](/images/5-Workshop/5.4-AWS-EC2/z8007993502305_c977416dc91cb6dd7fa401b0e8741e0e.jpg)