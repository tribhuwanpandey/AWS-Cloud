# S3 Use cases
- Backup and storage
- Disaster Recovery
- Archive
- Hybrid Cloud storage
- Application hosting
- Media hosting
- Data lakes & big data analytics
- Software delivery
- Static website

## Amazon S3 Overview - Buckets
- Amazon S3 allows people to store objects (files) in “buckets” (directories)
- Buckets must have a globally unique name (across all regions all accounts)
- Buckets are defined at the region level
- S3 looks like a global service but buckets are created in a region

### Naming convention
- No uppercase
- No underscore
- 3-63 characters long
- Not an IP
- Must start with lowercase letter or number

## Amazon S3 Overview - Objects
- Objects (files) have a Key
- The key is the FULL path:  
  `s3://my-bucket/my_file.txt`  
  `s3://my-bucket/my_folder1/another_folder/my_file.txt`
- The key is composed of prefix + object name  
  `s3://my-bucket/my_folder1/another_folder/my_file.txt`
- There’s no concept of “directories” within buckets (although the UI will trick you to think otherwise)
- Just keys with very long names that contain slashes (“/”)
- Object values are the content of the body:
  - Max Object Size is 5TB (5000GB)
  - If uploading more than 5GB, must use “multi-part upload”
- Metadata (list of text key / value pairs – system or user metadata)
- Tags (Unicode key / value pair – up to 10) – useful for security / lifecycle
- Version ID (if versioning is enabled)

## S3 Security
- User based  
  IAM policies - which API calls should be allowed for a specific user from IAM console
- Resource Based  
  Bucket Policies - bucket wide rules from the S3 console - allows cross account  
  Object Access Control List (ACL) – finer grain  
  Bucket Access Control List (ACL) – less common

**Note:** an IAM principal can access an S3 object if  
the user IAM permissions allow it OR the resource policy ALLOWS it  
AND there’s no explicit DENY

- Encryption: encrypt objects in Amazon S3 using encryption keys

## S3 Bucket Policies
- JSON based policies
- Resources: buckets and objects
- Actions: Set of API to Allow or Deny
- Effect: Allow / Deny
- Principal: The account or user to apply the policy to

Use S3 bucket for policy to:  
- Grant public access to the bucket  
- Force objects to be encrypted at upload  
- Grant access to another account (Cross Account)

Example policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": [
        "arn:aws:s3::examplebucket/*"
      ]
    }
  ]
}



## Bucket settings for Block Public Access

- **Block all public access:** On

- **Block public access to buckets and objects granted through new access control lists (ACLS):** On  
- **Block public access to buckets and objects granted through any access control lists (ACLS):** On  
- **Block public access to buckets and objects granted through new public bucket or access point policies:** On  
- **Block public and cross-account access to buckets and objects through any public bucket or access point policies:** On

These settings were created to prevent company data leaks.

If you know your bucket should never be public, leave these on.

Can be set at the account level.

---

# S3 Websites

S3 can host static websites and have them accessible on the www.

The website URL will be:  
`bucket-name.s3-website-AWS-region.amazonaws.com` OR  
`bucket-name.s3-website.AWS-region.amazonaws.com`

If you get a **403 (Forbidden)** error, make sure the bucket policy allows public reads!

---

# S3 - Versioning

- You can version your files in Amazon S3.  
- It is enabled at the bucket level.  
- Same key overwrite will increment the “version”: 1, 2, 3….  
- It is best practice to version your buckets.  
- Protect against unintended deletes (ability to restore a version).  
- Easy roll back to previous version.

**Notes:**  
- Any file that is not versioned prior to enabling versioning will have version “null”.  
- Suspending versioning does not delete the previous versions.

---

# S3 Access Logs

For audit purpose, you may want to log all access to S3 buckets.

- Any request made to S3, from any account, authorized or denied, will be logged into another S3 bucket.  
- That data can be analyzed using data analysis tools…  
- Very helpful to come down to the root cause of an issue, or audit usage, view suspicious patterns, etc…

---

# S3 Replication (CRR & SRR)

- Must enable versioning in source and destination.  
- Cross Region Replication (CRR).  
- Same Region Replication (SRR).  
- Buckets can be in different accounts.  
- Copying is asynchronous.  
- Must give proper IAM permissions to S3.

**Use cases:**  
- CRR: compliance, lower latency access, replication across accounts.  
- SRR: log aggregation, live replication between production and test accounts.
