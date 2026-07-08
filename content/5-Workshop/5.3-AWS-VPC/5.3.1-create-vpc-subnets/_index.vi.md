---
title : "Khởi tạo VPC & Subnets"
date : 2026-07-04 
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### 1. Khởi tạo Virtual Private Cloud (VPC)

**Step 1:** Đăng nhập vào AWS Management Console. Trên thanh tìm kiếm, gõ `VPC` và truy cập vào dịch vụ VPC. Đảm bảo bạn đang ở Region đúng cho Workshop.
![Select VPC](/images/5-Workshop/5.3-AWS-VPC/select-vpc.png)

**Step 2:** Trong thanh điều hướng bên trái, chọn **Your VPCs**, sau đó nhấn nút **Create VPC**.

![Create VPC](/images/5-Workshop/5.3-AWS-VPC/create-vpc.png)

**Step 3:** Tại giao diện cấu hình, điền các thông số sau và nhấn **Create VPC**:
*   **Resources to create:** `VPC only`
*   **Name tag:** `pm-vpc`
*   **IPv4 CIDR block:** Chọn *IPv4 CIDR manual input* và điền `10.0.0.0/16`
![Select create VPC](/images/5-Workshop/5.3-AWS-VPC/select-create-vpc.png)

---

#### 2. Khởi tạo Subnets (Mạng con)

Hệ thống của chúng ta yêu cầu 3 Subnets: 1 Public Subnet cho EC2 và 2 Private Subnets (nằm ở 2 Availability Zones khác nhau) cho RDS Database.

**Step 1:** Trở lại thanh điều hướng trái, chọn **Subnets** -> **Create subnet**.
![Create subnet button](/images/5-Workshop/5.3-AWS-VPC/create-subnet-button.png)

**Step 2:** Tại mục **VPC ID**, chọn `pm-vpc` vừa tạo.

**Step 3:** Tiến hành tạo 3 Subnet với các cấu hình dưới đây (Nhấn *Add new subnet* để tạo nhiều Subnet cùng lúc):

*   **Subnet 1 (Public):**
    *   **Subnet name:** `pm_public-subnet-1`
    *   **Availability Zone:** `ap-southeast-1a`
    *   **IPv4 CIDR block:** `10.0.0.0/24`

*   **Subnet 2 (Private 1):**
    *   **Subnet name:** `pm_private-subnet-1`
    *   **Availability Zone:** `ap-southeast-1a`
    *   **IPv4 CIDR block:** `10.0.1.0/24`

*   **Subnet 3 (Private 2 - Bắt buộc cho RDS):**
    *   **Subnet name:** `pm_private-subnet-2`
    *   **Availability Zone:** `ap-southeast-1b` *(Khác với AZ của Subnet 1 & 2)*
    *   **IPv4 CIDR block:** `10.0.2.0/24`

![Create subnet button](/images/5-Workshop/5.3-AWS-VPC/create-subnet.png)

**Step 4:** Cuộn xuống cuối trang và nhấn **Create subnet**.

Sau khi hoàn tất, AWS sẽ hiển thị màn hình workflow xác nhận VPC, các subnet, route table và internet gateway đã được tạo thành công.

![Create VPC workflow success](/images/5-Workshop/5.3-AWS-VPC/z8007889978504_abaf388742a623b682b46742d309f93a.jpg)

---

#### 3. Test & Validation (Kiểm tra kết quả)

*   Truy cập lại bảng điều khiển **Subnets**.
*   Kiểm tra thanh tìm kiếm với bộ lọc `VPC = pm-vpc`.
*   **Kết quả mong đợi:** 3 Subnets (1 Public, 2 Private) hiển thị trạng thái **Available** với dải CIDR và AZs tương ứng chính xác.
![3 Subnets](/images/5-Workshop/5.3-AWS-VPC/3-subnets.png)