---
title: "Worklog Tuần 2"
date: 2026-05-17
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Triển khai các ứng dụng tính toán trên môi trường máy chủ ảo.
* Quản lý và thao tác hạ tầng bằng giao diện dòng lệnh (AWS CLI).
* Cấp quyền giao tiếp an toàn giữa các dịch vụ và lưu trữ web tĩnh.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 2 | - Triển khai máy chủ ảo: **Getting Started and Deploying Applications on Amazon Compute Cloud (Amazon EC2)**. | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Quản trị qua dòng lệnh: **Using AWS CLI on Amazon EC2 (Windows/Ubuntu)**.<br>- Tìm hiểu cách cấu hình credentials cho AWS CLI. | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Phân quyền dịch vụ: **Grant application permissions to access AWS services through IAM Role (AWS IAM)**.<br>- Phân biệt giữa IAM User và IAM Role. | 13/05/2026 | 13/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Lưu trữ web tĩnh: **Hosting static website with Amazon S3**.<br>- Tìm hiểu về S3 Bucket, Object và Bucket Policy. | 14/05/2026 | 14/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành:**<br>&emsp; + Triển khai một website tĩnh cơ bản trên Amazon S3.<br>&emsp; + Gắn IAM Role cho EC2 để gọi lệnh CLI truy cập vào S3 an toàn. | 15/05/2026 | 15/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:
* Khởi tạo và truy cập thành công máy chủ Amazon EC2 chạy hệ điều hành Ubuntu/Windows.
* Thành thạo thao tác cấu hình và gọi lệnh dịch vụ bằng AWS CLI ngay trong máy chủ EC2.
* Hiểu và cấu hình thành công IAM Role, cho phép EC2 tương tác với các dịch vụ khác (như S3) mà không cần lưu trữ Hard-code Access Keys.
* Triển khai thành công tính năng Static Website Hosting trên Amazon S3.