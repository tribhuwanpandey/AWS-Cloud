# AWS-Cloud
Amazon web servies and uses


What is Cloud Computing?

Cloud computing is the on-demand delivery of compute power, database storage, applications, and other IT resources through a cloud services platform with pay-as-you-go pricing. It provides:

1: Provisioning of exactly the right type and size of computing resources.
2: Access to as many resources as needed, almost instantly.
3: A simple way to access servers, storage, databases, and a set of application services.
4: Amazon Web Services (AWS) owns and maintains the network-connected hardware, while you provision and use what you need via a web application.



The Deployment Models of the Cloud:

Private Cloud: 

1: Cloud services used by a single organization, not exposed to the public.
2: Complete control over data, security, and compliance.
3: Security for sensitive applications, ideal for critical workloads.       
4: Meet specific business needs and compliance requirements.

Public Cloud:

1: Cloud resources owned and operated by a third-party cloud service provider, delivered over the Internet.
2: Cost-effective as infrastructure is shared among multiple users.
3: Suitable for less sensitive workloads that require high scalability and availability.
4: No maintenance required as the cloud provider manages the infrastructure.

Hybrid Cloud:

1: Keep some servers on-premises and extend some capabilities to the cloud.
2: Allows data and applications to be shared between private and public clouds.   
3: Offers flexibility, security, and scalability for different use cases.
4: Provides business continuity, disaster recovery, and data backup solutions.



The Five Characteristics of Cloud Computing:

1: On-demand self-service: Provision computing resources as needed automatically.
2: Broad network access: Access cloud resources over the network using standard mechanisms.
3: Resource pooling: Providers serve multiple customers using a multi-tenant model.
4: Rapid elasticity: Resources can be scaled up or down rapidly.
5: Measured service: Resource usage is monitored and billed accordingly.




Six Advantages of Cloud Computing:

1: Cost Savings: Pay only for the computing power, storage, and other resources you use.
2: Speed and Agility: Quickly deploy services and resources.
3: Scalability: Easily scale resources up or down as needed.
4: High Availability: Highly available architecture for business continuity.
5: Global Reach: Access services from any geographical region.
6: Security: AWS provides robust security capabilities to protect your data.



Problems Solved by the Cloud:

1: High upfront costs: Replaced by a pay-as-you-go model.
2: Scalability limitations: Dynamic scaling to meet business demands.
3: Limited infrastructure availability: Global infrastructure to support workloads.



Types of Cloud Computing:

1: Infrastructure as a Service (IaaS): 

a: Provides virtualized computing resources over the internet (e.g., AWS EC2).	
b: Offers maximum control over the infrastructure.	
c: Suitable for developers needing control over OS, middleware, and runtime.	

2: Platform as a Service (PaaS)	:

a: Provides a platform allowing customers to develop, run, and manage applications (e.g., AWS Elastic Beanstalk).	
b: Focus on deploying applications without managing underlying infrastructure.	
c: Ideal for developers who want to focus on application development.	

3: Software as a Service (SaaS):

a: Provides software applications over the internet on a subscription basis (e.g., AWS Chime).
b: Accessible over the internet, usually via a web browser.
c: Suitable for users needing access to software without infrastructure management.


Example of Cloud Computing Types:

IaaS: AWS EC2 (Elastic Compute Cloud),GCP, Azure, Rackspace, Digital Ocean, Linode
PaaS: AWS Elastic Beanstalk,Heroku, Google App Engine (GCP), Windows Azure (Microsoft)
SaaS: AWS Chime,Google Apps (Gmail), Dropbox, Zoom



Pricing of the Cloud – Quick Overview:  AWS follows three fundamental pricing principles based on the pay-as-you-go pricing model:

Fundamental	            Description

Compute                 Pay for the compute time you consume. Examples include EC2 instance hours or Lambda invocation duration.
Storage                 Pay for the amount of data stored in the cloud. Examples include S3 storage space and EBS volume usage.
Data Transfer OUT	    Pay for data transfer out of the cloud. Data transfer IN is free. This pricing structure solves the issue of  
                        expensive data transfer fees in traditional IT systems.



How Cloud Pricing Solves Traditional IT Cost Issues:

1: Traditional IT requires expensive upfront investments for hardware, maintenance, and upgrades.
2: With AWS's pay-as-you-go model, you only pay for what you use, reducing overall costs.
3: You can scale up or down based on demand, minimizing under-utilized resources.



AWS Cloud Use Cases:

1: Web Hosting: Host websites with elastic scaling and high availability.
2: Big Data Analytics: Run analytics on large datasets.
3: Application Hosting: Host applications with global accessibility and automated scaling.
4: Disaster Recovery: Implement disaster recovery strategies with minimized infrastructure.
5: Backup and Storage: Store backups in a highly durable and secure manner.



AWS Global Infrastructure:

AWS Regions:

1: Geographically isolated areas where AWS clusters data centers.
2: Each region has multiple Availability Zones.
3: Used to deploy applications close to customers for lower latency.



How to Choose an AWS Region?

1: Latency: Choose a region closest to your customers for lower latency.
2: Compliance: Ensure the region meets data residency and compliance requirements.
3: Services Available: Check which AWS services are offered in the region.
4: Pricing: Prices vary by region, so choose a region that fits your cost requirements.



AWS Availability Zones (AZs):

1: Multiple, isolated data centers within a region.
2: Each AZ has independent power, cooling, and networking.
3: Provides redundancy and fault tolerance in case of a failure.
4: They’re connected with high bandwidth, ultra-low latency networking



AWS Points of Presence (Edge Locations):

1: Network locations that deliver content closer to end users.
2: Used by services like Amazon CloudFront and AWS Global Accelerator.
3: Provides low latency and improved performance for content delivery.



AWS Shared Responsibility Model:

What is the Shared Responsibility Model?

1: AWS and the customer share responsibility for security and compliance.
2: Divides security tasks based on AWS as the provider and customer as the user of cloud services.


AWS Responsibilities: Security of the Cloud:

1: AWS is responsible for protecting the infrastructure that runs all services offered in the AWS Cloud.
2: Includes hardware, software, networking, and facilities:
    a: Physical security of data centers (e.g., access control, environmental controls).
    b: Infrastructure security, such as maintaining hypervisors, host operating systems, and network infrastructure.
    c: Global network operations, such as DDoS protection and monitoring.



Customer Responsibilities: Security in the Cloud:

1: Customers are responsible for managing and securing what they put in the cloud.

Includes:
    a: Data protection: Encrypt data in transit and at rest.
    b: IAM: Control access through Identity and Access Management (IAM) roles, users, and policies.
    c: OS and application configurations: Maintain security of guest operating systems, applications, and firewall configurations.
    d: Network settings: Manage security group rules and network access control lists (NACLs).
    e: Compliance: Ensure compliance with regulations and standards based on data storage and usage.