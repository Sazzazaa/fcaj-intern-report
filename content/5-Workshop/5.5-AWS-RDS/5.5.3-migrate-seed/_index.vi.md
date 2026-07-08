---
title : "Migrate và seed dữ liệu"
date : 2026-07-06
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

### Khởi tạo schema và dữ liệu mẫu từ EC2

Sau khi RDS đã **Available** và Security Group đã mở đúng rule, quay lại máy EC2 để hoàn tất backend.

#### 1. Cập nhật file `.env`

Ví dụ:

```bash
PORT=8000
DATABASE_URL="postgresql://postgres:<your-password>@project-management-db.<your-endpoint>.us-east-2.rds.amazonaws.com:5432/project_management_aws?schema=public"
```

#### 2. Generate Prisma Client

Trong quá trình triển khai thực tế, lệnh `npm prisma generate` có thể không chạy được. Cách ổn định là dùng `npx prisma generate`:

```bash
cd ~/project-management-aws/server
npx prisma generate
```

#### 3. Chạy migrate và seed dữ liệu

```bash
npx prisma migrate deploy
npm run seed
```

Ảnh dưới đây cho thấy quá trình generate Prisma Client, migrate database và seed dữ liệu mẫu thành công.

![Prisma migrate seed](/images/5-Workshop/5.4-AWS-EC2/z8014660603531_d2b6b06a6c4d6ae71694dc71875c548e.jpg)

#### 4. Cài PM2 và chỉnh lệnh start

Do output build thực tế của project nằm tại `dist/src/index.js`, ta cập nhật script start trước khi chạy PM2:

```bash
npm pkg set scripts.start="npm run build && node dist/src/index.js"
npm install -g pm2
pm2 start npm --name project-management-api -- start
pm2 save
pm2 status
```

![PM2 save status](/images/5-Workshop/5.4-AWS-EC2/z8014660603511_f1b5c8eff652021b8de8c74d269871b6.jpg)

#### 5. Kiểm tra backend bằng localhost

Sau khi PM2 chạy ổn định, có thể kiểm tra nhanh API ngay trên EC2:

```bash
curl http://localhost:8000/projects
```

Nếu trả về danh sách project JSON, backend đã kết nối thành công với RDS.

![Curl localhost projects](/images/5-Workshop/5.4-AWS-EC2/z8014714331396_4de9416dc5804df52ec5d66b097a4b8b.jpg)