---
title : "Bảo mật API Gateway bằng Cognito Authorizer"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.8.3. </b> "
---

### Bắt buộc người dùng đăng nhập trước khi gọi API

Frontend của dự án đã tự động đính kèm `Bearer token` vào request thông qua `fetchAuthSession()` trong file `client/src/state/api.ts`. Vì vậy ta có thể dùng **Cognito JWT Authorizer** ở API Gateway để bảo vệ các route backend.

#### 1. Tạo JWT Authorizer

Tại API Gateway HTTP API:

1. Mở phần **Authorization**.
2. Tạo một **JWT authorizer** mới.
3. Điền:

* **Issuer**: URL issuer của Cognito User Pool, ví dụ:

```text
https://cognito-idp.us-east-2.amazonaws.com/us-east-2_7KWEBP8Ci
```

* **Audience**: Client ID của App Client, ví dụ:

```text
45qj7u3s4el2ggvjec6oqnfq6d
```

#### 2. Gắn authorizer cho route

Bạn có thể gắn authorizer cho:

* route `$default`, hoặc
* các route cần bảo vệ như `/projects`, `/tasks`, `/users`, `/teams`, `/search`.

Sau khi thay đổi, hãy deploy lại stage `$default`.

#### 3. Vì sao frontend dùng được ngay

Trong file `client/src/state/api.ts`, trước mỗi request, frontend đã:

1. lấy session Cognito hiện tại,
2. lấy `accessToken`,
3. gắn header:

```text
Authorization: Bearer <token>
```

Do đó sau khi người dùng đăng nhập thành công, các request tới API Gateway sẽ tự mang theo token hợp lệ.

#### 4. Kết quả mong đợi

* Người dùng đã đăng nhập truy cập ứng dụng bình thường.
* Request không có token hoặc token không hợp lệ sẽ bị API Gateway từ chối.
* Các trang như Home, Priority, Users, Teams chỉ hoạt động đầy đủ khi session Cognito còn hiệu lực.