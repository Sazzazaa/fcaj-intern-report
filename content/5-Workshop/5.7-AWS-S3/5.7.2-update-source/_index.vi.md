---
title : "Cập nhật URL ảnh trong mã nguồn"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

### Kết nối frontend với bucket S3

Trong dự án này, frontend không hard-code URL ảnh. Thay vào đó, URL được ghép tự động từ biến môi trường.

#### 1. Cập nhật biến môi trường

Trong local hoặc Amplify, khai báo:

```bash
NEXT_PUBLIC_S3_BUCKET_NAME=project-management-images-aws
NEXT_PUBLIC_AWS_REGION=us-east-2
```

#### 2. Kiểm tra helper tạo URL ảnh

File `client/src/lib/s3.ts` hiện đang xử lý như sau:

```ts
const S3_BUCKET_NAME =
  process.env.NEXT_PUBLIC_S3_BUCKET_NAME ?? "project-management-images-aws";
const S3_REGION = process.env.NEXT_PUBLIC_AWS_REGION ?? "us-east-2";

export const S3_BASE_URL = `https://${S3_BUCKET_NAME}.s3.${S3_REGION}.amazonaws.com`;
```

Khi component cần hiển thị ảnh, dự án sẽ gọi `getS3Url(key)` để sinh URL đầy đủ.

#### 3. Cho phép Next.js tải ảnh từ S3

Trong `client/next.config.mjs`, dự án đã thêm `remotePatterns` cho domain S3. Điều này cho phép component `Image` của Next.js render ảnh từ bucket AWS.

#### 4. Redeploy frontend

Sau khi cập nhật biến môi trường hoặc upload thêm object, hãy redeploy frontend trên Amplify để đảm bảo giao diện sử dụng đúng bucket mới.