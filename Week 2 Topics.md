Absolutely. Since you're learning AWS and Linux together, I'll teach these concepts the way I teach new cloud engineers: **start with the "why," then the "what," then the "how," and finally how everything works together.**


# AWS Security Deep Dive

AWS security is built on one core principle:

> **Give only the permissions needed, only when needed, only to the right identity.**

This is called the **Principle of Least Privilege**.

Everything below supports that principle.


# 1. IAM (Identity and Access Management)

## Definition

IAM is the AWS service used to **control who can do what inside an AWS account**.

Think of IAM as the **security guard** at a company.

It answers questions like:

- Who are you?

- What resources can you access?

- What actions can you perform?

IAM manages:

- Users

- Groups

- Roles

- Policies


## Why use IAM?

Without IAM:

- Everyone could delete EC2 instances.

- Anyone could access S3 buckets.

- There would be no security.

IAM lets you control permissions precisely.


## When do you use IAM?

Almost always.

Examples:

- Developers need EC2 access.

- Administrators need full AWS access.

- Applications need permission to read S3.

- Lambda functions need DynamoDB access.


## How does IAM work?

Example:

```
`Andre`

`   │`

`   ▼`

`IAM User`

`   │`

`Attached Policy`

`   │`

`Allows:`

`Start EC2`

`Stop EC2`

`Read S3`
```

IAM evaluates every request.

If permission exists:

✅ Allow

Otherwise:

❌ Deny


## IAM Components

### Users

Represents one person.

Example:

```
`Andre`

`Jessica`

`Admin`
```


### Groups

Collection of users.

Example:

```
`Developers`


`contains`


`Andre`

`Jessica`

`David`
```

Everyone inherits the group's permissions.


### Policies

JSON documents describing permissions.

Example

```
`\{`

` "Effect":"Allow",`

` "Action":"s3:GetObject",`

` "Resource":"\*"`

`\}`
```


### Roles

Temporary identities used by:

- EC2

- Lambda

- ECS

- Cross-account access

Roles do **not** have passwords.


# Use Case

A developer needs read-only access to CloudWatch.

Solution:

```
`IAM User`

`↓`


`CloudWatch ReadOnly Policy`
```


# IAM Deep Dive

There are two major authorization models.


# RBAC (Role-Based Access Control)

## Definition

Permissions are assigned based on **job role**.

Example:

```
`Database Administrator`


`↓`


`Database Permissions`
```

Not based on the individual.


## Why use RBAC?

Easy to manage.

Instead of configuring 500 employees individually,

you create:

```
`Developer Role`


`Manager Role`


`Administrator Role`
```

Assign users to roles.


## When to use RBAC?

Organizations with:

- fixed departments

- stable responsibilities

- predictable permissions


## Example

```
`Developers`


`Can`


`Launch EC2`

`Read CloudWatch`


`Cannot`


`Delete VPC`
```


## AWS Example

```
`IAM Group`


`Developers`


`↓`


`EC2FullAccess`

`CloudWatchReadOnly`
```


# Use Case

Company hires 20 new developers.

Simply add them to:

```
`Developer Group`
```

Done.


# ABAC (Attribute-Based Access Control)

## Definition

Permissions are granted using **attributes (tags)** instead of roles.


Example

User

```
`Department = Finance`
```

EC2 Instance

```
`Department = Finance`
```

Policy

```
`Only access matching department.`
```


## Why use ABAC?

Perfect for large organizations.

Instead of hundreds of roles,

AWS compares tags.


## When to use?

Large enterprise

Thousands of users

Many departments

Dynamic workloads


## Example

Employee

```
`Department = HR`
```

Can only access

```
`Department = HR`
```

resources.


## AWS Tags

```
`Department=Finance`


`Environment=Production`


`Project=Payroll`
```


## Use Case

Company has

1000 employees

Instead of

1000 IAM roles

Use:

```
`Department Tags`
```

AWS automatically matches permissions.


# RBAC vs ABAC

| **RBAC** | **ABAC** |
| :-: | :-: |
| Role based | Tag based |
| Easier | More scalable |
| Good for small companies | Good for enterprises |
| Fixed permissions | Dynamic permissions |
| Uses groups and roles | Uses tags |


# STS (Security Token Service)

## Definition

STS creates **temporary AWS credentials**.

Instead of permanent passwords,

AWS creates credentials that expire.


## Why use STS?

Permanent credentials are dangerous.

Temporary credentials reduce risk.


## When?

- EC2

- Lambda

- Cross-account access

- CI/CD

- SSO


## How?

```
`IAM Role`


`↓`


`STS`


`↓`


`Temporary Credentials`


`↓`


`Expire`
```


Temporary credentials contain

```
`Access Key`


`Secret Key`


`Session Token`
```


## Use Case

Developer needs production access for one hour.

STS issues credentials.

After one hour

They automatically expire.


# Temporary Credentials

## Definition

Credentials that expire automatically.

Unlike IAM access keys,

they are not permanent.


## Why?

Reduces risk.

If stolen,

they become useless after expiration.


## Example

```
`Valid`


`9 AM`


`↓`


`Expires`


`10 AM`
```


## Use Case

GitHub Actions deployment.

Pipeline gets credentials for

15 minutes.

Deploys.

Credentials disappear.


# Secrets Manager

## Definition

Stores sensitive information securely.

Examples:

- Database passwords

