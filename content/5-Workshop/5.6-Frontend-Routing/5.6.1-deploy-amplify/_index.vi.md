---
title : "Triển khai frontend lên Amplify"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

### Deploy ứng dụng Next.js bằng AWS Amplify

Frontend của dự án nằm trong thư mục `client/` và đã có sẵn file `amplify.yml` để Amplify build tự động.

#### 1. Kết nối repository

1. Mở **AWS Amplify**.
2. Chọn **Host web app** hoặc **Create app**.
3. Kết nối tài khoản GitHub.
4. Chọn repository `Sazzazaa/project-management-aws` và branch `main`.

#### 2. Kiểm tra file build

File `amplify.yml` của dự án đang dùng:

```yml
version: 1
applications:
  - appRoot: client
    frontend:
      phases:
        preBuild:
          commands:
            - npm ci
        build:
          commands:
            - npm run build
```

Điều này đảm bảo Amplify build đúng thư mục frontend.

#### 3. Khai báo biến môi trường

Tại Amplify, thêm các biến môi trường giống cấu hình local:

```bash
NEXT_PUBLIC_API_BASE_URL=https://30o8modynj.execute-api.us-east-2.amazonaws.com
NEXT_PUBLIC_S3_BUCKET_NAME=project-management-images-aws
NEXT_PUBLIC_AWS_REGION=us-east-2
NEXT_PUBLIC_COGNITO_USER_POOL_ID=us-east-2_7KWEBP8Ci
NEXT_PUBLIC_COGNITO_USER_POOL_CLIENT_ID=45qj7u3s4el2ggvjec6oqnfq6d
```

#### 4. Deploy và kiểm tra trạng thái

Sau khi build hoàn tất, Amplify sẽ cấp cho bạn một URL public.

![Amplify overview](/images/5-Workshop/5.6-Frontend-Routing/z8018624951197_552794d116a7747abbb6451cac611889.jpg)

#### 5. Xác minh giao diện đã hoạt động

Khi truy cập URL được deploy, trang Dashboard hiển thị thành công với biểu đồ và danh sách task.

![Dashboard home](/images/5-Workshop/5.6-Frontend-Routing/z8015064749679_f863e1da662ef87d8fe7e782dccbd205.jpg)

Ngoài trang Home, các route con như trang Priority cũng hoạt động bình thường.

![Priority page](/images/5-Workshop/5.6-Frontend-Routing/z8018816674221_4ba98393e460b77ee8591a7c240df558.jpg)