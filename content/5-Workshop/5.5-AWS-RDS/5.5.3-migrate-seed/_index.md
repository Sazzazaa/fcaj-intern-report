---
title : "Migrate and Seed the Database"
date : 2026-07-06
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

### Initialize the schema and seed data from EC2

After the RDS instance becomes **Available** and the Security Group rule is in place, go back to the EC2 server to finish the backend setup.

#### 1. Update the `.env` file

Example:

```bash
PORT=8000
DATABASE_URL="postgresql://postgres:<your-password>@project-management-db.<your-endpoint>.us-east-2.rds.amazonaws.com:5432/project_management_aws?schema=public"
```

#### 2. Generate the Prisma Client

During the actual deployment, `npm prisma generate` may fail. The stable command is:

```bash
cd ~/project-management-aws/server
npx prisma generate
```

#### 3. Run migrations and seed data

```bash
npx prisma migrate deploy
npm run seed
```

The screenshot below shows the Prisma Client generation, database migration, and data seeding process completed successfully.

![Prisma migrate seed](/images/5-Workshop/5.4-AWS-EC2/z8014660603531_d2b6b06a6c4d6ae71694dc71875c548e.jpg)

#### 4. Install PM2 and adjust the start command

Because the actual build output of this project is located at `dist/src/index.js`, update the `start` script before running PM2:

```bash
npm pkg set scripts.start="npm run build && node dist/src/index.js"
npm install -g pm2
pm2 start npm --name project-management-api -- start
pm2 save
pm2 status
```

![PM2 save status](/images/5-Workshop/5.4-AWS-EC2/z8014660603511_f1b5c8eff652021b8de8c74d269871b6.jpg)

#### 5. Verify the backend locally on EC2

Run:

```bash
curl http://localhost:8000/projects
```

If the command returns the project list as JSON, the backend is connected to RDS successfully.

![Curl localhost projects](/images/5-Workshop/5.4-AWS-EC2/z8014714331396_4de9416dc5804df52ec5d66b097a4b8b.jpg)