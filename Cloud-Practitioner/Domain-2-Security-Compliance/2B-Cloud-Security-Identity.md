# Domain 2: Security and Compliance
# (2B: Cloud Security and Identity)

## Identity Federation
  * ### Overview
    * Ultimately, identity federation is **single sign-on (SSO)** for the Cloud.
    * It allows you to use your existing credentials from one system (like your company’s Active Directory, or even your Google/Facebook account) to access AWS resources without having to create a separate IAM user for every person.
  * ### IAM - Security Assertion Markup Language (SAML) 2.0 Identity Federation
    * #### SSO Flow using SAML 2.0
      1. User logins into their on-prem systems --> Windows Active Directory (this is an "Identity Store" since it stores user IDs) --> User can access on-prem applications and resources after logging in through Windows Active Directory (AD).
      2. What if the user now wants to access a resource on the AWS Cloud? --> Before that can happen, the user must go through an **identity provider (IdP)** like Windows Active Directory Federation Server (ADFS) --> ADFS allows SSO into the AWS VPC.
      3. Before the user can access resources in the AWS VPC, the AFDS uses IdP that will let the user access the resource --> The IdP goes to the **Amazon Security Token Service (STS)** --> STS provides a temporary security token to the IdP --> User can then access resources in the AWS VPC.
  * ### IAM - Web Identity Federation
    * #### SSO Flow using Web Identity Federation
      * The flow is similar to SMAL 2.0, except the user authenticate using either their Amazon, Apple, Google, or Meta account to access resources.
      * So the user uses a **social identity provider (IdPs)** to access AWS Cloud resources from their mobile device.
      * The IdPs talks to the STS, which returns the temporary token to the user's device letting them access the resource in the AWS VPC.
      * Amazon recommends using **AWS Cognito** for web identity federation.
  * ### IAM - Identity Center
    * #### Overview
      * This is AWS's successor to AWS Single-Sign On.
      * This service enables centralized management of permissions and SSO.
      * You can store identities within Identity Center and they can be identities within Identity Center itself, Azure AD, or any providers using the SAMLE 2.0 protocol.
      * Identity Center can integrate with AWS Organizations to connect to different accounts created throuhg AWS Organizations.
  * ### AWS Cognito
    * #### Overview
      * Cognito can be used for Web Identity Federation by either storing the account in **Cognito User Pool** or by retieving IdSp from the user's Amazon, Apple, Google, or Meta account.
      * The **Cognito User Pool** is the service responsible for authenticating the user.
      * From the Cognito User Pool, a JSON Web Token (JWT) is issued, which then goes to the **Cognito Identity Pool**, which then talks to STS to issue the temporary security token for the session --> User can access resources in the VPC.
                      
