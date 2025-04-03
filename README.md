# Running-webapp-on-AWS-Amplify
Call n' Go Subscription
Service
Automating Subscription Processes with AWS Amplify, API
Gateway, DynamoDB, Lambda, CloudFormation, and Git


**1. Introduction**

● Overview:
This project is all about simplifying the subscription process for Call n’Go web application. By leveraging AWS services, I built a system that is not only scalable and secure but also easy to manage. My aim was to create a solution that delivers a seamless subscription experience while automating critical backend processes.

● AWS Services used:
 ○ AWS Amplify
 ○ AWS API Gateway
 ○ AWS DynamoDB
 ○ AWS Lambda
 ○ Amazon CloudFormation
 ○ Git
 
**2. Project Architecture and Solution Design**

● The big picture:
Imagine a system where a user’s subscription request travels smoothly from a simple web interface to a robust backend process. AWS Amplify handles the front end, API Gateway takes care of the communication, Lambda processes the request, and DynamoDB stores the details—all brought together seamlessly using CloudFormation.

● Architecture Diagram:
○ AWS Amplify: Hosts the user interface
○ API Gateway: Exposes and manages API endpoints
○ AWS Lambda: Runs the business logic

**3. Setting Up the Infrastructure with AWS CloudFormation**

● Why CloudFormation?
To make sure everything runs smoothly and can be easily recreated, I used AWS CloudFormation to define the whole infrastructure as code. This meant that every resource—from DynamoDB tables to API Gateway configurations—was set up consistently and reliably. 
 ○ Amazon DynamoDB: Stores subscriber’s data
 ○ CloudFormation: Automates the setup of all these components


● Key Components in the Template:
 ○ The DynamoDB table for saving subscribers’s data.
 ○ IAM roles and policies for secure Lambda execution.
 ○ API Gateway setup for our REST API endpoints.

● Code Walkthrough:
DynamoDB Schema Flexibility: DynamoDB only requires you to define key attributes (e-mail in this case) in the CloudFormation template. Non-key attributes like "name" and "surname" can be added dynamically when items are inserted, without being pre-defined in the table schema.

**4. AWS Lambda Function**

● Function purpose:
The Lambda function is the engine behind the subscription process. It validates user input, ensures that emails are unique, and safely stores subscriber details in DynamoDB while giving realtime information to the user in the front-end.

● Code Walkthrough:
 ○ Input validation and error handling
 ○ Prevention of duplicate subscriptions using a conditional check

**5. Connecting the Dots: API Gateway**

Integration

● Role of API Gateway:
API Gateway acts like a traffic controller. It ensures that user requests reach the Lambda function securely and efficiently. It also handles CORS, making sure our front end can communicate with the backend without any hiccups.

● How It All Works Together:
 ○ User submits a subscription form (Name, Surname and e-mail)
 ○ API Gateway forwards the request to the Lambda function
 ○ Lambda processes the request, validates the data imputed by the user against the definition logic and writes to DynamoDB

**6. DynamoDB for Subscription Data Management**

DynamoDB is our fast, scalable NoSQL database that securely stores every user’s subscription details. It’s a key component in our system, enabling real-time data access with minimal latency.

● Table design:
The Subscribers table uses the email as the primary key to ensure each subscription is unique. Additional fields like name, surname, and timestamps help track when a subscription is created or updated. 

● Conditional writes:
Our Lambda function uses conditional expressions when inserting data. This means a new subscription is added only if the email isn’t already registered, protecting against duplicates. 

● Real-Time access:
Data in DynamoDB is available instantly, allowing for fast retrieval and efficient management of subscriptions.

**7. Continuous Integration and Deployment with Git**

● Streamlined DevOps:
Using Git for version control and CI/CD allowed me to automate testing and deployment, making sure that every change was deployed reliably. This process not only saves time but also reduces the risk of errors. AWS Amplify supports Git integration, including Bitbucket, AWS CodeCommit, and GitLab, streamlining automated testing and deployment.

● How It Works:
 ○ Code changes pushed to Git trigger automated builds and deployments
 ○ The whole infrastructure updates automatically via CloudFormation

**8. Conclusion and Final Thoughts**

● Wrapping Up:

 ○ This project not only improved the subscription process but also demonstrated the power of a well-integrated, serverless architecture. It’s been a rewarding experience that sharpened my skills in cloud automation and DevOps.
 
 ○ Infrastructure as a Code (IaC). Using AWS CloudFormation improved by at least 80% the testing and deployment of new features or even error correction rate. This increased response time and agility.
 
 ○ Serverless. All of this was powered by using serverless architecture provided by AWS. No need for server management, patching or monitoring.
