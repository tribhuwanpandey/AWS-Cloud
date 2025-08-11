#  Amazon CloudWatch & Monitoring Tools for AWS

A comprehensive overview of **Amazon CloudWatch** and related AWS monitoring tools.

---

##  Amazon CloudWatch

Amazon CloudWatch is a **monitoring and observability service** for AWS resources and applications. It enables real-time tracking of metrics, logs, events, and automated responses to operational changes.

###  Key Features

- **Collect and track metrics**
- **Set alarms and automate actions**
- **Store and access logs**
- **Create CloudWatch Dashboards**

---

###  Metrics Overview

A **metric** is a variable to monitor, such as `CPUUtilization`, `NetworkIn`, etc.

#### Important Metrics by AWS Service

| Service        | Metrics Examples                                                                 |
|----------------|-----------------------------------------------------------------------------------|
| EC2 Instances  | `CPUUtilization`, `DiskReadOps`, `NetworkIn/Out`                                  |
| EBS Volumes    | `VolumeReadOps`, `VolumeWriteOps`                                                 |
| RDS Databases  | `CPUUtilization`, `FreeStorageSpace`, `ReadIOPS`, `WriteIOPS`                     |
| S3 Buckets     | `AllRequests`, `4xxErrors`, `5xxErrors`, `FirstByteLatency`                       |
| Lambda         | `Invocations`, `Errors`, `Duration`                                               |
| Billing        | `EstimatedCharges` (only in `us-east-1`)                                          |
| Custom Metrics | Push your own metrics using the CloudWatch API                                    |

####  Monitoring Frequency

- **Default**: Every 5 minutes
- **Detailed Monitoring (extra cost)**: Every 1 minute

---

##  Amazon CloudWatch Alarms

Create **automated alerts or actions** when a metric exceeds a threshold.

### Examples

- Alert if **EC2 CPU > 80%**
- **Auto-scale** EC2 instances based on demand
- Perform EC2 actions: `stop`, `terminate`, `reboot`, `recover`
- Send alerts via **SNS**
- Create **Billing Alarms** to monitor usage costs

### Alarm States

- `OK`
- `ALARM`
- `INSUFFICIENT_DATA`

---

##  Amazon CloudWatch Logs

Provides **centralized logging** for AWS services and custom applications.

### Supported Sources

- **Elastic Beanstalk**
- **ECS Containers**
- **AWS Lambda**
- **CloudTrail logs**
- **EC2 instances** (via CloudWatch Agent)
- **Route 53 DNS logs**

###  Setup Notes

- By default, **EC2 does not send logs** to CloudWatch.
- You must **install and configure the CloudWatch Agent**.
- Ensure the instance has **correct IAM permissions**.
- CloudWatch Logs Agent can also be used on **on-premises servers**.

---

##  Amazon CloudWatch Events & EventBridge

CloudWatch Events delivers **event streams** that describe changes in AWS resources.

### Use Cases

- **Trigger Lambda** when EC2 state changes
- **Schedule scripts** (Cron jobs)
- **Send SNS messages** on specific events

###  EventBridge

EventBridge is the **next generation** of CloudWatch Events, supporting:

- **Default event bus**: AWS service events
- **Partner event bus**: Events from SaaS providers (e.g., Datadog, Zendesk)
- **Custom event bus**: For your own applications
- **Schema Registry**: Discover and model event schemas

---

##  AWS CloudTrail

AWS CloudTrail provides **audit logging of all API activity** in your AWS account.

###  Key Features

- **Logs API calls** from Console, CLI, SDKs, and services
- **Tracks**: Who made the call, when, and from where
- **Default retention**: 90 days (store to S3 for longer)

###  Types of Events

- **Management Events**: e.g. IAM policy changes, resource creation
- **Data Events**: e.g. S3 object access, Lambda invokes _(not enabled by default)_

---

##  CloudTrail Insights

CloudTrail Insights helps **detect unusual activity** by analyzing management events.

### Detects:

- Resource misconfigurations
- Sudden bursts of activity (e.g. IAM actions)
- Gaps in maintenance patterns

### Delivery

- **Stored in S3**
- **Trigger EventBridge** events for automation

---

## AWS X-Ray

A **distributed tracing system** that helps debug and analyze AWS and custom applications.

### Key Features

- **Trace requests** through AWS and your app
- **Identify bottlenecks and exceptions**
- **Visualize service maps and dependencies**
- **Support for local testing and deployment**

---

## Amazon CodeGuru

Amazon CodeGuru offers **automated code reviews** and **performance profiling**.

###  CodeGuru Reviewer

- ML-powered **static code analysis**
- Detects:
  - Security issues
  - Code inefficiencies
  - Best practice violations
- Supports: **Java** and **Python**
- Integrates with: GitHub, Bitbucket, CodeCommit

###  CodeGuru Profiler

- Understand runtime behavior
- Identify CPU or memory-intensive code
- Help **optimize application performance** and reduce compute cost

---

##  AWS Status Dashboards

###  [Service Health Dashboard](https://status.aws.amazon.com/)

- Global status of all AWS services by region
- Shows **historical and live status**
- **RSS Feed** available

###  [Personal Health Dashboard](https://phd.aws.amazon.com/)

- Personalized view of AWS events **affecting your resources**
- **Proactive alerts**, scheduled changes, and guidance

---

##  Cloud Monitoring Summary

| Service                    | Key Features                                                                 |
|----------------------------|------------------------------------------------------------------------------|
| **Amazon CloudWatch**      | Metrics, Alarms, Logs, Events, EventBridge                                   |
|                            | - Monitor service/billing metrics                                            |
|                            | - Alarms: notifications, EC2 actions, SNS                                    |
|                            | - Logs: from EC2, Lambda, and more                                           |
|                            | - Events/EventBridge: trigger based on activity                              |
| **AWS CloudTrail**         | Tracks API activity, auditing, and compliance                                |
| **CloudTrail Insights**    | Detects anomalies in API call patterns                                       |
| **AWS X-Ray**              | Traces requests across distributed apps, visualizes bottlenecks              |
| **Amazon CodeGuru**        | Automated code reviews, profiling runtime performance                        |
| **Health Dashboards**      | General (status.aws.amazon.com) & Personalized (phd.aws.amazon.com)          |

---

##  Resources

- [AWS CloudWatch Docs](https://docs.aws.amazon.com/cloudwatch/)
- [AWS CloudTrail Docs](https://docs.aws.amazon.com/cloudtrail/)
- [Amazon X-Ray Docs](https://docs.aws.amazon.com/xray/)
- [Amazon CodeGuru Docs](https://docs.aws.amazon.com/codeguru/)

---

> _“Monitor everything. React intelligently.”_

---
