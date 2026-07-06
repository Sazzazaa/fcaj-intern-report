---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Project Management Dashboard trên nền tảng AWS
## Đề xuất triển khai kiến trúc Ứng dụng Web 3 lớp (3-Tier Architecture)

### 1. Tổng quan dự án (Project Overview)
Dự án **Project Management Dashboard** là một ứng dụng web toàn diện (Full-stack) được thiết kế nhằm hỗ trợ các cá nhân và nhóm làm việc theo dõi tiến độ, quản lý tác vụ (tasks) và phân bổ tài nguyên hiệu quả. Thay vì chỉ chạy thử nghiệm trên môi trường máy cá nhân (localhost), dự án này tập trung vào việc thiết kế kiến trúc hạ tầng và triển khai toàn bộ hệ thống (Frontend Next.js, Backend Node.js, Database PostgreSQL) lên hệ sinh thái điện toán đám mây Amazon Web Services (AWS) theo tiêu chuẩn của doanh nghiệp (Enterprise standard).

### 2. Mục tiêu (Objectives)
* **Chuyển đổi số toàn diện:** Đưa thành công ứng dụng từ môi trường Local lên môi trường Production (AWS Cloud).
* **Tính sẵn sàng và mở rộng (High Availability & Scalability):** Đảm bảo ứng dụng có thể chịu tải tốt và hoạt động liên tục 24/7 thông qua việc phân tách các dịch vụ.
* **Bảo mật hệ thống (Security):** Cô lập cơ sở dữ liệu khỏi Internet công cộng thông qua Mạng lưới ảo (VPC) và quản lý định danh an toàn với Amazon Cognito.
* **Tối ưu chi phí:** Thiết kế kiến trúc tận dụng tối đa gói AWS Free Tier (750 giờ EC2/RDS miễn phí mỗi tháng) để ngân sách duy trì ở mức thấp nhất.

### 3. Vấn đề cần giải quyết (Problem Statement)
* **Vấn đề hiện tại:** Các hệ thống quản lý dự án tự lưu trữ (on-premise) hoặc chạy trên các máy chủ nguyên khối (Monolithic) truyền thống thường gặp khó khăn trong việc mở rộng khi lượng dữ liệu và người dùng tăng. Việc tự xây dựng luồng xác thực (Authentication) bảo mật tốn rất nhiều thời gian và dễ xảy ra lỗ hổng. Ngoài ra, việc lưu trữ cơ sở dữ liệu chung với máy chủ ứng dụng tạo ra rủi ro mất mát dữ liệu nghiêm trọng nếu máy chủ bị tấn công.
* **Giải pháp đề xuất:** Phân tách hệ thống thành mô hình 3 lớp. Sử dụng Managed Database (AWS RDS) để đảm bảo an toàn dữ liệu; dùng dịch vụ định danh chuyên biệt (AWS Cognito) để gỡ bỏ gánh nặng bảo mật; và tự động hóa quy trình phân phối giao diện tới người dùng cuối thông qua AWS Amplify.

### 4. Kiến trúc giải pháp (Solution Architecture)
Nền tảng áp dụng kiến trúc 3 lớp (Frontend - Backend - Database) được phân bổ vào các dịch vụ chuyên biệt của AWS, đặt bên trong một VPC (Virtual Private Cloud) có phân chia Subnet rõ ràng.

![Project Architecture](/images/2-Proposal/aws-architecture.png)
*(Lưu ý: Bạn hãy chèn ảnh sơ đồ kiến trúc AWS của hệ thống vào đây)*

*Thiết kế các thành phần & Dịch vụ AWS sử dụng:*
- **AWS VPC (Mạng lưới ảo):** Tạo 1 Public Subnet (cho EC2) để kết nối với Internet qua Internet Gateway và 2 Private Subnets (cho RDS) để cô lập dữ liệu.
- **Amazon Cognito:** Cung cấp giao diện Đăng nhập/Đăng ký an toàn, gửi mã xác thực qua email và cấp phát JWT Token. Kết hợp với một **AWS Lambda Trigger** để tự động đồng bộ thông tin người dùng mới xuống cơ sở dữ liệu sau khi đăng ký thành công.
- **AWS RDS (PostgreSQL):** Cơ sở dữ liệu quan hệ được quản lý bởi AWS, lưu trữ toàn bộ dữ liệu nghiệp vụ (Project, Task, User).
- **AWS EC2 (Ubuntu):** Máy chủ ảo chạy môi trường Node.js/Express (Backend), sử dụng PM2 để quản lý tiến trình chạy ngầm. Giao tiếp với Database qua cổng nội bộ.
- **Amazon API Gateway:** Cổng giao tiếp trung gian giúp định tuyến (proxy) và chuyển đổi giao thức an toàn từ HTTPS (Frontend) sang HTTP (Backend EC2).
- **Amazon S3:** Bucket lưu trữ độc lập các tệp tin tĩnh và phương tiện (Ví dụ: Ảnh đại diện người dùng, tệp đính kèm dự án).
- **AWS Amplify:** Nền tảng CI/CD tự động kéo mã nguồn Frontend (Next.js) từ GitHub, tiến hành build và phân phối (hosting) ra mạng toàn cầu với chứng chỉ bảo mật HTTPS có sẵn.

