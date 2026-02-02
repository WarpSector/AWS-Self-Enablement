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

## AWS Directory Service
  * ### Overview
    * A suite of products with various options for hosting a directory service in the Cloud or connecting to another directory service.
    * AWS Managed Microsoft Active Directory is one of such directory services you can connect to via AWS Directory Service - this is a fully managed service by AWS on AWS infrastructure.  

## AD Connector
  * ### Overview
    * You can connect a different directory (such as MS AD) via VPN to an AD Connector.
    * The AD Connector then connects to various AWS services.
    * Rather than having any director service running in the Cloud, we can just connect them to the Cloud through the AD Connector.
    * AD Connector eliminates the need for directory synchronization as well as the cost and complexity of hosting a federation structure.
    * Connects your on-prem to AD to AWS.

## Secrets
  * ### Systems Manager Parameter Store
    * Provides hierarchal storage for data management and secrets management.
    * Highly scalable, available, and reliable/durable.
    * You can store passwords, database strings, and license codes as **parameter values**.
    * You can store parameter values as plain text (unencrypted) or as cipher text (encrypted).
    * You then reference parameter values by using the unique name that you specified when you created the parameter.
    * You don't have to store the info in your code, you can store it in a secure, centralized place (you might have lots of apps and can change/store parameter values in one place).
      * #### Example:
        * An EC2 instance needs to query RDS --> In order to authenticate and retrieve information from the DB, it makes an API call to the **Parameter Store** --> The Parameter Store holds a DB connection string --> EC2 instance retrieves the string --> EC2 authenticates and is able to query RDS.   
  * ### AWS Secrets Manager
    * Similar to Parameter Store, but has some additional features, and costs more in some cases.
    * Allows native and automatic rotation of access keys, passwords, etc.
    * Has central auditing for rotation and fine-grained permissions. 

## Encryption
  * ### Overview
    * Data is encrypted **in transit** (as it moves over the network) and **at rest** (while its stored).
    * **Encryption In Transit:** User is connecting to an application over the internet using the HTTPS protocol, which utilizes the **SSL/TLS** certificate to encrypt data **IN TRANSIT**.
    * **Encryption At Rest:** User uploads unencrypted object into S3 and S3 automatically encrypts the object using a **DATA ENCRYPTION KEY** to encrypt the object as it's being written into the S3 bucket.
  * ### Asymmetric Encryption
    * Also known as "public key cryptography".
    * Messages encrypted with a **public key** can only be decrypted by a **private key**.
    * Messages encrypted with a **private key** can only be decrypted by a **public key**.
    * This is why it's known as **asymmetric encryption**.
    * Examples include SSL/TLS certificates and SSH.
  * ### AWS Certificate Manager (ACM)
    * ACM creates, stores, and renews SSL/TLS certificates.
    * Supports single and multiple domains.
    * Integrates with ELB, CloudFront, CloudFormation, Elastic Beanstalk, and Nitro Enclaves.
    * For example: when you're generating a website with CloudFront, you can select a certificate from ACM. 
  * ### Symmetric Encryption
    * Encryption takes place by encrypting the plain text data with an encryption key.
    * Decryption takes place by decrypting the plain text **with the same key**.
    * This is why it's known as **symmetric encryption**.
  * ### AWS Key Management Service (KMS)
    * Creates and manages **BOTH** synmmetric and asymmetric *software* keys.
    * **Customer Managed Keys (CMKs)** are protected by **Hardware Security Modules (HSMs)**.
    * CMKs are created by developers and stored in KMS.
    * CMKs are used for encryption.
    * You can also use **AWS Managed Keys** that are provided by AWS to encrypt things like EBS volumes, SQS, FSx, etc. vs. using CMKs.
  * ### AWS Hardware Security Modules (HSMs)
    * Hardware Security Modules are physical, tamper-resistant computing device that generates, manages, and stores cryptographic keys.
    * In the AWS world, you'll see this as AWS CloudHSM. While most users are happy with AWS KMS (which is a managed software service), some organizations require the "physical isolation" of an HSM to meet strict regulatory or security standards.  

## Logging and Auditing
  * ### AWS CloudWatch
    * CloudWatch monitors the performance of the applications and resources in your AWS account.
    * CloudWatch is also a respository for **metrics** from your EC2 instances, network, S3, utilization, etc.
    * **CloudWatch Logs:** CloudWatch Logs gathers the metrics and builds the repository.
  * ### AWS CloudTrail
    * CloudTrail captures user activity and API calls in your AWS account such as creating or terminating resources, logins, etc.
    * CloudTrail captures who used an API, what time, what action, and on what resource.
    * Logs are retained for 90 days **unless** a **CLOUDTRAIL TRAIL** logs events into an S3 bucket for indefinite retention.
    * CloudTrails can be in one or multiple Regions.
  * ### VPC Flow Logs
    * VPC Flow Logs capture information about the IP traffic going to and from network interfaces within a VPC.
    * Data is stored using CloudWatch Logs at the VPC, subnet, and network interface levels.
  * ### Access Logs
    * **ELB Access Logs:** captures detailed information about requests sent to the load balancer, the IP, request type, etc. to analyze traffic patterns.
    * **S3 Access Logs:** choose a target bucket and provides detailed records for requests made to the bucket (disabled by default).  
