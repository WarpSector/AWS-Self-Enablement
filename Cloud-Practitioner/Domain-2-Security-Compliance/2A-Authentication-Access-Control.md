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
    *       

