---
title: "Week 10 Worklog"
date: 2026-06-30
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
* Use AWS Lambda Triggers to automatically synchronize user information from Cognito to RDS.
* Deploy the Frontend application to the Internet using the AWS Amplify Hosting service.
* Optimize network security using Cognito Authorizer on API Gateway and summarize the project.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - Create an **AWS Lambda (Post-Confirmation Trigger)** function using Node.js.<br>- Program Lambda to trigger an HTTP POST call event to the Backend EC2 to save User information into the Database. | 06/07/2026 | 06/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Configure Backend security: Attach **Cognito Authorizer** to API Gateway.<br>- Adjust RTK Query on the Frontend to include JWT tokens in the Headers of API requests. | 07/07/2026 | 07/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Configure continuous deployment (CI/CD) for the Next.js application on **AWS Amplify Hosting**.<br>- Connect Amplify with GitHub and configure Production environment variables. | 08/07/2026 | 08/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Comprehensively test the entire system from Frontend (Amplify) -> API Gateway -> Backend (EC2) -> Database (RDS).<br>- Optimize the user interface. | 09/07/2026 | 09/07/2026 | |
| Fri | - Finalize source code (Push code to Git). | 10/07/2026 | 10/07/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 10 Achievements:
* Fully automated the User data synchronization process between Cognito and PostgreSQL via Lambda Triggers.
* The Backend API is strictly protected by JWT Authorization through Amazon API Gateway and Cognito.
* Successfully deployed the Frontend application to a production environment with CI/CD using AWS Amplify Hosting.
* 100% completed the Capstone project, ready for final review with full documentation and high-quality Source Code.