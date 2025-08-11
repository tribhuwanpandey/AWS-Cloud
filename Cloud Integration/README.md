# Cloud Integration


## Section Introduction

When deploying multiple applications, they often need to communicate with one another. There are two main patterns of application communication:

- **Synchronous communications** (application to application)  
- **Asynchronous / Event-based** (application → queue → application)  

Synchronous communication can be problematic during sudden spikes in traffic.  
**Example:** Needing to encode 1000 videos suddenly, while usually encoding only 10.

In such cases, it’s better to decouple your applications using:

- **SQS:** Queue model  
- **SNS:** Pub/Sub model  
- **Kinesis:** Real-time data streaming model (out of scope for the exam)  

These services scale independently from your application.

---

# Amazon SQS - Simple Queue Service

- One of the oldest AWS services (10+ years old)  
- Fully managed, serverless service to decouple applications  
- Enables asynchronous message sending and receiving  
- Supports:
  - **Standard queues:** Unlimited throughput, at-least-once delivery (messages may be delivered more than once)
  - **FIFO queues:** Ordered processing, exactly-once processing  
- Scales from 1 message/second to tens of thousands per second  
- Message retention: default 4 days, max 14 days  
- Unlimited messages in queue  
- Messages deleted after consumption  
- Low latency (<10 ms on publish/receive)  
- Consumers share message processing load and scale horizontally

---

# Amazon Kinesis

- Real-time big data streaming service  
- Managed service to collect, process, and analyze streaming data at any scale  

**Components (too detailed for Cloud Practitioner but good to know):**

- **Kinesis Data Streams:** Low-latency ingestion from hundreds of thousands of sources  
- **Kinesis Data Firehose:** Load streams into S3, Redshift, Elasticsearch, etc.  
- **Kinesis Data Analytics:** Real-time stream analytics using SQL  
- **Kinesis Video Streams:** Stream and analyze real-time video data  

---

# Amazon SNS - Simple Notification Service

- Publishes one message to many receivers (pub/sub model)  
- “Event publishers” send messages to one SNS topic  
- Multiple “event subscribers” receive all messages from the topic  
- Supports up to 12,500,000 subscriptions per topic and 100,000 topics per account  
- Subscribers can be:
  - Email  
  - Lambda  
  - SQS  
  - HTTP endpoints  
  - Mobile push notifications  

---

# Amazon MQ

- Traditional applications often use open messaging protocols like MQTT, AMQP, STOMP, OpenWire, WSS  
- Instead of rewriting apps to use SQS/SNS, migrate using **Amazon MQ**: a managed Apache ActiveMQ service  
- Not serverless; runs on dedicated machines  
- Supports both queue (like SQS) and topic (like SNS) features  
- Less scalable than SQS/SNS but supports legacy protocols  

---

# Integration - Summary

| Service     | Description                                        | Key Characteristics                                  |
|-------------|--------------------------------------------------|-----------------------------------------------------|
| **SQS**     | AWS queue service                                 | Multiple producers, messages retained up to 14 days, multiple consumers share messages, used to decouple applications |
| **SNS**     | AWS notification service                          | Multiple subscribers, sends all messages to all, no message retention |
| **Kinesis** | Real-time streaming data collection, persistence and analytics | Real-time data streaming and analysis                 |
| **Amazon MQ** | Managed Apache MQ in AWS cloud                   | Supports MQTT, AMQP protocols; runs on dedicated machines; supports queues & topics |

