# VPC & Subnets Primer

## What is a VPC?

**VPC (Virtual Private Cloud)** is a private, isolated network within AWS where you can launch AWS resources.  
- **Regional resource**: Spans across multiple Availability Zones (AZs)

## Subnets

Subnets allow partitioning of your VPC:
- **Public Subnet**: Accessible from the internet (via Internet Gateway)
- **Private Subnet**: Not directly accessible from the internet

## Route Tables

Used to define traffic routing rules **within VPC** and **to/from the internet**.

---

## Internet Gateway (IGW)

- Connects a VPC to the internet.
- Allows instances in public subnets to communicate with the internet.
- Required for public subnets.

## NAT Gateway

- Allows instances in **private subnets** to access the internet (for updates, patches, etc.)
- Blocks unsolicited **inbound traffic**.
- Fully managed by AWS.

---

## NAT Gateway vs NAT Instance

| Attribute             | NAT Gateway                               | NAT Instance |
|-----------------------|-------------------------------------------|--------------|
| **Availability**      | Highly available, redundant across AZs    | Requires failover management |
| **Bandwidth**         | Up to 100 Gbps                            | Depends on instance type |
| **Maintenance**       | Fully managed by AWS                      | You manage OS and software updates |
| **Performance**       | Optimized for NAT traffic                 | Depends on generic AMI |
| **Cost**              | Based on usage, duration, data processed  | Based on instance size and time |
| **Type & Size**       | Fixed offering                            | Customizable |
| **Public IP**         | Requires Elastic IP during creation       | Can assign or change Elastic IP |
| **Private IP**        | Auto-assigned                             | Must be manually assigned |
| **Security Groups**   | Not supported                             | Supported |
| **Network ACLs**      | Supported                                 | Supported |
| **Flow Logs**         | Supported                                 | Supported |
| **Port Forwarding**   | Not supported                             | Custom configuration required |
| **Bastion Server**    | Not supported                             | Can be used as one |
| **Traffic Metrics**   | CloudWatch                                | CloudWatch |
| **Timeout Behavior**  | Sends RST packet                          | Sends FIN packet |
| **IP Fragmentation**  | Partial support (UDP only)                | Full support (UDP, TCP, ICMP) |

---

## Network ACLs & Security Groups

### Network ACL (NACL)
- Stateless firewall at the **subnet level**
- Supports **ALLOW** and **DENY** rules
- Rules apply to **IP addresses**

### Security Groups
- Stateful firewall at the **instance/ENI level**
- Supports **ALLOW** rules only
- Rules can reference **IP addresses** or **other security groups**

### NACL vs Security Group

| Feature               | Security Group                | Network ACL |
|-----------------------|-------------------------------|-------------|
| **Scope**             | Instance/ENI                  | Subnet |
| **Rule Type**         | Allow only                    | Allow & Deny |
| **State**             | Stateful                      | Stateless |
| **Rule Processing**   | All rules evaluated           | Rules processed in order |
| **Default Behavior**  | Must be attached to instance  | Applies to all instances in subnet |

[Read more in AWS Docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html)

---

## VPC Flow Logs

Capture IP traffic data for:
- VPCs
- Subnets
- ENIs (Elastic Network Interfaces)

**Use cases:**
- Troubleshoot traffic issues
- Monitor traffic between:
  - Subnets ↔ Internet
  - Subnets ↔ Subnets
  - Internet ↔ Subnets

**Destinations**: Amazon S3 / CloudWatch Logs

---

## VPC Peering

- Enables **direct, private network** connectivity between two VPCs
- Can be across same or different AWS accounts
- **No overlapping CIDR blocks allowed**
- **Non-transitive** (no traffic routing through intermediary VPCs)

---

## VPC Endpoints

Access AWS services **privately** within your VPC:

- **Interface Endpoint**: For most AWS services
- **Gateway Endpoint**: For S3 and DynamoDB

**Benefits**:
- Improved security
- Lower latency (no internet route)

---

## Hybrid Connectivity

### Site-to-Site VPN
- Connect on-premises network to AWS over the **public internet**
- Encrypted connection
- Requires:
  - **Customer Gateway (CGW)** on-premises
  - **Virtual Private Gateway (VGW)** on AWS

### AWS Direct Connect (DX)
- Establishes a **private**, **dedicated** connection to AWS
- **Bypasses the public internet**
- Takes **~1 month** to establish

---

## AWS Transit Gateway

- Centralized routing hub for:
  - Multiple VPCs
  - On-premises networks
- Highly scalable
- Advanced security and routing features
- Suitable for large, enterprise-scale architectures

---

## VPC Summary

- **VPC**: Isolated cloud network
- **Subnets**: AZ-specific network partitions
- **Internet Gateway**: Enables internet access for public subnets
- **NAT Gateway/Instance**: Enables internet access for private subnets
- **NACLs**: Stateless, subnet-level firewall
- **Security Groups**: Stateful, instance-level firewall
- **VPC Peering**: Private connection between two VPCs
- **Endpoints**: Private access to AWS services
- **Flow Logs**: Track traffic for troubleshooting
- **VPN**: Secure connection over public internet
- **Direct Connect**: Dedicated private connection to AWS
- **Transit Gateway**: Connect thousands of networks centrally

---

## Resources

 AWS Documentation  
 [VPC Security Guide](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html)
