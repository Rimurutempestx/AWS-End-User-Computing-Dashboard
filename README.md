# AWS-End-User-Computing-Dashboard
Built a dashboard that enables your help desk staff to view details for Amazon AppStream 2.0 fleets and Amazon WorkSpaces directories and instances.

## Overview
A quick summary of a dashboard that enables your help desk staff to view details for Amazon AppStream 2.0 fleets and Amazon WorkSpaces directories and instances. For both AppStream 2.0 and WorkSpaces, your staff can also use the dashboard to perform basic administrative tasks. For AppStream 2.0, they can monitor autoscaling activities and manage users’ streaming sessions. For WorkSpaces, they can send the registration code email to a user, or stop, start, restart, and restore a user’s WorkSpace. With this workflow, your teams don’t require access to the AppStream 2.0 console or WorkSpaces console, or cloud-based computing experience.





![image](https://user-images.githubusercontent.com/106786020/213949555-ebc030a6-5585-40f7-9814-0e2bb87504d6.jpeg)



## Static website and Cloudfront configuration
Started off by creating a S3 bucket to store my objects, then made sure that my bucket name was a globally unique DNS-compliant name. Also verified that the region is supported for the project. Configured the Origin Domain Name to my S3 bucket, proceeded to leave the Orgin Path empty and kept the default value for the origin ID. For the OAI i chose to just burn a little bit of time and create a new identity, then made sure to update my bucket policys. I also decided to leave the values for Origin Connection Attempts and Origin Connection Timeout as default and the Origin Custom Headers empty for now. Then for Default Cache Behavior Settings, for Viewer Protocol Policy, chose Redirect HTTP to HTTPS. Finally for the Default Root Object for the distribution settings i entered index.html and created the Distribution.



## The Authentication Workflow
Began by creating an Amazon Cognito user pool and making a note of the pool id. Then strated creating the app client that i would be using for the project, cleared the generate client checkbox and created the app client. I played around with the password strength for a while because i didn't know if i wanted to increase the resiliency of it to protect the users or simplify it to save users time, In the end i just went with the Resilient option. I also chose to allow users to sign themselves up rather than administrators only that would've been a little extra. After that i chose a domain name and saved the changes after making a note of the complete domain name.

For the second part of the workflow i started by enabling SSO and creating an AWS organization to manage the SSO access and user permissions across all the accounts. Then started by adding a user and the application to SSO. Created a new user and configured all the user details (ex: Username, password, email). I didn't created any groups though because i didn't exactly feel their was any reason. I then made sure the invite links went through to the specified emails and the invites were accepted. After all the invite links were accepted i then added a custom SAML 2.0 application and made a note of the URL and configured all the settings and destinations for the Application ACS URL and the Application SAML audience. For Maps to this string value or user attribute in AWS SSO I configured the value to ${user:email} and configured the format for attribute mapping and saved.

At last for the final part I created a SAML identity provider in the user pool. Started by providing the metadata document endpoint URL and filled in everything for the provider name and identifiers. Then created the idp, added the SAML attribute and for user pool attribute chose email. Set up the Callback URL(s) and saved.



## Building a Serverless Backend
To grant permissions to handle backend requests for the End User Computing (EUC) dashboard I created a custom IAM policy that grants all the needed permissions (see IAM policy permissions and JSON policy in the files section). Next I began creating the IAM service role so that the Lambda functions can call the AWS services, then created the Lambda function itself.



## Deploying RESTful API
This part was pretty straightforward I simple just opened the API Gateway console and checked a few boxes and entered the API name, Description, and Endpoint type and created the API. Next it was time to configure the API Gateway for Lambda integration I started by creating my new authorizer for my user pool, then created my resource and verified my region code and enabled API Gateway CORS. Then got around to deploying the API.



## Customize the FROM address used for email communications with users
Amazon SES is an email service that enables you to send and receive email using your own email addresses and domains.
