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

