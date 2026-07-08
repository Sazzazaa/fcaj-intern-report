---
title : "Tạo RDS PostgreSQL"
date : 2026-07-04
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

### Khởi tạo PostgreSQL trên Amazon RDS

#### 1. Mở dịch vụ RDS

1. Tìm kiếm `RDS` trên AWS Console.
2. Chọn **Databases**.
3. Nhấn **Create database**.

#### 2. Cấu hình cơ bản

Khi tạo database, có thể dùng cấu hình tương tự:

* **Engine type**: PostgreSQL
* **Template**: Free tier
* **DB instance identifier**: `project-management-db`
* **Master username**: ví dụ `postgres`
* **DB instance class**: `db.t3.micro` hoặc cấu hình Free Tier tương đương
* **Initial database name**: `project_management_aws`

#### 3. Cấu hình kết nối mạng

Ở phần **Connectivity**:

* Chọn đúng **VPC** đã dùng cho EC2.
* Đặt database vào **private subnets**.
* **Public access**: `No`
* **VPC security group**: tạo mới hoặc chọn `pm-rds-sg`
* **Database port**: `5432`

#### 4. Chờ RDS khởi tạo

Sau khi nhấn **Create database**, trạng thái ban đầu sẽ là **Creating**.

![RDS creating](/images/5-Workshop/5.5-AWS-RDS/z8007964995120_4ae5126884b8b2c034b6aae6e646f5b3.jpg)

Khi hoàn tất, trạng thái chuyển sang **Available**.

![RDS available](/images/5-Workshop/5.5-AWS-RDS/z8007996839089_2b855aa77f72204f2e7ff7d3ca5e659b.jpg)

#### 5. Lưu lại endpoint

Sau khi RDS sẵn sàng, mở trang chi tiết của database và sao chép **endpoint**. Endpoint này sẽ được dùng trong file `.env` trên EC2:

```bash
DATABASE_URL="postgresql://<db-username>:<db-password>@<rds-endpoint>:5432/project_management_aws?schema=public"
```