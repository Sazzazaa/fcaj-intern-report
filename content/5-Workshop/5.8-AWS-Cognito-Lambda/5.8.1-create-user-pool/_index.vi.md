---
title : "Khởi tạo Cognito User Pool"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

### Tạo User Pool cho ứng dụng

#### 1. Tạo User Pool mới

Mở **Amazon Cognito** và tạo một **User Pool** mới cho ứng dụng. Sau khi tạo xong, trang Overview sẽ hiển thị:

* **User Pool ID**
* **OpenID Connect configuration URL**
* khu vực đang sử dụng

![User pool overview](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015062966503_5df85de2a59a22275ab7faf01bb041b2.jpg)

#### 2. Tạo App Client cho frontend

Vì frontend là ứng dụng SPA, ta tạo một **App client** riêng và ghi lại:

* **User Pool ID**: ví dụ `us-east-2_7KWEBP8Ci`
* **Client ID**: ví dụ `45qj7u3s4el2ggvjec6oqnfq6d`

![App client](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015063019491_486c54ff7f6487dfb12f9bd1e4d9a1fc.jpg)

#### 3. Cập nhật biến môi trường cho frontend

Trong `client/.env.local` hoặc Amplify Environment variables:

```bash
NEXT_PUBLIC_COGNITO_USER_POOL_ID=us-east-2_7KWEBP8Ci
NEXT_PUBLIC_COGNITO_USER_POOL_CLIENT_ID=45qj7u3s4el2ggvjec6oqnfq6d
```

File `client/src/app/authProvider.tsx` sẽ dùng hai biến này để cấu hình Amplify Authenticator.

#### 4. Kiểm tra luồng đăng ký

Khi người dùng đăng ký tài khoản mới, Cognito sẽ gửi email xác minh.

![Email verification](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015064830628_12dc6c0e7aaef99d2bfc59ad2fe1ad3a.jpg)

Sau khi nhập mã xác minh, người dùng sẽ xuất hiện trong danh sách **Users** của User Pool.

![Cognito users list](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015068340177_570aaa9ef9b914783f16a38cb7562492.jpg)