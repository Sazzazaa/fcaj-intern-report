---
title : "Tạo S3 Bucket và phân quyền"
date : 2026-07-06
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

### Tạo bucket lưu ảnh cho ứng dụng

#### 1. Tạo bucket mới

1. Mở **Amazon S3**.
2. Chọn **Create bucket**.
3. Đặt tên bucket, ví dụ: `project-management-images-aws`.
4. Chọn đúng region đang dùng cho dự án, ở đây là `us-east-2`.

Sau khi tạo thành công, bucket sẽ xuất hiện trong danh sách.

![S3 bucket created](/images/5-Workshop/5.7-AWS-S3/z8014903805881_ad0eece18580fb6b88234fd493898503.jpg)

#### 2. Tải object lên bucket

Upload các tệp cần dùng cho giao diện như:

* `logo.png`
* avatar người dùng
* ảnh đính kèm mẫu

Khi mở trang chi tiết object, AWS sẽ hiển thị URL tương ứng.

![S3 object properties](/images/5-Workshop/5.7-AWS-S3/z8014913860501_46e832754f7daa970e9eb8d14be759d3.jpg)

#### 3. Phân quyền đọc ảnh

Do frontend sẽ render ảnh trực tiếp bằng object URL, bạn cần cho phép các object được đọc công khai theo cách phù hợp với cấu hình bucket của mình, ví dụ:

* bucket policy chỉ cho phép `s3:GetObject`, hoặc
* cấu hình public read cho các object cần hiển thị.

Mục tiêu cuối cùng là URL kiểu:

```text
https://project-management-images-aws.s3.us-east-2.amazonaws.com/<object-key>
```

có thể được frontend truy cập thành công.