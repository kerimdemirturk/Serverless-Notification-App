# Serverless-App
Simple serverless application using S3, API Gateway, Lambda, Step Functions, SNS &amp; SES.

My application is going to send reminder messages from email.App using AMAZON SES for this.In production, it could be configured to allow sending from the application email to any users of the application.But I dont want any spam mails and I only used verified address and because sure it's a demo app.
First chard of app:
![chard1](_docs/assets/Serverless%20APP%20CHARD.png)
<br>
Then I configure SES in aws
![SES](_docs/assets/ses.jpg)

Then I create a email lambda function for using SES to send emails for the app.I start with creating lambda execution role for lambda.This roles gives permission to lambda for ses,sns and states.Then I create email reminder lambda function.
Chard for this part:
![chard2](_docs/assets/Screenshot%20from%202023-04-02%2017-13-24.png)
![lambda](_docs/assets/lambda.png)

In This part I add state machine,which is the main component of this serverless application.State machine will control the flow of the app.It will initially pause for a number of seconds, the time until the next cuddle requirement.After the time's expired,the state machine then uses the email Lambda function to send a cuddle notification  customer maill adress.The state machine has role for interact to other services which I use in this project.I use step functions in aws for creating state machine.
![chard3](_docs/assets/Screenshot%20from%202023-04-03%2020-02-33.png)
![stepfunction](_docs/assets/Screenshot%20from%202023-04-03%2019-52-45.png)

In this part I create a lambda function for supporting API Gateway and API Gateway itself which will function as the entry point to  application. By creating the API Gateway, I have an endpoint that client application can use to talk to application itself.So I create lambda function and configure API Gateway. 

![chard4](_docs/assets/Screenshot%20from%202023-04-03%2022-10-10.png)
![apıgateway](_docs/assets/Screenshot%20from%202023-04-03%2022-08-32.png)

In this stage of the application ı will create an S3 bucket and static website hosting which will host the application front end.I will download the source files for the front end, configure them to connect to your specific API gateway and then upload them to S3. Then I will run some application tests to verify its functionality.I use S3 for hosting client part of app.I will enable static website hosting in s3 also bucket is publicly accessible.
![chard5](_docs/assets/Screenshot%20from%202023-04-04%2016-50-20.png)
![s3](_docs/assets/newS3.jpg)
![frontend](_docs/assets/newappfrontend.jpg)

When I fill the information in this page state machine start to running and this is the timer state.I write 120 second for wait and when 120 second pass it will continue in email state.In this step lambda function invoke and send an email notification.When its completed its the end of the state machine execution.

![stepfunction](_docs/assets/stepfunction.png)
![execution](_docs/assets/executiondetail.jpg)


burayada step function resimleri.









