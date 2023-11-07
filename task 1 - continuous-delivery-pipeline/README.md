# 🌩️ continuous-delivery-pipeline in AWS Cloud

In **continuous-delivery-pipeline** project, we will be creating a continuous delivery pipeline in AWS. Pipelines are a cruial part of almost every project.

# Tasks

The continuous-delivery-pipelin task is going to be split up into *4 subtasks*. **Subtask 1:** You will begin by altering the *app.js* file and pushing the changes to your repository. **Subtask 2:** Next step is the deployment of the application into the AWS Elastic Beanstalk Service. Next you will create a build project in AWS Codebuild. **Subtask 3:** Following this you will create the actual pipeline which will be building and deploying your application automatically using AWS CodePipeline. **Subtask 4:** Finally you will finalize the Pipeline by adding a manual approval step (which are important to have) and testing the pipeline.

# Prerequisites

- Create GitHub Account
- Fork [example application](https://github.com/aws-samples/aws-elastic-beanstalk-express-js-sample)
- Clone the forked repo locally

## How to fork the example repo

- Login into your GitHub Account
- Choose the white Fork button on the top right corner of the screen. Next, you will see a small window asking you where you would like to fork the repo.
- Verify it is showing your account and choose Create a fork. After a few seconds, your browser will display a copy of the repo in your account under Repositories.

# 🚀 Setup a Web-App using ElasticBeanstalk

## ✅ Subtask 1 - dockerized web application

![](./docs/img/docker-url-shortener.png)

> In this subtask, your goal is setup an ElasticBeanstalk Application.

- Edit App.js to your liking

- Deploy App into ElasticBeanstalk

At the end, you should be able to access your web application via the given Domain in your ElasticBeanstalk environment.

### 🔥 Adjust App.js

Edit the App.js to your liking or simply change the "Hello World" text to some custom text.

Next push your changes into the repository using:
```
git add app.js
git commit -m "change message"
```

Now it is time to configure an ElasticBeanstalk App:
- Navigate to ElasticBeanstalk and create an Application
- Choose **Web server environment** under the Configure environment heading
- For the application name use **"<YOUR_NAME>_aws-hands-on"**
- Select Node.js as your platform
- Confirm that the radio button next to Sample application under the Application code heading is selected
- Confirm that the radio button next to Single instance (free tier eligible) under the Presets heading is selected
- Select Next
- On the Configure service access screen, choose Use an existing service role for Service Role
- As your Service Role choose 'aws-elasticbeanstalk-service-role'
- As your EC2 instance profile choose 'aws-elasticbeanstalk-ec2-role' ( if not available choose the default one or create a new one)
- Choose Skip to review
- Choose Submit

You have successfully created an App in ElasticBeanstalk! You can test your App by clicking into your environment and opening the 'Domain'

# 🚀 Laying the foundation for the Pipeline

## ✅ Subtask 2: Create Build Project

### ✨ Architecture

![](./docs/img/apigw-url-shortener.png)

> In this task you will create a CodeBuild Project which will be used to build the source code that is located inside of your GitHub Respository. AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy.

- Create a build project with AWS CodeBuild

- Set up GitHub as the source provider for a build project

- Run a build on AWS CodeBuild

First step is to setup CodeBuild. For this navigate to the AWS CodeBuild Service. For the setup perform the following steps:

- For the Project Name choose <YOUR_NAME>-aws-hands-on-cbp
- Select GitHub as the Source Provider
- Connect to your GitHub Account and choose the repository you have setup earlier
- Confirm that Managed Image is selected
- Select Amazon Linux 2 from the Operating system dropdown menu
- Select Standard from the Runtime(s) dropdown menu
- Select aws/codebuild/amazonlinux2-x86_64-standard:3.0 from the Image dropdown menu
- Confirm that Always use the latest image for this runtime version is selected for Image version
- Confirm that Linux is selected for Environment type
- Confirm that New service role is selected

Next you will be creating a Buildspec file for your buildspec project. For this perform the following steps:

- Select Insert build commands
- Choose switch to editor
- Write the buildspec file

Write the buildpsec file with the following config:
- Version 0.2
- add only a build phase
- add npm installation command to the build phase
- add artifacts and set the *'files'* attribute to: - '**/*'

Now you can procees by clicking 'Create build project'. In your dashboard you can now test your Codebuild Project by selecting 'Start build'.

## ✅ Subtask 3: Creating the Continuous Delivery Pipeline

### ✨ Architecture

![](./docs/img/ecs-url-shortener.png)

> The main element of this task is the Continuous Delivery Pipeline. You are going to set up a continuous delivery pipeline with source, build, and deploy stages. The pipeline will detect changes in the code stored in your GitHub repository, build the source code using AWS CodeBuild, and then deploy your application to AWS Elastic Beanstalk.

- Creating an AWS CodePipeline

- Adding a source stage

- Adding a build stage

- Adding a deploy stage

To create your first CodePipelin navigate to the AWS CodePipeline Service and create a new pipeline with the following configuration:
- Pipeline Name: <YOUR_NAME>-aws-hands-on-pipeline
- Select 'New service role'
- Choose next

Next up is the creation of source first stage:
- choose **GitHub Version 1** as the Source provider
- connect your GitHub and choose your repository and select the main branch
- Confirm that GitHub Webhooks is selected
- Choose next

The second stage we are going to add is the build stage:
- Choose **AWS CodeBuild** as the Build Provider
- Select the Europe (Ireland) Region (eu-west-1)
- select build-<YOUR_NAME> as the project name
- choose next

Last but not least it is time to add the deploy stage:
- choose **AWS Elastic Beanstalk** as the Deploy Provider
- Select the Europe (Ireland) Region (eu-west-1)
- Select your previously created environment
- Choose next
- Choose Create pipeline

Now that you pipeline is setup you should be able to execute your pipeline and see the first deployment running through.

## ✅ Subtask 4: Finalizing + Testing

### ✨ Architecture

![](./docs/img/ecs-url-shortener.png)

> Now we will finalize and test the newly created Continuous Delivery Pipeline.

- Creating a review stage

- Test Pipeline

To create the review stage perform the following:
- Select your pipeline and edit it
- Choose 'Add Stage' between the Build and Deploy stages
- In the Stage name field, enter Review and add the stage
- In the Review stage, add an action group
- Under Action name, enter **Manual_Review** and select **Manual approval**
- Confirm that the optional fields have been left blank and click done
- Choose save twice

Now you have successfully setup a manual approval stage.
The last thing we are going to do is to test the functionality of the created pipeline. For that we are going to change the App.js file in our repo using for example VSCode and then pushing the changes to our repo. The change can again be a simple change of the display message.
After you have commited and pushed your changes the pipeline should automaitcally get triggered.

Monitor the pipeline and approve the manual step once it is reached. As soon as the deploy stage is done you can navigate to your ElasticBeanstalk Environment and verify that the changes were applied by opening your Domain.

## 👀 References

1. ☁️ [AWS Create Continuous Delivery Pipeline](https://aws.amazon.com/getting-started/hands-on/create-continuous-delivery-pipeline/?ref=gsrchandson)