---
title : "Cấu hình Internet Gateway & Route Tables"
date : 2026-07-04 
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### 1. Khởi tạo và gắn Internet Gateway (IGW)

Internet Gateway cho phép tài nguyên bên trong Public Subnet (máy chủ EC2) giao tiếp với Internet.

**Step 1:** Trong thanh điều hướng bên trái của VPC Console, chọn **Internet Gateways** -> **Create internet gateway**.
![IGW](/images/5-Workshop/5.3-AWS-VPC/igw.png)

**Step 2:** Nhập **Name tag** là `pm_internet-gateway` và nhấn **Create internet gateway**.
![Create IGW](/images/5-Workshop/5.3-AWS-VPC/create-gateway.png)

**Step 3:** Sau khi tạo xong, IGW sẽ ở trạng thái *Detached*. Nhấn nút **Actions** -> **Attach to VPC**.
![attach button](/images/5-Workshop/5.3-AWS-VPC/attach-to-vpc.png)

**Step 4:** Chọn `pm_vpc` từ danh sách và nhấn **Attach internet gateway**.

![Attach IGW](/images/5-Workshop/5.3-AWS-VPC/attach-igw.png)
---

#### 2. Khởi tạo Route Tables

Chúng ta cần tách biệt Route Table để đảm bảo Private Subnet không có đường dẫn ra Internet.

**Step 1:** Chọn **Route Tables** ở thanh điều hướng trái -> **Create route table**.
![route table button](/images/5-Workshop/5.3-AWS-VPC/create-route-table-button.png)

**Step 2:** Tạo lần lượt 3 Route Tables và liên kết tất cả với `pm_vpc`:
*   `pm_public-route-table-1`    
*   `pm_private-route-table-1`
*   `pm_private-route-table-2`
![create route table 1](/images/5-Workshop/5.3-AWS-VPC/create-route-table-button.png)

---

#### 3. Cấu hình định tuyến Public & Gắn Subnet

**Step 1:** Cấu hình định tuyến ra Internet cho Public Route Table:
*   Chọn `pm_public-route-table-1` từ danh sách.
*   Chuyển sang tab **Routes** ở nửa dưới màn hình -> Chọn **Edit routes**.
   *   ![Select edit](/images/5-Workshop/5.3-AWS-VPC/select-edit-route-table.png)

*   Nhấn **Add route**. Điền Destination: `0.0.0.0/0`. Tại Target, chọn **Internet Gateway** và trỏ tới `pm_internet-gateway`.
*   Nhấn **Save changes**.

* ![Edit public route table](/images/5-Workshop/5.3-AWS-VPC/edit-route-table.png)
*(Lưu ý: Chụp màn hình thao tác thêm route 0.0.0.0/0 trỏ tới IGW tương đương mốc 07:41:15)*

**Step 2:** Gắn các Subnet vào đúng Route Table tương ứng:
*   **Public RT:** Chọn `pm_public-route-table-1` -> Tab **Subnet associations** -> **Edit subnet associations** -> Tích chọn `pm_public-subnet-1` -> Save.
*   ![edit subnet button](/images/5-Workshop/5.3-AWS-VPC/button-edit-subnet.png)

*   **Private RT 1:** Chọn `pm_private-route-table-1` -> Tab **Subnet associations** -> Tích chọn `pm_private-subnet-1` -> Save.
*   **Private RT 2:** Chọn `pm_private-route-table-2` -> Tab **Subnet associations** -> Tích chọn `pm_private-subnet-2` -> Save.
*   ![edit subnet](/images/5-Workshop/5.3-AWS-VPC/edit-subnet.png)

---

#### 4. Test & Validation (Kiểm tra kết quả)

*   Tại danh sách **Route Tables**, kiểm tra tab **Routes** của `pm_private-route-table-1` và `pm-private-route-table-2`.
*   **Kết quả mong đợi:** Các Private Route Tables này **KHÔNG** có route trỏ tới `0.0.0.0/0` (chỉ có route `local`). Điều này xác nhận database của chúng ta đã được cô lập an toàn khỏi Internet công cộng.
*   ![check route](/images/5-Workshop/5.3-AWS-VPC/check-route.png)