### 5. Timeline (Lộ trình triển khai)
Dự án dự kiến được triển khai theo lộ trình 5 giai đoạn:
* **Giai đoạn 1: Chuẩn bị & Đánh giá (Tuần 1):** Chuẩn bị mã nguồn local, thiết kế sơ đồ kiến trúc AWS, tính toán chi phí và thiết lập tài khoản AWS.
* **Giai đoạn 2: Thiết lập Nền tảng Bảo mật & Dữ liệu (Tuần 2):** Khởi tạo VPC (Subnets, Route Tables, Internet Gateway). Tạo AWS RDS PostgreSQL và thiết lập Amazon Cognito cùng Lambda trigger.
* **Giai đoạn 3: Triển khai Backend & Lưu trữ (Tuần 3):** Khởi chạy EC2, cài đặt môi trường Node.js. Chạy seed data vào RDS. Khởi tạo S3 bucket và cấp quyền Public Access cho tệp tin tĩnh.
* **Giai đoạn 4: Triển khai Frontend & Định tuyến (Tuần 4):** Đẩy mã nguồn lên GitHub, kết nối với AWS Amplify. Thiết lập API Gateway để Frontend kết nối thông suốt với Backend.
* **Giai đoạn 5: Kiểm thử & Bàn giao (Tuần 5):** Kiểm thử luồng End-to-End (Tạo dự án mới, cập nhật Task dạng Drag & Drop). Hoàn thiện tài liệu Workshop và chuẩn bị các lệnh Dọn dẹp tài nguyên (Clean-up).

### 6. Ngân sách (Budget)
Dự án được triển khai tại khu vực **Asia Pacific (Singapore)** với mức phí On-Demand (Dùng bao nhiêu trả bấy nhiêu). Mặc dù các tài khoản mới có thể tận dụng **AWS Free Tier** để giảm thiểu tối đa chi phí, bảng dưới đây thể hiện mức chi phí thực tế khi không có Free Tier (rất hữu ích để tính toán khi sử dụng quỹ AWS Credits):

* **Amazon EC2 (t3.micro):** ~$10.41 / tháng (Bao gồm chi phí máy chủ chạy 24/7 và ổ cứng EBS).
* **Amazon RDS for PostgreSQL (db.t3.micro - Single-AZ):** ~$23.20 / tháng (Bao gồm máy chủ database và 20GB dung lượng lưu trữ).
* **Amazon Cognito:** ~$5.01 / tháng (Phí quản lý xác thực và phân quyền người dùng).
* **AWS Amplify:** ~$1.80 / tháng (Chi phí băng thông phục vụ và phút build mã nguồn).
* **Amazon API Gateway:** ~$0.42 / tháng (Cửa ngõ REST API).
* **Amazon S3:** ~$0.25 / tháng (Lưu trữ hình ảnh và tệp tĩnh).
* **AWS Lambda:** $0.00 / tháng (Luôn miễn phí do lượng request nằm trong giới hạn Always Free).

* **Tổng ngân sách dự kiến:** **~$41.09 / tháng** (Tương đương ~$493.08 / năm).

### 7. Rủi ro (Risk Assessment)
*Ma trận rủi ro & Cách giảm thiểu:*
1. **Phát sinh chi phí ngoài ý muốn (Rủi ro: Cao):** Do vô tình chọn sai cấu hình (Ví dụ: bật RDS Multi-AZ hoặc cấp phát nhiều Elastic IP).
   * *Giảm thiểu:* Bắt buộc cài đặt cảnh báo ngân sách (AWS Budgets zero-spend). Rà soát kỹ bảng giá và tag "Free tier eligible" trước khi tạo dịch vụ. Xóa sạch tài nguyên (Clean-up) ngay sau khi báo cáo xong.
2. **Lỗi kết nối giữa các dịch vụ (Rủi ro: Trung bình):** Frontend không gọi được API, Backend bị từ chối truy cập Database.
   * *Giảm thiểu:* Lập bản đồ các **Security Group** cẩn thận. Đảm bảo RDS mở port 5432 cho IP nội bộ của EC2, và EC2 mở port cho phép API Gateway truy cập.
3. **Rò rỉ thông tin bảo mật (Rủi ro: Cao):** Vô tình commit các chuỗi kết nối (Database URL), Secret Keys lên GitHub công khai.
   * *Giảm thiểu:* Lưu trữ toàn bộ thông tin nhạy cảm trong file `.env` và thêm file này vào `.gitignore`. Sử dụng chức năng Environment Variables tích hợp sẵn trong AWS Amplify và EC2 để quản lý.