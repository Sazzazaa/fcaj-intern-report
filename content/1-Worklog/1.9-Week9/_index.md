---
title: "Week 9 Worklog"
date: 2026-06-30
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
* Configure image storage on Amazon S3 with Bucket Policies.
* Integrate identity management (IAM) and user authentication using Amazon Cognito.
* Integrate login/registration interfaces into the Next.js application using AWS Amplify UI.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - Initialize **Amazon S3 Bucket** to store static assets (Images).<br>- Disable Block Public Access and configure S3 Bucket Policy to allow `s3:GetObject`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Initialize an **Amazon Cognito User Pool**.<br>- Configure login formats, password policies, and create an App Client. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Install `aws-amplify` and `@aws-amplify/ui-react` packages on the Next.js Frontend.<br>- Build an Auth Provider with AWS's built-in **Authenticator UI**. | 01/07/2026 | 01/07/2026 | |
| Thu | - Configure custom form fields in the Authenticator to allow user registration including: Email, Username, Password. | 02/07/2026 | 02/07/2026 | |
| Fri | - Test the flow of sending verification codes via email through Cognito.<br>- Extract the `NEXT_PUBLIC_COGNITO_USER_POOL_ID` environment variable. | 03/07/2026 | 03/07/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 9 Achievements:
* All static image assets of the system have been uploaded to Amazon S3 and links have been successfully mapped to the Frontend interface.
* Completely configured the Amazon Cognito User Pool to manage user identities.
* Seamlessly integrated a professional Registration / Login interface into Next.js using Amplify UI without having to custom-code the authentication form.