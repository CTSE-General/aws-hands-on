### Intermediate Task: URL Shortener with Web Frontend

###### Scenario: Social Media Marketing Campaign

Imagine you are part of a marketing team for a rapidly growing e-commerce company. You have a new product launch and a compelling social media marketing campaign. However, the URLs for your campaign are long and unattractive. To enhance the user experience and track the campaign's success, your task is to create a URL shortening service with a user-friendly web frontend. This will help you generate short, branded URLs for your campaign materials, such as product pages and promotional content. Users should be able to create shortened links and view basic analytics, like click-through rates, to measure the impact of your marketing efforts.

###### General Info:

For this task both the frontend and the database schmema with sample data will be provided. You only need to write the architecture and the code for the lambda functions.

Further information about the task and the code can be found in the following repository: [apigw-lambda-url-shortener](https://github.com/CTSE-General/aws-hands-on/tree/main/serverless-web-hosting/apigw-lambda-url-shortener)

You can clone it with the following link from GitHub (HTTPS): https://github.com/CTSE-General/aws-hands-on.git

##### Subtask 1: Website distribution

1. Create an S3 Bucket that will host the frontend
2. Create a CloudFront Distribution and configure it to distribute the frontend from the S3 Bucket
3. Test functionality

##### Subtask 2: Create DynamoDB and CRUD Lambdas

1. Create the DynamoDB with the given schema
2. Create two Lambda functions (GetUrl and PostUrl)
3. Test the Lambda functions

##### Subtask 3: Create Backend connection

1. Create an API-Gateway
2. Integrate the Lambdas into it
3. Test both endpoints

##### Subtask 4: Connect frontend to backend

1. Add API-GateWay URL into frontend
2. Test functionality
