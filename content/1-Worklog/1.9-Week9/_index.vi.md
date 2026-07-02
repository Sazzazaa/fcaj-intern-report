---
title: "Worklog Tuần 9"
date: 2026-06-30
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
* Cấu hình lưu trữ hình ảnh trên Amazon S3 với Bucket Policy.
* Tích hợp hệ thống quản lý danh tính (IAM) và xác thực người dùng bằng Amazon Cognito.
* Tích hợp giao diện đăng nhập/đăng ký vào ứng dụng Next.js bằng AWS Amplify UI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 2 | - Khởi tạo **Amazon S3 Bucket** lưu trữ tài nguyên tĩnh (Hình ảnh).<br>- Tắt Block Public Access và cấu hình S3 Bucket Policy cho phép `s3:GetObject`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Khởi tạo **Amazon Cognito User Pool**.<br>- Cấu hình định dạng đăng nhập, chính sách mật khẩu và tạo App Client. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Cài đặt gói `aws-amplify` và `@aws-amplify/ui-react` trên Frontend Next.js.<br>- Xây dựng Auth Provider với **Authenticator UI** tích hợp sẵn của AWS. | 01/07/2026 | 01/07/2026 | |
| 5 | - Cấu hình trường tuỳ chỉnh (Custom form fields) trong Authenticator cho phép người dùng đăng ký gồm: Email, Username, Password. | 02/07/2026 | 02/07/2026 | |
| 6 | - Kiểm thử luồng gửi email xác thực mã Code (Verification Code) qua Cognito.<br>- Bóc tách biến môi trường `NEXT_PUBLIC_COGNITO_USER_POOL_ID`. | 03/07/2026 | 03/07/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 9:
* Toàn bộ tài nguyên hình ảnh tĩnh của hệ thống đã được đẩy lên Amazon S3 và trỏ link thành công vào giao diện Frontend.
* Cấu hình hoàn chỉnh Amazon Cognito User Pool để quản lý danh tính người dùng.
* Tích hợp mượt mà giao diện Đăng ký / Đăng nhập chuyên nghiệp lên Next.js bằng Amplify UI mà không cần tự code form xác thực.