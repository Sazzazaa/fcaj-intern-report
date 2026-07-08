---
title : "Dọn dẹp tài nguyên"
date : 2026-07-07
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Dọn dẹp tài nguyên

Sau khi hoàn thành workshop triển khai hệ thống Project Management trên AWS, bước dọn dẹp tài nguyên là cần thiết để tránh phát sinh chi phí không mong muốn. Việc xóa nên được thực hiện theo từng nhóm dịch vụ, đi từ lớp ứng dụng bên ngoài vào các tài nguyên hạ tầng bên trong, để hạn chế lỗi phụ thuộc trong quá trình thao tác.

#### Thứ tự thực hiện khuyến nghị

1. **Gỡ frontend trên AWS Amplify**

   Trước tiên, mở **AWS Amplify** và kiểm tra ứng dụng đã được deploy. Nếu không còn nhu cầu giữ môi trường demo, có thể xóa branch đang sử dụng hoặc xóa toàn bộ app hosting.

2. **Xóa cấu hình xác thực trên Amazon Cognito**

   Tiếp theo, vào **Amazon Cognito** để rà soát các thành phần sau:

   - User Pool đã tạo cho project
   - App Client đi kèm
   - Các user test không còn cần dùng

   Nếu hệ thống không còn sử dụng lại, nên xóa toàn bộ User Pool để tránh giữ các cấu hình xác thực không cần thiết.

3. **Xóa API trên Amazon API Gateway**

   Sau phần xác thực, vào **API Gateway** và tiến hành xóa:

   - HTTP API hoặc REST API đã tạo
   - Stage deploy liên quan
   - Authorizer nếu được tạo riêng cho bài lab

4. **Xóa Lambda Trigger**

   Nếu trong quá trình triển khai có sử dụng Lambda để xử lý post-confirmation hoặc các trigger liên quan đến Cognito, cần:

   - Gỡ trigger ra khỏi User Pool
   - Xóa function Lambda nếu không dùng nữa

5. **Dừng và xóa EC2 backend**

   Tại **EC2 Console**, thực hiện lần lượt các bước sau:

   - Stop instance để kiểm tra lần cuối
   - Terminate instance backend nếu không cần giữ
   - Xóa Elastic IP nếu có gán riêng
   - Xóa key pair trên AWS nếu không còn sử dụng

6. **Xóa cơ sở dữ liệu Amazon RDS**

   Đối với **Amazon RDS**, cần cân nhắc trước khi xóa để tránh mất dữ liệu cần lưu trữ. Tại **RDS Console**, có thể chọn một trong hai hướng:

   - **Giữ final snapshot** nếu muốn sao lưu dữ liệu trước khi kết thúc
   - **Không giữ snapshot** nếu đây chỉ là môi trường lab và không còn nhu cầu phục hồi

   Sau khi xác định phương án phù hợp, tiến hành xóa database instance.

7. **Xóa S3 bucket lưu hình ảnh**

   Tại **Amazon S3**, thực hiện dọn dẹp theo thứ tự:

   - Xóa toàn bộ object trong bucket
   - Xác nhận bucket rỗng
   - Xóa bucket chứa ảnh hoặc static assets của project

8. **Xóa Security Group và tài nguyên mạng phụ trợ**

   Sau khi EC2 và RDS đã được xóa, có thể tiếp tục xử lý các tài nguyên mạng đi kèm:

   - Security Group dùng riêng cho EC2
   - Security Group dùng riêng cho RDS
   - DB subnet group nếu tạo riêng

9. **Xóa subnet, route table, internet gateway và VPC**

   Nếu VPC này chỉ được tạo riêng cho workshop, nên xóa theo đúng thứ tự sau:

   - Subnet
   - Route table tùy chỉnh
   - Internet Gateway (detach trước, rồi delete)
   - VPC

#### Lưu ý cuối cùng

Trước khi xóa hoàn toàn tài nguyên, cần kiểm tra lại rằng các nội dung sau đã được lưu đầy đủ:

- Source code cuối cùng
- Ảnh chụp màn hình để viết báo cáo
- Link demo hoặc thông tin cấu hình quan trọng nếu cần đối chiếu sau này