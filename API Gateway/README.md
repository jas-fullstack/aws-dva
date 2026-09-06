# 🔐 AWS IAM (Identity and Access Management) – Notes

IAM is a global AWS service used to securely control access to AWS resources.

---

# 📌 What is IAM?

IAM allows you to:
- Manage users and their access
- Control permissions
- Secure AWS resources
- Implement least privilege principle

IAM is global (not region-specific).

---

# 🧱 Core IAM Components

## 1️⃣ Users
- Represents a person or application
- Can have:
  - Console password
  - Access keys (CLI / SDK)

⚠️ Avoid using root user for daily tasks.

---

## 2️⃣ Groups
- Collection of users
- Permissions attached to group
- Users inherit permissions

Note:
- A user can belong to multiple groups
- Groups cannot contain other groups

---

## 3️⃣ Roles (Very Important for SAA)

- Used for temporary access
- No long-term credentials
- Assumed by:
  - EC2
  - Lambda
  - Cross-account users
  - Federation

Example:
EC2 → Assume Role → Access S3 securely

---

## 4️⃣ Policies

JSON document defining permissions.

### Types:
- AWS Managed Policy
- Customer Managed Policy
- Inline Policy

---

# 📜 IAM Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*",
      "Condition": {}
    }
  ]
}
```
## What is difference between IAM user and role?

## What is policy evaluation logic?

## When do we use resource-based policy?

## What is STS?

## Why are roles preferred over access keys?

## What does Explicit Deny do?

