# Elastic Load Balancing & Auto Scaling Groups

---

##  Scalability

**Scalability** is the ability of a system to handle increased load by adapting to demand.

### Types of Scalability:

#### 1. Vertical Scalability (Scale Up / Down)
- Increase the capacity of a single instance.
- Example: `t3.medium` → `t3.large`
-  Suitable for:
  - Databases
  - Applications needing stronger single-instance performance
- ❗ Limited by hardware constraints.

#### 2. Horizontal Scalability (Scale Out / In / Elasticity)
- Add more instances (servers) to distribute the load.
- Achieved using:
  - **Auto Scaling Groups (ASG)**
  - **Elastic Load Balancer (ELB)**
-  Ideal for:
  - Resilient and distributed applications
  - Microservices
- Implies a **distributed system architecture**.

---

##  High Availability (HA)

**High Availability** ensures a system is operational and accessible for the majority of time by minimizing downtime.

### Key Characteristics:
- Deploy resources across **multiple Availability Zones (AZs)**.
- Provides **redundancy and failover**.
- Often goes hand-in-hand with **horizontal scaling**.

---

##  High Availability & Scalability for EC2

| Concept           | Description |
|------------------|-------------|
| **Vertical Scaling** | Increase instance size (e.g., `t2.nano` to `u-12tb1.metal`) |
| **Horizontal Scaling** | Increase number of instances |
| **High Availability** | Run EC2 instances across multiple AZs |

- Use:
  - **Auto Scaling Group (multi-AZ)**
  - **Elastic Load Balancer (multi-AZ)**

---

##  Scalability vs Elasticity vs Agility

| Term         | Definition |
|--------------|------------|
| **Scalability** | Ability to increase/decrease system capacity to handle varying loads. |
| **Elasticity** | Auto-adjust resources in real-time to match load and prevent under/over-provisioning. |
| **Agility** | Ability to deploy/manage resources quickly in response to changing demands. |

---

##  Load Balancing

**Load Balancer** distributes incoming traffic across multiple targets to avoid overwhelming a single resource.

### Why Use Load Balancers?
- Ensures **fault tolerance** & **high availability**
- Performs **health checks**
- Handles **SSL termination (HTTPS)**
- Automatically reroutes traffic if a target fails

---

##  Elastic Load Balancer (ELB)

**ELB** is a fully managed service that:
- Distributes traffic across multiple targets in one or more AZs
- Automatically scales and handles failover
- Provides **limited configuration** but **managed infrastructure**

###  Types of Load Balancers:

| Type                    | Layer | Use Case |
|-------------------------|-------|----------|
| **Application LB (ALB)** | 7     | HTTP/HTTPS traffic |
| **Network LB (NLB)**     | 4     | TCP/UDP high-performance traffic |
| **Classic LB (CLB)**     | 4 & 7 | Legacy use (being retired) |

---

##  Auto Scaling Group (ASG)

**ASG** ensures the right number of EC2 instances are running to handle demand.

### Features:
- Scales based on metrics (e.g., CPU utilization)
- Supports **multi-AZ deployments**
- **Automatically registers** new instances with ELB
- Replaces **unhealthy instances**
- Optimizes **cost** by running only required capacity

### Goals:
-  **Scale Out**: Add instances when load increases
-  **Scale In**: Remove instances when load decreases
-  Maintain **min/max** capacity range

---

## ASG Scaling Strategies

| Strategy             | Description |
|----------------------|-------------|
| **Manual Scaling**       | Manually adjust instance count based on predictions |
| **Dynamic Scaling**      | Automatically scale based on CloudWatch metrics |
| **Simple/Step Scaling**  | Trigger actions via thresholds (e.g., CPU > 70%) |
| **Target Tracking**      | Maintain a target metric (e.g., CPU at 40%) |
| **Scheduled Scaling**    | Scale at specific times (e.g., 5pm every Friday) |
| **Predictive Scaling**   | Use ML to forecast load and scale proactively |

---

##  ELB & ASG Summary

###  Elastic Load Balancer (ELB)
- Distributes traffic across EC2 instances
- Works across multiple AZs
- Performs health checks
- Supports 3 types (ALB, NLB, CLB)

###  Auto Scaling Group (ASG)
- Provides **Elasticity**
- Works across **multiple AZs**
- Scales EC2 instances dynamically
- Replaces unhealthy instances

---
>  Use ELB + ASG for a highly available, fault-tolerant, and scalable cloud architecture.