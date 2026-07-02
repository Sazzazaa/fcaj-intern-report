---
title: "Week 8 Worklog"
date: 2026-06-28
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:
* Deploy the Backend application server to Amazon EC2.
* Optimize server operations using PM2 Process Manager.
* Build an HTTPS intermediary gateway via Amazon API Gateway to handle Mixed Content.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - Initialize **Amazon EC2 (Amazon Linux 2023)** in the Public Subnet.<br>- Configure EC2 Security Group: Open Port 22 (SSH) and Port 80 (HTTP). | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - SSH into EC2, install the runtime environment: Node.js, NVM, Git.<br>- Git Clone the server source code, install **PM2** to automatically restart the Backend. | 23/06/2026 | 23/06/2026 | |
| Wed | - Configure environment variables on EC2 to connect with Amazon RDS.<br>- Run `npx prisma generate` and synchronize the database on the Cloud. | 24/06/2026 | 24/06/2026 | |
| Thu | - Initialize **Amazon API Gateway (REST API)**, create a resource as `/{proxy+}`.<br>- Set up **HTTP Proxy Integration** pointing to the EC2 server IP. Configure CORS. | 25/06/2026 | 25/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - Deploy API Gateway to the `prod` stage to get a secure HTTPS certificate URL.<br>- Replace the Local API environment variable on the Frontend with the API Gateway URL. | 26/06/2026 | 26/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 8 Achievements:
* The Node.js Backend server was successfully deployed and is running stably on Amazon EC2 using PM2.
* The RDS database system was successfully connected from the EC2 environment.
* Completely resolved the Mixed Content (HTTP/HTTPS) error by using Amazon API Gateway as a Proxy wrapping the EC2 instance.