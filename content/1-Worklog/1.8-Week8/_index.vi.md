---
title: "Worklog Tuần 8"
date: 2026-06-28
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
* Triển khai máy chủ ứng dụng Backend lên Amazon EC2.
* Tối ưu hóa vận hành máy chủ bằng PM2 Process Manager.
* Xây dựng cổng trung gian HTTPS qua Amazon API Gateway để xử lý Mixed Content.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 2 | - Khởi tạo **Amazon EC2 (Amazon Linux 2023)** trong Public Subnet.<br>- Cấu hình EC2 Security Group: Mở Port 22 (SSH) và Port 80 (HTTP). | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - SSH vào EC2, cài đặt môi trường chạy: Node.js, NVM, Git.<br>- Git Clone mã nguồn server, cài đặt **PM2** để tự động khởi động lại Backend. | 23/06/2026 | 23/06/2026 | |
| 4 | - Cấu hình biến môi trường trên EC2 kết nối với Amazon RDS.<br>- Chạy `npx prisma generate` và thực hiện đồng bộ cơ sở dữ liệu trên Cloud. | 24/06/2026 | 24/06/2026 | |
| 5 | - Khởi tạo **Amazon API Gateway (REST API)**, tạo tài nguyên dạng `/{proxy+}`.<br>- Thiết lập **HTTP Proxy Integration** trỏ về IP của máy chủ EC2. Cấu hình CORS. | 25/06/2026 | 25/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Deploy API Gateway lên stage `prod` để lấy URL có chứng chỉ HTTPS bảo mật.<br>- Thay thế biến môi trường API Local trên Frontend bằng URL của API Gateway. | 26/06/2026 | 26/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:
* Máy chủ Node.js Backend đã được deploy thành công và chạy ổn định trên Amazon EC2 bằng PM2.
* Hệ thống cơ sở dữ liệu RDS đã được kết nối thành công từ môi trường EC2.
* Giải quyết triệt để lỗi Mixed Content (HTTP/HTTPS) bằng cách sử dụng Amazon API Gateway làm Proxy bọc bên ngoài EC2.