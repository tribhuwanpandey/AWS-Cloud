# AWS Identity and Federation Services

## AWS STS (Security Token Service)

- Provides **temporary**, limited-privilege credentials to access AWS resources  
- Credentials have a **configurable expiration period**

### Use Cases:
- **Identity Federation**: Use external identity systems (e.g., corporate AD, SAML) and provide STS tokens to access AWS resources  
- **IAM Roles**:
  - **Cross-account access**: Assume roles in another AWS account
  - **Same-account access**: Assume roles within the same account
- **EC2 Role Access**: Provide temporary credentials to EC2 instances to access AWS services (e.g., S3, DynamoDB)

---

## Amazon Cognito

- Manages identity for **web and mobile applications** (supports millions of users)  
- Replaces the need to create IAM users for each application user  
- Supports:
  - User sign-up and sign-in
  - Identity federation (Facebook, Google, SAML)
  - Token-based authentication (JWT)
  - Integration with **AWS STS** for temporary AWS credentials

---

## Microsoft Active Directory (AD)

- Directory service available on Windows Server
- Central database of objects:
  - Users, computers, printers, file shares, security groups
- Centralized user management and access control

---

## AWS Directory Services

### AWS Managed Microsoft AD
- Fully managed Microsoft AD in AWS
- Supports MFA
- Can **establish trust** with on-premises AD

### AD Connector
- **Proxy/gateway** to on-premise AD
- Users remain managed in on-prem AD
- Supports MFA

### Simple AD
- AD-compatible directory managed by AWS
- Lightweight, **does not support trust** with on-premise AD

---

## AWS IAM Identity Center (formerly AWS SSO)

- **Single Sign-On (SSO)** for:
  - **Multiple AWS accounts** via AWS Organizations
  - Business cloud applications (e.g., Salesforce, Box, Microsoft 365)
  - **SAML 2.0**-enabled applications
  - **EC2 Windows instances**

### Identity Providers:
- **Built-in identity store**
- External identity providers via **SAML 2.0**

---

## Summary

| Service                   | Purpose |
|---------------------------|---------|
| **IAM**                   | Identity and Access Management within your AWS account for trusted users |
| **Organizations**         | Manage multiple AWS accounts with centralized control |
| **STS**                   | Provides **temporary credentials** for AWS resource access (used with federated users, roles, and EC2) |
| **Cognito**               | Identity service for **web and mobile apps** – handles user sign-up, sign-in, and tokens |
| **Directory Services**    | Integrate **Microsoft AD** with AWS – includes Managed AD, AD Connector, Simple AD |
| **IAM Identity Center**   | Unified **SSO** access to AWS accounts and **external applications** |

