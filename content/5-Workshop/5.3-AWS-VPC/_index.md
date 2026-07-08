---
title : "Virtual Network Setup (AWS VPC)"
date : 2026-07-04 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

### Isolating Network Resources with VPC

In this section, we will manually provision a **Virtual Private Cloud (VPC)** from scratch to provide a secure network environment for the entire project. Instead of using the Default VPC (AWS's default VPC), we will design a tiered network architecture including: a **Public Subnet** for the Backend server (EC2) to enable communication with the Internet via an **Internet Gateway**, and **Private Subnets** dedicated to the database (RDS) to protect the system's business data from unauthorized external access.

![VPC Architecture](/images/5-Workshop/5.3/vpc-architecture.png)

#### Content

- [Create VPC & Subnets](5.3.1-create-vpc-subnets/)
- [Configure Internet Gateway & Route Tables](5.3.2-igw-route-tables/)