---
title: "Blog 3"
date: 2026-07-03
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# NGĂN CHẶN DATA EXFILTRATION TRONG MÔI TRƯỜNG ML VỚI AMAZON SAGEMAKER AI

Bài viết chia sẻ case study thực tế từ iBusiness về cách giải quyết bài toán bảo mật dữ liệu nhạy cảm cho các data scientist. Bằng cách thiết lập kiến trúc bảo mật 3 lớp kết hợp Amazon SageMaker AI, hệ thống này ngăn chặn hoàn toàn việc tuồn dữ liệu ra ngoài (data exfiltration) mà không cần dùng đến các hạ tầng VDI đắt đỏ.

Các điểm chính cần nắm:

* **Layer 1 - WorkSpaces Secure Browser:** Khóa chặt đầu vào bằng môi trường trình duyệt được quản lý, vô hiệu hóa hoàn toàn chức năng upload/download, copy-paste và in ấn trực tiếp từ client.
* **Layer 2 - URL Allowlisting & VPC Endpoints:** Chỉ cho phép truy cập các domain cụ thể của AWS và sử dụng mạng nội bộ để ép người dùng phải login vào đúng account của tổ chức, chặn đứng nguy cơ đẩy data sang tài khoản cá nhân.
* **Layer 3 - Cách ly môi trường SageMaker:** Ngắt toàn bộ kết nối Internet của VPC chứa SageMaker, mọi tương tác với các dịch vụ khác (như S3) phải đi qua VPC Endpoints với granular policies quản lý nghiêm ngặt các API calls.
* **Tiết kiệm chi phí vận hành:** Cắt giảm chi phí môi trường phát triển từ hơn $40/user/tháng (VDI) xuống chỉ còn $7/user/tháng.
* **Tăng tốc triển khai:** Nhờ tự động hóa, thời gian cấp phát môi trường làm việc an toàn mới được giảm từ 2 ngày xuống chỉ còn vài phút.

![Blog 3](/images/3-BlogsPosted/blog-3.png)

[Link bài blog: Preventing data exfiltration in machine learning environments with Amazon SageMaker AI](https://www.facebook.com/groups/660548818043427/)

