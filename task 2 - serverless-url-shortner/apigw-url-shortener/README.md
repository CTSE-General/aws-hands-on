# apigw-url-shortener

## 💡 Description

Usecase of the url shortener is to reaplace original domain to easily typable and user friendly short url, in order to display this url with clients inside/outside of the application.

- First, using POST /urls admin user can generate a simply designed url from original url. And this generated url will be mapped in DynamoDB.

- Second, GET /urls/{{path}} will set the original url into the Locatoin header of the response and returns HTTP Statuscode **307**. Whenever user cliks the fancy url form the application, user will be redirected to the original url.

## ✅ Requirements

- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed
- [Node and NPM](https://nodejs.org/en/download/) installed
- [NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html) installed
- [DynamoDBLocal.jar](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.DownloadingAndRunning.html) installed
- [AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed

## ✨ Architecture

Architecture is simple. CDK defines an ApiGateway with single endpoint of **urls**. To this endpoint lambda functions are attached to run business logics with DynamoDB.

Exactly same functionality of this AWS Services, however, can be hosted complete locally via **fiber** and **NoSQL Workbench**.

![](../docs/img/apigw-url-shortener.png)