- API keys

- OAuth tokens

- SSH keys


## Why?

Never store passwords inside code.

Bad:

```
`password="admin123"`
```

Good

```
`Secrets Manager`


`↓`


`Retrieve password securely`
```


## When?

Applications

Lambda

Containers

Databases


## Automatic Rotation

Secrets Manager can automatically rotate passwords.

Example

Old password

↓

New password

↓

Application updated


## Use Case

Application connects to RDS.

Instead of storing

```
`DB Password`
```

inside code,

retrieve it from Secrets Manager.


# KMS (Key Management Service)

## Definition

Creates and manages encryption keys.


## Why?

Encryption protects data.

KMS manages the encryption keys safely.


## When?

Encrypt:

- S3

- EBS

- RDS

- Secrets Manager

- Lambda Environment Variables


## How?

```
`File`


`↓`


`Encrypted`


`↓`


`KMS Key`


`↓`


`Ciphertext`
```


## Use Case

Encrypt an S3 bucket containing payroll data.


# Zero Trust Access

## Definition

Never trust anyone automatically.

Always verify.


Traditional Security

```
`Inside network`


`↓`


`Trusted`
```

Zero Trust

```
`Verify`


`Every request`


`Every identity`


`Every time`
```


## Why?

Hackers often gain internal access.

Being "inside" doesn't mean trusted.


## AWS Example

Developer wants EC2 access.

AWS checks

- IAM permissions

- MFA

- Device

- Session

- Role

Every request.


## Use Case

Employee connects from home.

AWS still verifies identity before allowing access.


# DevOps Mapping


## CI/CD Roles Assume Permissions

Instead of storing AWS credentials,

Pipeline assumes an IAM Role.

```
`GitHub Actions`


`↓`


`Assume Role`


`↓`


`STS`


`↓`


`Temporary Credentials`


`↓`


`Deploy`
```

Why?

No permanent credentials.


## No Hardcoded Credentials

Bad

```
`AWS\_SECRET\_KEY="123456"`
```

Good

```
`Application`


`↓`


`Secrets Manager`


`↓`


`Retrieve Secret`
```


## Secure Pipeline Execution

Secure CI/CD pipeline

```
`Developer`


`↓`


`GitHub`


`↓`


`GitHub Actions`


`↓`


`Assume IAM Role`


`↓`


`STS`


`↓`


`Temporary Credentials`


`↓`


`Secrets Manager`


`↓`


`Deploy to AWS`


`↓`


`KMS Encrypts Data`
```


# Complete Relationship Table

| **Term** | **Purpose** | **Uses** | **Works With** | **Typical User Case** |
| :-: | :-: | :-: | :-: | :-: |
| IAM | Identity and permissions | Control access | Roles, Policies, STS | Give developers EC2 access |
| RBAC | Role-based authorization | Permissions by job role | IAM | Developers, Admins, DBAs |
| ABAC | Tag-based authorization | Dynamic access | IAM Tags | Large enterprises with many departments |
| STS | Temporary credentials | Secure short-term access | IAM Roles | CI/CD, EC2, cross-account access |
| Temporary Credentials | Short-lived AWS credentials | Replace long-term keys | STS | GitHub Actions deployment |
| Secrets Manager | Secure secret storage | Passwords, API keys | KMS | Store RDS database credentials |
| KMS | Encryption key management | Encrypt AWS resources | Secrets Manager, S3, EBS, RDS | Encrypt sensitive data at rest |
| Zero Trust Access | Security model | Verify every request | IAM, STS, MFA, KMS | Remote employee access |
| CI/CD Role Assumption | Secure deployments | Pipeline authentication | IAM Roles + STS | GitHub Actions deploys to AWS |
| No Hardcoded Credentials | Security best practice | Protect secrets | Secrets Manager | Applications retrieve passwords securely |
| Secure Pipeline Execution | End-to-end secure deployment | Automated deployments | IAM, STS, Secrets Manager, KMS | Production application deployment |


# How Everything Works Together (Real-World Scenario)

Imagine your team deploys a web application to AWS using GitHub Actions.

```
`Developer`

`    │`

`    ▼`

`Pushes code to GitHub`

`    │`

`    ▼`

`GitHub Actions (CI/CD)`

`    │`

`    ▼`

`Assumes an IAM Role`

`    │`

`    ▼`

`STS issues Temporary Credentials (valid for 15–60 minutes)`

`    │`

`    ▼`

`Pipeline retrieves database password from Secrets Manager`

`    │`

`    ▼`

`Secrets Manager uses KMS to protect the secret at rest`

`    │`

`    ▼`

`Pipeline deploys the application to EC2 or ECS`

`    │`

`    ▼`

`IAM policies (using RBAC or ABAC) determine what resources can be accessed`

`    │`

`    ▼`

`Zero Trust principles continuously verify identity and permissions throughout the process`
```

This illustrates how these services are complementary rather than competing:

- **IAM** decides **who** is allowed.

- **RBAC/ABAC** decide **how permissions are organized**.

- **STS** provides **temporary credentials** instead of long-lived ones.

- **Secrets Manager** securely stores **sensitive values** like passwords and API keys.

- **KMS** encrypts those secrets and other AWS resources.

- **Zero Trust** is the overarching security philosophy that requires continuous verification.

- **CI/CD** ties them together to build a secure, automated deployment pipeline without exposing credentials.

