---
title : "Cài đặt môi trường và chuẩn bị backend"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

### Kết nối EC2, cài Node.js và tải mã nguồn

Sau khi instance đã chạy, chúng ta SSH vào máy để cài môi trường thực thi và clone mã nguồn backend.

#### 1. SSH vào EC2

Từ máy local, sử dụng file `.pem` đã tải để kết nối:

```bash
ssh -i "C:\Users\admin\Downloads\pm-key.pem" ec2-user@<public-dns-or-public-ip>
```

Sau khi vào được máy, nạp lại shell và chọn phiên bản Node phù hợp:

```bash
source ~/.bashrc
nvm use node
```

![SSH and install environment](/images/5-Workshop/5.4-AWS-EC2/z8014660664709_d852d8aca4a9c0b88cf677c434a0945a.jpg)

#### 2. Cài dependency và clone repo

```bash
sudo yum update -y
sudo yum install git -y

git clone https://github.com/Sazzazaa/project-management-aws.git
cd ~/project-management-aws/server
npm install
```

Nếu bạn chưa cài Node.js trên EC2, có thể tham khảo lại các bước cài NVM/Node ở hình minh họa bên dưới:

![Install Nodejs](/images/5-Workshop/5.4-AWS-EC2/install-nodejs.png)
![Install Nodejs 2](/images/5-Workshop/5.4-AWS-EC2/install-nodejs1.png)

#### 3. Chuẩn bị file `.env`

Ở giai đoạn đầu, bạn có thể tạo file `.env` trước với `PORT`. Sau khi hoàn tất phần RDS ở bước 5.5, quay lại bổ sung `DATABASE_URL`.

```bash
cat > .env <<EOF
PORT=8000
DATABASE_URL="postgresql://<db-username>:<db-password>@<rds-endpoint>:5432/project_management_aws?schema=public"
EOF
```

![Config Env](/images/5-Workshop/5.4-AWS-EC2/config-env0.png)
![Config Env 2](/images/5-Workshop/5.4-AWS-EC2/config-env.png)

#### 4. Chuẩn bị cho bước tiếp theo

Đến đây, EC2 đã sẵn sàng nhận kết nối tới cơ sở dữ liệu. Ở phần **5.5 AWS RDS**, chúng ta sẽ:

* tạo PostgreSQL trên RDS,
* mở rule kết nối giữa `pm-ec2-sg` và `pm-rds-sg`,
* migrate và seed dữ liệu cho backend.