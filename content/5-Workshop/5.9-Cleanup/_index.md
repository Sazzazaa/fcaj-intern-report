---
title : "Clean up"
date : 2026-07-07
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Clean up resources

After completing the Project Management deployment workshop, it is important to remove the AWS resources to avoid unnecessary charges. The deletion process should be done in a controlled order, starting from the application layer and moving inward to the infrastructure layer, so that service dependencies do not cause avoidable errors.

#### Recommended order

1. **Remove the frontend deployment on AWS Amplify**

   First, open **AWS Amplify** and review the deployed application. If the demo environment is no longer needed, delete the active branch or remove the entire hosting application.

2. **Delete the Amazon Cognito configuration**

   Next, go to **Amazon Cognito** and review the following resources:

   - The User Pool created for this project
   - The related App Client
   - Any test users that are no longer needed

3. **Delete the API in Amazon API Gateway**

   After that, open **API Gateway** and remove:

   - The HTTP API or REST API created for the project
   - The deployed stage
   - Any authorizer created specifically for the lab

4. **Delete the Lambda trigger**

   If a Lambda function was created for post-confirmation or another Cognito trigger, make sure to:

   - Detach the trigger from the User Pool
   - Delete the Lambda function if it is no longer required

5. **Stop and terminate the EC2 backend**

   In **EC2 Console**, perform the following steps:

   - Stop the instance for a final check
   - Terminate the backend instance when you are done
   - Release any Elastic IP that was attached
   - Delete the key pair on AWS if you do not need it anymore

6. **Delete the Amazon RDS database**

   For **Amazon RDS**, decide first whether the database needs to be preserved before deletion:

   - Keep a snapshot if you may need the data later
   - Skip the snapshot if this was only a lab environment

   Once the appropriate option has been chosen, delete the database instance.

7. **Delete the S3 bucket used for images**

   In **Amazon S3**, clean up the bucket in this order:

   - Delete all objects inside the bucket
   - Confirm that the bucket is empty
   - Delete the bucket used for project images or static assets

8. **Delete security groups and supporting network resources**

   After EC2 and RDS have been removed, continue with the related network resources:

   - The EC2 security group
   - The RDS security group
   - The DB subnet group if it was created specifically for this workshop

9. **Delete the subnets, route tables, internet gateway, and VPC**

   If the VPC was created only for this workshop, remove it in the following order:

   - Subnets
   - Custom route tables
   - Internet gateway (detach first, then delete)
   - VPC

#### Final note

Before removing everything completely, make sure the following items have already been saved:

- The final source code
- Screenshots used in the report
- Any important configuration values or demo links you may need later