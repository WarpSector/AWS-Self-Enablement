# Domain 2: Security and Compliance
# (2A: Authentication and Access Control)

## AWS Identity and Access Management (IAM)
  * ### Overview
    * IAM is an AWS web service that helps you securely control access to AWS resources on your account.
    * IAM controls who is **authenticated** (signed in) and who is **authorized** (has permissions) to use resources.
  * ### Users
    * **Users** are individual accounts you log in with.
    * Users have **NO** permissions to access anything **by default**.
  * ### Groups
    * Groups are used for organizing users and assigning **policies** to them.
  * ### Policies
    * Policies are used for **defining** permissions (re: who is authorized to access what).
  * ### Roles
    * Roles are used for **delegating** permissions and are assumed by **services**.
    * AWS services can be assigned **roles** the same way roles can be assigned to users.
  * ### AWS Management Console
    * The AWS Management Console is used to manage the AWS account (or accounts if using AWS Organizations).
    * Users log into the AWS Management Console using a username and password (with strong password policies).
  * ### Access Keys
    * Access keys are used for CLI and API access (programmatic).
    * Access Keys consist of:
      * Access Key ID
      * Secret Access Key
    * **Users must always make sure their access keys are private!**
  * ### Root Users
    * The **root user** is the user that created the AWS account.
    * Root users have full permissions and cannot be restricted (unless restricted by a Service Control Policy (SCP)).
  * ### Multi-Factored Authentication (MFA)
    * Uses an additional factor in addition to a password to authenticate (typically a random generated numerical code from another device).
    * MFA uses the **"something you have"** (MFA device + code) and **"something you know"** (your username + password) to authenticate.          
  * ### Service Control Policies (SCPs)
    * SCPs are a feature of AWS Organizations.
    * SCPs are used to define the maximumavailable permissions in an account.
    * SCPs do not grant permissions - they just define what is allowed in the account.
  * ### IAM Best Practices
    * Lock away your AWS account root user access keys.
    * Create individual IAM users - **DO NOT SHARE USER ACCOUNTS!**
    * Use **GROUPS** to assign permissions to IAM users.
    * Add users to a GROUP --> Apply POLICIES to a Group = All users in that GROUP have the same permissions AND it's very easy to manage permissions for that GROUP and associated users.
    * **Grant least privilege!** (Principal of Least Privilege): Users and Groups have the minimum amount of permissions required to perform their tasks - nothing less, nothing more.
    * Get started using permissions with AWS managed policies - only use custom policies once you are deeply familiar with the services and permissions available to minimize security risks.
    * Use customer managed policies instead of inline policies (inline policies are where you assign a policy directly to a user account or a role - it's always safer to separate the policies from the users and have them in one place where you can then assign them to groups or to roles and update them in one place).
    * Use **access levels** to review IAM permissions - meaning constantly review the permissions granted to users to ensure the principal of least privilege is being applied.
    * Configure a strong password policy for your users.
    * Enable MFA.
    * Use **ROLES** for applications that run on EC2 instances - don't use access keys and don't put access keys into the application code - always safer to assign a ROLE to an application to grant it permissions.
    * Use **ROLES** to delegate permissions.
    * Do not share access keys.
    * Rotate credentials regularly.
    * Remove unnecessary credentials.
    * Use policy conditions for extra security.
    * Monitor activity in your AWS account.  
