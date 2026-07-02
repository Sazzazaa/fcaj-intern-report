---
title: "Worklog Tuần 10"
date: 2026-06-30
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:
* Sử dụng AWS Lambda Trigger tự động đồng bộ hóa thông tin người dùng từ Cognito sang RDS.
* Triển khai ứng dụng Frontend lên Internet bằng dịch vụ AWS Amplify Hosting.
* Tối ưu hóa bảo mật mạng bằng Cognito Authorizer trên API Gateway và tổng kết đồ án.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 2 | - Tạo hàm **AWS Lambda (Post-Confirmation Trigger)** bằng Node.js.<br>- Lập trình Lambda kích hoạt sự kiện gọi HTTP POST xuống Backend EC2 để lưu thông tin User vào Database. | 06/07/2026 | 06/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Cấu hình bảo mật Backend: Gắn **Cognito Authorizer** vào API Gateway.<br>- Điều chỉnh RTK Query Frontend gửi kèm token JWT vào Header các API request. | 07/07/2026 | 07/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Cấu hình triển khai liên tục (CI/CD) cho ứng dụng Next.js trên **AWS Amplify Hosting**.<br>- Liên kết Amplify với GitHub và cấu hình các biến môi trường Production. | 08/07/2026 | 08/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Kiểm thử toàn diện toàn hệ thống từ Frontend (Amplify) -> API Gateway -> Backend (EC2) -> Database (RDS).<br>- Tối ưu hóa giao diện người dùng. | 09/07/2026 | 09/07/2026 | |
| 6 | - Hoàn thiện mã nguồn (Push code lên Git). | 10/07/2026 | 10/07/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 10:
* Tự động hóa hoàn toàn quy trình đồng bộ dữ liệu User giữa Cognito và PostgreSQL thông qua Lambda Trigger.
* API Backend được bảo vệ nghiêm ngặt bằng JWT Authorization thông qua Amazon API Gateway và Cognito.
* Triển khai thành công ứng dụng Frontend lên môi trường thực tế với CI/CD bằng AWS Amplify Hosting.
* Hoàn thiện 100% dự án Capstone, sẵn sàng nghiệm thu với đầy đủ tài liệu và Source Code chất lượng cao.