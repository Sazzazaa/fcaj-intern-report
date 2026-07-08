---
title : "Các bước chuẩn bị"
date : 2026-07-04 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. Yêu cầu tài khoản & Region (AWS Account & Region)

Để thực hiện workshop này, bạn cần có một tài khoản AWS đang hoạt động. Khuyến nghị sử dụng tài khoản mới tạo để tận dụng gói **AWS Free Tier** (Miễn phí 12 tháng cho nhiều dịch vụ cốt lõi như EC2, RDS).


Trong toàn bộ bài Lab này, để giảm thiểu độ trễ (latency) và đảm bảo tính thống nhất, chúng ta sẽ chọn chung một Khu vực (Region):
*   **Region Name:** `ap-southeast-1`
*   **Region Location:** Singapore

![AWS Region Selection](/images/5-Workshop/5.2-Prerequisite/aws-region.png)


---

#### 2. Phân quyền IAM (IAM Permissions)

Để có thể khởi tạo các dịch vụ (VPC, EC2, RDS, Cognito, Amplify...), tài khoản IAM User mà bạn đang dùng để đăng nhập cần có đủ quyền hạn. Khuyến nghị gán quyền `AdministratorAccess` cho môi trường thực hành, hoặc bạn có thể tạo và gắn IAM inline-policy với mã JSON dưới đây cho User của bạn:
*To provision services, your logged-in IAM User needs sufficient permissions. It is recommended to attach `AdministratorAccess` for the lab environment, or you can attach the following JSON inline-policy to your User:*

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ProjectManagementLabPermissions",
            "Effect": "Allow",
            "Action": [
                "ec2:*",
                "rds:*",
                "cognito-idp:*",
                "s3:*",
                "apigateway:*",
                "amplify:*",
                "lambda:*",
                "iam:PassRole",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "budgets:*"
            ],
            "Resource": "*"
        }
    ]
}
```

---

#### 3. Thiết lập Cảnh báo chi phí (AWS Budgets - Zero Spend Budget)

Workshop này được thiết kế để hoàn toàn miễn phí ($0) nếu bạn tuân thủ các cấu hình Free Tier. Tuy nhiên, để quản trị rủi ro chi phí điện toán đám mây, chúng ta bắt buộc phải tạo một cảnh báo ngân sách.


**Step 1:** Từ giao diện AWS Console, tìm kiếm dịch vụ **Billing and Cost Management**.


**Step 2:** Ở thanh điều hướng bên trái, chọn **Budgets** -> **Create budget**.

**Step 3:** Dưới mục *Budget setup*, chọn **Use a template (simplified)**. Trong phần *Templates*, chọn **Zero spend budget**. 

**Step 4:** Nhập địa chỉ Email của bạn vào ô **Email recipients** và nhấn **Create budget**. Hệ thống sẽ tự động cảnh báo qua email nếu chi phí dự án bắt đầu phát sinh vượt mức `$0.01`.

![Zero Spend Budget Config](/images/5-Workshop/5.2-Prerequisite/zero-spend-budget.png)

---

#### 4. Chuẩn bị Mã nguồn dự án (Project Source Code)

Khác với các bài lab tự động dùng mã CloudFormation, trong workshop này, chúng ta sẽ tự tay triển khai hạ tầng từ đầu (from scratch). Bạn cần đẩy mã nguồn ứng dụng (gồm cả frontend và backend) lên GitHub Repository cá nhân để chuẩn bị cho quá trình Upload và CI/CD sau này.


Mở Terminal (hoặc Git Bash) trên máy tính của bạn và chạy lệnh sau để thiết lập:

```bash
# Clone repository gốc của dự án
git clone https://github.com/Sazzazaa/project-management-aws

# Di chuyển vào thư mục dự án
cd project-management

# Cài đặt thư viện cho máy khách và máy chủ
cd client && npm install
cd ../server && npm install

# Dọn dẹp .gitignore cũ và đẩy lên Repository mới của riêng bạn
rm -rf client/.git
rm -rf server/.git
git init
git add .
git commit -m "Initial commit for AWS Deployment"
git remote add origin <LINK_GITHUB_REPO_CỦA_BẠN>
git push -u origin master
```

![GitHub Repository](/images/5-Workshop/5.2-Prerequisite/github-repo.png)