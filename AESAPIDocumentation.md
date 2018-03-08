## Process to Onboard onto AES

1.	To onboard onto our Azure Email Service (AES) using our API call, we first need your certificate thumbprint 
     - To do this, you will need to create a Client Certificate (.cer file - public key file) by going to [SSLAdmin] (http://SSLadmin)- follow the steps outlined on the page

**NOTE:** 

     - This process will require your manager's approval
     - Once the manager approves the request, this can take ~3-4 hours for you to receive your Client Certificate
       
2.	Please send the following to the Azure Email Service team: 
     - Thumbprint of the certificate
     - Your Name
     - Your Team Name
     - The email address you wish to send ‘as’ (i.e. TeamName@azureemail.microsoft.com)
     - The “friendly name” to send ‘as’ (i.e. Microsoft Cloud Engineering Team)
     - Email template(s) you wish to ‘program’ into our system
     - The email address you wish to send test emails to (today, we support only one test email address)
       - For example, when we do the initial round of tests, all emails will automatically be routed to this email address so we can ensure that no data is sent to the customer accidentally until we have sign-off to go live
       - If test emails are going to a DL/SG, please check IDWeb to ensure you can accept emails outside of Microsoft. 
       
     - If this email is a non-transactional/promotional email, do you need your emails to be De-duped based on a look-back period? Yes/No
       - For example, should a user (email address) receive more than one email for this email template? 
     - Do you need sovereign/national cloud support? If so, which sovereign/national clouds?
     - The languages (localization) you need your email templates to have?
       - We can support certain languages - SLA is 2-3 days
       - This will create a net new email template URL for those locales


       We will use your information to: 
       - Create your Client ID (GUID) that you will use to call our API
       - Create your email template(s) in our system

3.	Import the Nuget packet "Microsoft.CE.CIP.TransactionalEmailClient" from the package source 'wanuget' 
 
     - This is a thin layer wrapper to make REST calls to our API which includes the contract models published

## Calling the AES API

You can use this sample code snippet to start making calls to our service:
```C#
 var environment = EmailEnvironment.Prod;
```
You can use our pre-production environment too with the value as "EmailEnvironment.Int" DO NOT use our Dev environment to test.
```C#
var client = Microsoft.CE.CIP.TransactionalEmailClient.EmailClient.Create(environment, (your assigned ClientId from CIP), 
(your certificate thumbprint that is used to authenticate and onboard with CIP));
```
This expects the onboarded certificate is installed on the calling machine

<img src="\AES\wanuget.png" class="inline">

## Sovereign Cloud Onboarding

If you are interested in onboarding into one of the sovereign/national clouds: Blackforest, Fairfax, and/or Mooncake, please provide the following to AES Support:


| Items | Public Cloud | Sovereign Cloud |
| :--- | :--- | :--- |
| Transactional emails | Yes | Yes |
| Promotional emails | Yes | Yes |
| Transactional Opt Out | Yes | Yes |
|Telemetry | Yes | No |
|Schedule emails | Yes | No |
    
    
  


