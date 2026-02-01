# Domain 3: Technology
# (3G: Automation and Continuous Integration/Continuous Deployment (CI/CD))

## Executive Summary
The Automation and Deployment domain transforms manual "click-ops" into scalable, repeatable code, enabling organizations to innovate faster while reducing human error. By leveraging Infrastructure as Code (CloudFormation) and integrated CI/CD pipelines (The CodeSuite), AWS provides a unified "conveyor belt" that automates the journey from a developer's browser-based IDE to a globally optimized, high-performance production environment.

## Amazon CloudFront
  * ### Overview
    * CloudFront is a **content delivery network (CDN)** that stores (caches) content (images, videos, apps, APIs) at Edge locations across the globe.
    * CloudFront allows you to deliver your content to users around the world faster and with low latency while also protected against DDoS attacks (Amazon Shield comes standard for DDoS protection and attaching a WAF also helps block XSS/SQL injection attacks).

## AWS Global Accelerator (same notes from the *3D Networking Markdown*)
 * ### Overview
   * Global Accelerator improves the availability and performance of applications for local and global users.
   * Global Accelerator uses the AWS Global Network to optimize the path for users to applications, which improves the performance of TCP and UDP traffic (such a online gaming).
   * Example: Users accessing applications via TCP/UDP traffic --> Routed to Regional Edge Location --> Global Accelerator uses the AWS Global Network backbone to optimize traffic to Origin Regions.
   * Global Accelerator accomplishes this by providing static IP addresses (anycast IPs) that act as fixed entry points to application endpoints in a single and/or multiple Regions (connecting to ALBs, NLBs, or EC2 instances).

## AWS CloudFormation
 * ### Overview
   * **Infrastructure as Code:** You can code templates for Cloud environments and resources you want (or are updating) via code (Terraform, YAML, or JSON).
   * Infrastructure is provisioned consistently with fewer errors and with less time and effort than configuring resources manually via the AWS Management Console via *click-ops*.
   * **Free-to-use:** you are only charged for the resources you've provisioned with your CloudFormation template.  
 * ### Stacks
   * When you build infrastructure with CloudFormation, the template you use builds a **STACK** of the infrastructure.
   * You can easily rollback and delete the stack as well.

## AWS Cloud Development Kit (CDK)
 * ### Overview
   * CDK is an open-source development framework that lets you use programming languages other than YAML or JSON to code CloudFormation templates.
   * Can use TypeScript, Python, Java, or .NET.
   * Can use existing integrated development environments (IDEs), testing tools, and workflow patterns with the CDK.

## AWS Developer Tools
  * ### Continuous Integration/Continuous Deployment (CI/CD)
    * #### **Continuous Integration (CI)**
      * A software development practice where developers regularly merge their code changes into a central repository (like AWS CodeCommit), after which automated builds and tests are run.
    * #### **Continuous Deployment (CD)**
      * The highest level of automation in the software release lifecycle.
      * While Continuous Integration (CI) builds and tests your code, Continuous Delivery ensures that code is ready for production.
      * Continuous Deployment (CD) actually pushes that code into the live production environment for customers to use automatically, with no human intervention.
  * ### AWS CodeCommit
    * Secure Git-based code repository where engineers write, store, update, debug, and work on code.
  * ### AWS CodeBuild
    * AWS service that compiles and tests code stored in AWS CodeCommit.
  * ### AWS CodeDeploy
    * Automated service that release delivered and tested code into live production.
  * ### AWS CodePipeline
    * The **orchestrator** of the AWS DevOps CI/CD pipeline.
    * CodePipeline bands all the stages (Commit, Build, Deploy) together into a workflow.
  * ### AWS CodeArtifact
    * **DO NOT CONFUSE WITH CODECOMMIT!**
    * AWS CodeArtifact stores the **LIBRARIES** needed for your code to work.
    * AWS CodeCommit stores the code you **WRITE**.
  * ### AWS CodeStar
    * CodeStar is the UI dashboard allowing you to view and project manage the entire CI/CD pipeline.
  * ### AWS Cloud9
    * Browser-based IDE to write and debug code.           

## AWS Apps
  * ### AWS AppConfig
    * Creates, manages and deploys application configurations.
    * Part of AWS Systems Manager and can be accessed and used there.
    * Configurations influence the behavior of your application.
    * Streamlines the deployment of your app configurations in one place so it reduces errors and prevents having to adjust configs app by app.
  * ### AWS X-Ray
    * Used to debug your distributed applications.
    * Used to trace requests through your applications to analyze latency.
    * Provides telemetry on your distributed apps so you can debug/update, etc.   

## Summary Tables of Automation and Deployment in AWS
### 🔄 1. The CI/CD Pipeline: Automation & Delivery
| Stage | Process | AWS Service | Key Difference |
| :--- | :--- | :--- | :--- |
| **Source** | Storing/Versioning Code | **CodeCommit** | Managed Git; triggers the pipeline. |
| **Build** | Compile & Test | **CodeBuild** | Runs automated tests; builds artifacts. |
| **Deploy** | Release to Servers | **CodeDeploy** | Pushes code to EC2, Lambda, or ECS. |
| **Orchestrate** | The Pipeline Flow | **CodePipeline** | **Bands all services together** into a workflow. |

---

### 🛡️ 2. Delivery vs. Deployment: The "Manual Gate" Test
* **Continuous Delivery:** Requires a **Human Approval** to push to Production. (The "Decision" is a business one).
* **Continuous Deployment:** **Fully Automated** push to Production. (The "Decision" is a technical one based on tests).

---

### 🔄 3. The AWS Developer Tools "CodeSuite"

| Service | Pipeline Role | Primary Job | Analogy |
| :--- | :--- | :--- | :--- |
| **AWS CodeCommit** | **Source** | Secure Git-based version control. | The Filing Cabinet |
| **AWS CodeBuild** | **Build/Test** | Compiles code and runs tests. | The Inspector |
| **AWS CodeDeploy** | **Deploy** | Automates code release to servers. | The Installer |
| **AWS CodePipeline** | **Orchestrate** | **Bands all stages together** automatically. | The Conveyor Belt |
| **AWS CodeStar** | **Project Mgmt** | Unified UI for the whole project. | The Dashboard |

**Key Mnemonic:** You **Commit** the code, **Build** the code, **Deploy** the code, and **Pipeline** manages the flow.

---

### 🛠️ 4. Developer Productivity & Analysis Tools

| Service | Primary Purpose | Key Exam Trigger |
| :--- | :--- | :--- |
| **AWS Cloud9** | Cloud-based IDE for writing and debugging code. | **"Browser-based editor," "Collaborative coding."** |
| **AWS CodeArtifact** | Repository for software packages/dependencies. | **"npm, pip, Maven," "Manage software libraries."** |
| **AWS X-Ray** | Trace requests through distributed applications. | **"Debugging," "Analyze latency," "Service Map."** |
| **AWS AppConfig** | Manage and deploy application configurations. | **"Feature flags," "Runtime updates without redeploy."** |

---

### 🧠 5. The "Source" vs. "Package" Distinction
* **CodeCommit:** I store **MY** code here (e.g., `app.py`).
* **CodeArtifact:** I store **THEIR** packages here (e.g., `numpy` or `boto3`).
