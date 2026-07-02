---
title: "Worklog Tuần 6"
date: 2026-06-14
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:
* Triển khai các API cốt lõi trên Node.js/Express Backend.
* Khởi tạo hạ tầng mạng Amazon VPC với đầy đủ các mạng con (Subnets).
* Triển khai Amazon RDS PostgreSQL vào khu vực mạng an toàn (Private Subnet).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 2 | - **Backend Task:** Cài đặt Express, cấu hình CORS, Helmet, Morgan logging.<br>- Viết các Controller xử lý logic GET/POST cho `projects` và `tasks`. | 08/06/2026 | 08/06/2026 | |
| 3 | - **Infra Task:** Tạo **Amazon VPC** tùy chỉnh với dải mạng CIDR Block.<br>- Tạo 1 Public Subnet (cho EC2) và 2 Private Subnets (cho RDS) khác AZs. | 09/06/2026 | 09/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Infra Task:** Thiết lập **Internet Gateway (IGW)**, gắn vào VPC.<br>- Cấu hình **Route Tables**: Cấp quyền ra internet cho Public Subnet. | 10/06/2026 | 10/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Infra Task:** Khởi tạo instance **Amazon RDS (PostgreSQL)** chuẩn Free Tier đặt trong Private Subnet.<br>- Cấu hình Security Group cho phép kết nối cổng 5432. | 11/06/2026 | 11/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Họp nhóm cập nhật tiến độ, test thử các API GET/POST Project thông qua Postman trên Local. | 12/06/2026 | 12/06/2026 | |

### Kết quả đạt được tuần 6:
* Đã lập trình xong các endpoint API cốt lõi cho Backend.
* Triển khai thành công kiến trúc mạng VPC bảo mật với các lớp Subnet riêng biệt.
* Khởi tạo thành công database PostgreSQL trên Amazon RDS, đảm bảo Database được cô lập khỏi Internet.