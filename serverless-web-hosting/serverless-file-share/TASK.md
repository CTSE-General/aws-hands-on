### Advanced Task: File Transfer with Web Frontend

###### Scenario: Global Collaborative Project

In this scenario, you are managing a global collaborative project involving multiple teams and partners across different continents. Effective and secure file sharing is crucial for the project's success. Your task is to build a file transfer system with a web frontend that facilitates the seamless exchange of large project files, documents, and data. The system should support encryption, access control, version history, and efficient transfer mechanisms. As the project progresses, you will need to provide team members and partners with a user-friendly web interface to upload, share, and collaborate on project assets securely. This system will enhance productivity, streamline communications, and ensure data integrity in a complex, international project environment.

###### General Info:
For this task both the frontend and the database schmema with sample data will be provided. You only need to write the architecture and the code for the lambda functions.

Further information about the task and the code can be found in the following repository: [apigw-lambda-url-shortener](https://github.com/CTSE-General/aws-hands-on/tree/main/serverless-web-hosting/serverless-file-share)

You can clone it with the following link from GitHub (HTTPS): https://github.com/CTSE-General/aws-hands-on.git

##### Subtask 1: Website distribution
1. Create an S3 Bucket that will host the frontend
2. Create a CloudFront Distribution and configure it to distribute the frontend from the S3 Bucket
3. Test functionality

##### Subtask 2: Create DynamoDB and CRUD Lambdas
1. Create the DynamoDB with the given schema
2. Create four Lambda functions (for more information check the architecture)
3. Test the Lambda functions

##### Subtask 3: Create Backend connection
1. Create an API-Gateway and a cookie authroizer Lambda for it
2. Integrate the Lambdas into it
3. Create S3 Buclket to hold the shared files
4. Test both endpoints

##### Subtask 4: Setup Authentication + Protected CloudFront Distribution
1. Create protected CloudFront Distribution
2. Create Cognito User Pool
3. Write Authentication Lambda@Edge and connect it to SSM
4. Test functionality