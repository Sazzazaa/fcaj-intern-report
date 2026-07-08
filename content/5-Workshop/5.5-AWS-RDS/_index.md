---
title : "Deploy the Database (AWS RDS)"
date : 2026-07-04
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

In this section, we deploy **Amazon RDS for PostgreSQL** to store the application data. The database is placed in private subnets so it is not exposed directly to the public internet, and only the backend EC2 instance is allowed to connect through its Security Group.

The goals of this section are:

* Create a PostgreSQL database on RDS
* Configure the Security Group so EC2 can connect on port `5432`
* Run `Prisma generate`, `migrate`, and `seed` from the EC2 server

#### Contents

1. [Create RDS PostgreSQL](5.5.1-create-rds/)
2. [Configure the RDS Security Group](5.5.2-config-sg/)
3. [Migrate and Seed the Database](5.5.3-migrate-seed/)