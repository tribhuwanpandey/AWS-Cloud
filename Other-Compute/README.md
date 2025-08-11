# Other Compute Services on AWS

---

## What is Docker?

- Docker is a software development platform to deploy apps.
- Apps are packaged in containers that can run on any OS.
- Apps run the same regardless of where they’re run:
  - Any machine
  - No compatibility issues
  - Predictable behavior
  - Less work
  - Easier to maintain and deploy
- Works with any language, any OS, any technology.
- Scale containers up and down very quickly (seconds).

---

## Where are Docker Images Stored?

- **Docker Hub:** Centralized public repository for Docker images.  
  Public: [https://hub.docker.com/](https://hub.docker.com/)  
- **Amazon ECR (Elastic Container Registry):** AWS service for storing, managing, and deploying container images (private repository).

---

## Docker vs Virtual Machines

| Docker Containers                    | Virtual Machines (VMs)           |
|------------------------------------|---------------------------------|
| Lightweight, shares host OS kernel | Heavier, includes full OS       |
| Starts in seconds                  | Slower startup (minutes)        |
| Portable, fast scaling             | Less portable, resource-intensive |
| Best for microservices & modern apps | Best for running multiple OS environments |

---

## ECS (Elastic Container Service)

- Fully managed container orchestration service.
- Supports Docker containers.
- Launch Docker containers on AWS.
- AWS handles starting and stopping containers.
- Two launch modes:
  - **EC2:** Self-managed instances.
  - **Fargate:** Serverless compute for containers.
- Integrates with IAM, VPC, ELB, and ECR.

---

## Fargate

- Serverless compute engine for containers (works with ECS and EKS).
- No need to manage EC2 instances.
- Pay only for resources used (vCPU and memory).
- AWS runs containers based on CPU/RAM requirements.

---

## ECR (Elastic Container Registry)

- Fully managed Docker container registry.
- Stores, manages, and secures Docker images.
- Integrated with ECS, EKS, and Fargate for easy deployment.
- Central place to store Docker images for AWS container services.

---

## What’s Serverless?

- No need to provision, scale, or manage servers.
- Resources are automatically provisioned and scaled by AWS.
- Developers just deploy code — functions!  
- Initially Serverless == FaaS (Function as a Service).
- Serverless now includes managed databases, messaging, storage, etc.
- Serverless means **you don’t manage or provision servers** — they just run.
- Ideal for event-driven and stateless applications.

---

## Why AWS Lambda?

- Serverless compute service to run code without managing infrastructure.
- Executes code in response to events (e.g., API calls, file uploads).
- Scales automatically, pay only for usage.

| EC2                      | Lambda                       |
|--------------------------|------------------------------|
| Virtual servers in cloud  | Virtual functions, no servers |
| Limited by RAM and CPU    | Limited by time (short runs)  |
| Continuously running      | Run on-demand                 |
| Scaling requires intervention | Automated scaling          |

---

## Benefits of AWS Lambda

- No server management.
- Automatic scaling based on events.
- Flexible scaling from few to thousands of requests per second.
- Event-driven architecture.
- Pay per request and compute time.
- Free tier: 1 million requests and 400,000 GB-seconds compute time monthly.
- Integrated with AWS ecosystem.
- Easy monitoring with CloudWatch.
- Up to 10GB RAM per function (increases CPU & network too).

---

## AWS Lambda Language Support

- Node.js  
- Python  
- Ruby  
- Java  
- Go  
- .NET Core  
- Custom runtimes via container images (community-supported, e.g. Rust)  

---

## Lambda Container Image

- Container image must implement Lambda Runtime API.
- ECS / Fargate preferred for running arbitrary Docker images.

---

## AWS Lambda Pricing (Example)

- First 1 million requests/month free.
- After that: $0.20 per million requests.
- Execution duration: $0.00001667 per GB-second (first 400,000 GB-seconds free).
- Billing in 1 ms increments.
- Usually very cost-effective and popular.

More details: [AWS Lambda Pricing](https://aws.amazon.com/lambda/pricing/)

---

## Amazon API Gateway

- Managed service to create, publish, and monitor REST, HTTP, and WebSocket APIs.
- Integrates with AWS Lambda for fully serverless APIs.
- Supports security, authentication, throttling, API keys, monitoring.
- Includes caching and authorization features.

---

## AWS Batch

- Fully managed batch processing service.
- Dynamically provisions compute resources based on job needs.
- Suitable for large-scale data processing (ML, rendering).
- Runs hundreds of thousands of batch jobs.
- Batch jobs defined as Docker images running on ECS.
- Optimizes cost and infrastructure management.

---

## Batch vs Lambda

| AWS Batch                         | AWS Lambda                     |
|----------------------------------|--------------------------------|
| Designed for batch processing     | Designed for event-driven apps |
| Handles large-scale compute jobs  | Executes short-lived functions |
| Uses custom EC2 or Fargate tasks  | Fully serverless               |
| Jobs can take minutes to hours    | Max execution time 15 minutes  |
| Relies on EBS/instance storage    | Limited temporary disk space   |

---

## Amazon Lightsail

- Virtual servers, storage, databases, and networking.
- Low and predictable pricing.
- Simpler alternative to EC2, RDS, ELB, EBS, Route 53.
- Great for beginners and small projects.
- Templates for popular stacks: LAMP, Nginx, MEAN, Node.js, WordPress, Magento, Joomla, Plesk.
- Use cases:
  - Simple web applications
  - Websites
  - Dev/test environments
- High availability but no auto-scaling and limited AWS integrations.

---

## Lambda Summary

- Serverless Function as a Service with seamless scaling.
- Billing by runtime x RAM provisioned and invocation count.
- Supports multiple programming languages.
- Max execution time 15 minutes.
- Use cases:
  - Image thumbnail creation on S3 uploads.
  - Serverless cron jobs.
  - API Gateway integrations for HTTP APIs.

---

## Other Compute Summary

- **Docker:** Container technology to run applications.
- **ECS:** Run Docker containers on EC2 instances.
- **Fargate:** Run Docker containers without managing infrastructure (serverless).
- **ECR:** Private Docker image repository.
- **Batch:** Run batch jobs on managed EC2 instances.
- **Lightsail:** Simple, low-cost app & DB hosting.

