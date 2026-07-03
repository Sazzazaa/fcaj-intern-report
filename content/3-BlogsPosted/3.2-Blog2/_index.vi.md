---
title: "Blog 2"
date: 2026-07-03
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# TRÍCH XUẤT VĂN BẢN PDF TƯƠNG TÁC TỪ AMAZON S3: GIẢI PHÁP REAL-TIME VỚI MCP

Bài viết giới thiệu giải pháp xây dựng một máy chủ (MCP Server) để trích xuất văn bản PDF thuần chữ từ Amazon S3 theo thời gian thực. Thay vì chờ đợi các batch job chậm chạp, cách tiếp cận này giúp AI Assistant có thể đọc, tìm kiếm điều khoản và trả lời câu hỏi từ tài liệu ngay lập tức.

Các điểm chính cần nắm:

* **Tối ưu chi phí cực tốt:** Chi phí chỉ rơi vào khoảng $2.50/tháng cho 10.000 trang (rẻ hơn nhiều so với mức ~$23-$28/tháng của các dịch vụ chuyên dụng như Amazon Textract).
* **Kiến trúc 4 thành phần tinh gọn:** Bao gồm AI Client, giao thức Model Context Protocol (MCP), Custom MCP Server (dùng thư viện boto3, PyPDF2) và hệ thống lưu trữ/bảo mật Amazon S3.
* **Cơ chế hoạt động thông minh:** AI tự động gọi công cụ thông qua giao thức MCP để trích xuất chính xác đoạn văn bản cần thiết từ S3 bằng Object Key, thay vì tải toàn bộ tài liệu nặng nề về máy.
* **Triển khai cực kỳ nhanh chóng:** Có thể dựng hệ thống ngay trên máy tính bằng Python thông qua môi trường ảo và 3 gói thư viện cơ bản.
* **Ứng dụng thực tế cao:** Đây là giải pháp hoàn hảo cho môi trường Development hoặc PoC khi cần xây dựng trợ lý ảo nội bộ truy vấn dữ liệu on-demand tức thì.

![Blog 2](/images/3-BlogsPosted/blog-2.png)



[Link bài blog: Build interactive PDF text extraction from Amazon S3](https://www.facebook.com/groups/660548818043427/)

