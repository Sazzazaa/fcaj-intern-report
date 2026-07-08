---
title : "Write the AWS Lambda Trigger"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.8.2. </b> "
---

### Synchronize Cognito users into the application database

In this project, the backend `User` table contains a unique `cognitoId` field. For that reason, once a user is confirmed in Cognito, the application should automatically create a matching database record in PostgreSQL.

#### 1. Why a Lambda Trigger is needed

The backend already provides this route:

```text
POST /users
```

and the `postUser` controller accepts these main fields:

* `username`
* `cognitoId`
* `profilePictureUrl`
* `teamId`

The Lambda Trigger lets us automate this flow immediately after Cognito account confirmation instead of creating users manually.

#### 2. Use the correct Cognito trigger

Attach the Lambda function to the:

* **Post Confirmation** trigger

This is the best moment because the user has completed email verification and Cognito has already generated the `sub` identifier.

#### 3. Suggested processing flow

The Lambda function can read data from the Cognito event:

* `event.userName`
* `event.request.userAttributes.sub`
* `event.request.userAttributes.email`

Then it can:

1. build a new user payload
2. call the backend `/users` API or run equivalent database logic
3. return the `event`

#### 4. Practical notes

* If API Gateway is protected by an authorizer, keep a suitable route available for Lambda or configure a dedicated service-to-service access method.
* Use CloudWatch logs so it is easy to debug database user creation failures.
* Add a duplicate check on `cognitoId` to avoid creating the same user twice.