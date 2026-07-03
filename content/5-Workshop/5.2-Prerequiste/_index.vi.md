---
title : "Các bước chuẩn bị"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. Yêu cầu tài khoản & Region (AWS Account & Region)

Để thực hiện workshop này, bạn cần có một tài khoản AWS đang hoạt động. Khuyến nghị sử dụng tài khoản mới tạo để tận dụng gói **AWS Free Tier** (Miễn phí 12 tháng cho nhiều dịch vụ cốt lõi như EC2, RDS).
*To complete this workshop, you need an active AWS account. A newly created account is recommended to take advantage of the **AWS Free Tier** (12 months free for core services like EC2, RDS).*

Trong toàn bộ bài Lab này, để giảm thiểu độ trễ (latency) và đảm bảo tính thống nhất, chúng ta sẽ chọn chung một Khu vực (Region):
*Throughout this Lab, to minimize latency and ensure consistency, we will uniformly use a single Region:*
*   **Region Name:** `ap-southeast-1`
*   **Region Location:** Singapore

![AWS Region Selection](/images/5-Workshop/5.2/aws-region.png)
*(Lưu ý: Chụp màn hình góc trên cùng bên phải của AWS Console, khoanh đỏ hoặc highlight chỗ bạn đang chọn region ap-southeast-1)*

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
*This workshop is designed to be completely free ($0) if you strictly follow the Free Tier configurations. However, to manage cloud cost risks, we must mandate the creation of a budget alert.*

**Step 1:** Từ giao diện AWS Console, tìm kiếm dịch vụ **Billing and Cost Management**.
*From the AWS Console, search for the **Billing and Cost Management** service.*

**Step 2:** Ở thanh điều hướng bên trái, chọn **Budgets** $\rightarrow$ **Create budget**.
*In the left navigation pane, select **Budgets** $\rightarrow$ **Create budget**.*

**Step 3:** Dưới mục *Budget setup*, chọn **Use a template (simplified)**. Trong phần *Templates*, chọn **Zero spend budget**. 
*Under *Budget setup*, choose **Use a template (simplified)**. In the *Templates* section, select **Zero spend budget**.*

**Step 4:** Nhập địa chỉ Email của bạn vào ô **Email recipients** và nhấn **Create budget**. Hệ thống sẽ tự động cảnh báo qua email nếu chi phí dự án bắt đầu phát sinh vượt mức `$0.01`.
*Enter your email address in the **Email recipients** field and click **Create budget**. The system will automatically email you if the project cost exceeds `$0.01`.*

![Zero Spend Budget Config](/images/5-Workshop/5.2/zero-spend-budget.png)
*(Lưu ý: Chụp màn hình lúc bạn đang điền Email để tạo Budget (Tương đương mốc 07:26:15 trong video))*

---

#### 4. Chuẩn bị Mã nguồn dự án (Project Source Code)

Khác với các bài lab tự động dùng mã CloudFormation, trong workshop này, chúng ta sẽ tự tay triển khai hạ tầng từ đầu (from scratch). Bạn cần đẩy mã nguồn ứng dụng (gồm cả frontend và backend) lên GitHub Repository cá nhân để chuẩn bị cho quá trình Upload và CI/CD sau này.
*Unlike automated CloudFormation labs, we will provision the infrastructure from scratch. You need to push the application source code (both frontend and backend) to your personal GitHub Repository to prepare for the subsequent Upload and CI/CD processes.*

Mở Terminal (hoặc Git Bash) trên máy tính của bạn và chạy lệnh sau để thiết lập:
*Open your Terminal (or Git Bash) on your computer and run the following commands:*

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

![GitHub Repository](/images/5-Workshop/5.2/github-repo.png)
*(Lưu ý: Chụp màn hình giao diện trang GitHub cá nhân của bạn hiển thị Repository đã chứa đầy đủ 2 thư mục `client` và `server` (Tương đương mốc 07:21:20 trong video))*