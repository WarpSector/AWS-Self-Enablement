# Domain 3: Technology
# (3D: Amazon Serverless Services)

## Executive Summary
The Serverless model represents the peak of cloud efficiency, shifting the focus from "Managing Infrastructure" to "Executing Logic." By removing the burden of server provisioning, patching, and OS management, these services allow you to build highly available, automatically scaling applications where you only pay for the exact resources consumed during execution.

## Overview
  * Amazon strongly promotes use of their serverless services such as Lambda, Fargate, DynamoDB.
  * With serverless there are NO instances to manage - you do not need to provision hardware.
  * There is no management of OS or software.
  * Capacity provisioning and patching is handled automatically.
  * Automatic scaling and high availability is provided.

## Serverless Services
  * AWS Lambda
  * AWS Fargate ("serverless containers" - *see EC2 Compute markdown file 3B for full details*)
  * Amazon EventBridge
  * AWS Step Functions
  * Amazon Simple Queue Service (SQS)
  * Amazon Simple Notification Service (SNS)
  * Amazon API Gateway
  * Amazon S3
  * Amazon DynamoDB

## AWS Lambda
  * Executes code only when needed and scales automatically.
  * You put your code on Lambda, something triggers it, it runs, and you only pay for the amount of time it runs (millisecond billing).
  * No overhead, provisioning resources, etc. - just upload your code and let it do its thing!
  * You pay $0 when your code is not running.
  * Lambda integrates with almost all other AWS services.

## Amazon SQS
  * Reliable, highly-scalable message queueing service storing messages in transit between computers.
  * Good for distributed and decoupled applications and architectures.
  * SQS is pull-based not push-based, so applications will poll SQS for messages and pull the message in queue - useful for requests coming in from the front-end and not overwhelming & flooding the transactional layer.
  * There's also **Amazon MQ**, a message service that's similar to SQS, but based on Apache MQ and Rabbit MQ - used when customers require industry standard APIs and protocols (used when we can't use Amazon's proprietary message protocols).

## Amazon SNS
  * Publisher - Subscriber Model: you publish a notification and the subscribers all receiver it at the same time.
  * SNS is used for building and integrating loosely coupled architectures.
  * Instantaneous push-based delivery (no polling like SQS).
  * Simple API, easy integration with applications.
  * Inexpensive, pay-as-you-go pricing with no upfront cost.

## AWS Step Functions
  * Serverless orchestration.
  * Makes it easy to manage and coordinate the components of distributed applications built with loosely coupled microservices (e.g., Lambda functions for short tasks & ECS/EKS Containers or Fargate for longer tasks) as a **series of steps in a VISUAL WORKFLOW**.
  * You can quickly build and run **"state machines"** to execute the steps of your application in a reliable and scalable fashion.
  * Step Functions replaces **Amazon Simple Workflow**, which is best-suited for asynchronous human-enabled tasks.

## AWS EventBridge
  * Serverless event bus.
  * The Event Bus is the central hub that receives events from various sources and "routes" them to targets based on rules you create - this is what AWS EventBridge is.
  * Used for building **event-driven architectures**.
  * You want something to happen when an event occurs --> EventBridge ingests data from the event --> EventBridge routes it to the target AWS services to respond to the event (e.g. Lambda functions).

## Amazon API Gateway
  * Used for publishing APIs on AWS.
  * Creates Restful APIs (using HTTP protocols and closing the connection after the request) and WebSocket APIs (keeping the "comm channel" (port) open and receiving continual updates in real-time).
  * Fully managed service.
  * Forwards connections to AWS services and on-prem applications (so you can use this in hybrid Cloud architectures).

## Summary Tables
### 🏛️ 1. Core Serverless Compute & Data
| Service | Primary Function | The "Exam Logic" |
| :--- | :--- | :--- |
| **AWS Lambda** | Event-driven code execution. | **Millisecond billing**; scales to zero; 15-min limit. |
| **AWS Fargate** | Serverless container engine. | Run Docker containers **without managing EC2 host servers**. |
| **Amazon S3** | Serverless object storage. | Infinite scaling; built-in High Availability (HA). |
| **Amazon DynamoDB**| NoSQL Key-Value database. | Millisecond latency; **On-Demand** or Provisioned scaling. |

---

### 🛡️ 2. Messaging & Decoupling (The "Glue")
| Service | Pattern | Best Use Case |
| :--- | :--- | :--- |
| **Amazon SQS** | **Pull / Queue** | **Decoupling**; prevents back-end flooding/overload. |
| **Amazon SNS** | **Push / Fan-out** | Sending one message to **many** subscribers (Email/SMS). |
| **Amazon EventBridge**| **Event Bus** | Routing events from AWS or **3rd-party SaaS** (Shopify/Zendesk). |
| **Amazon MQ** | **Standard Protocols** | Migrating **RabbitMQ** or **ActiveMQ** without rewriting code. |

---

### 🚀 3. Orchestration & Connectivity
| Service | Role | Key Feature |
| :--- | :--- | :--- |
| **AWS Step Functions** | **Orchestration** | Visual **State Machines**; manages multi-step workflows. |
| **Amazon API Gateway** | **API Entry Point** | Supports **RESTful** (Request/Response) and **WebSocket** (Real-time). |
