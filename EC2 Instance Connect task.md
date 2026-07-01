**Below is a project-oriented summary of the AWS blog you referenced. I've organized it in the order you would complete the work in AWS and included the purpose of each step.**

**AWS Blog:** [Secure Connectivity from Public to Private: Introducing EC2 Instance Connect Endpoint](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com)


# Project Goal

Securely connect from your laptop (public Internet) to an EC2 instance in a **private subnet** using an **EC2 Instance Connect Endpoint (EICE)**.

The private EC2 should **not** have:

- ❌ Public IP

- ❌ Bastion Host

- ❌ VPN

- ❌ Internet Gateway for inbound SSH

Instead, AWS provides a managed endpoint that securely proxies the connection after authenticating you with IAM. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


# High-Level Architecture

```
`Your Laptop`

`      │`

` HTTPS (443)`

`      │`

`AWS IAM Authentication`

`      │`

`EC2 Instance Connect Endpoint (EICE)`

`      │`

`Private VPC`

`      │`

`Private EC2 Instance`
```


# Sequential Order to Complete the Project

## Step 1. Create a VPC

**AWS Console**

VPC → Your VPCs → Create VPC

Example

```
`Name:`

`roc-project-vpc`


`CIDR:`

`10.0.0.0/16`
```

Purpose

Creates the isolated network where everything will reside.


## Step 2. Create Two Subnets

### Public Subnet

AWS Console

VPC → Subnets → Create subnet

Example

```
`10.0.0.0/24`
```

Purpose

Hosts the EC2 Instance Connect Endpoint.


### Private Subnet

Create another subnet.

Example

```
`10.0.2.0/24`
```

Purpose

Hosts the private EC2 instance.


## Step 3. Configure Route Tables

### Public Route Table

Associate with

```
`Public subnet`
```

If your architecture requires internet access for other resources, this route table can include an Internet Gateway. **However, for the EICE feature itself, the endpoint provides secure connectivity without requiring the target EC2 instance to have a public IP.** ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


### Private Route Table

Associate with

```
`Private subnet`
```

Route

```
`10.0.0.0/16`

`local`
```

Purpose

Keeps the EC2 private.


## Step 4. Launch EC2

AWS Console

EC2 → Instances → Launch Instance

Configuration

```
`Amazon Linux`


`Private Subnet`


`Public IP:`

`Disabled`
```

Verify after launch

```
`Public IPv4:`

`None`


`Private IPv4:`

`10.x.x.x`
```

Purpose

The instance is reachable only through private networking.


## Step 5. Create Security Groups

### EC2 Security Group

Inbound

```
`SSH`

`TCP 22`

`Source:`

`Security Group of the EICE`
```

Purpose

Only the EC2 Instance Connect Endpoint can initiate SSH to the instance.


### EICE Security Group

Outbound

```
`TCP 22`


`Destination`


`Private EC2`
```

Purpose

Allows the endpoint to forward SSH traffic.


## Step 6. Create EC2 Instance Connect Endpoint

AWS Console

VPC

↓

Endpoints

↓

Create Endpoint

Choose

```
`Endpoint Type`


`EC2 Instance Connect Endpoint`
```

Select

```
`VPC`


`Public Subnet`


`Security Group`
```

Purpose

Creates the managed, IAM-authenticated endpoint that tunnels traffic to your private EC2. Only **one EICE is required per VPC** in most scenarios. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


## Step 7. Configure IAM Permissions

The user connecting must have permissions to:

- Use EC2 Instance Connect

- Connect through the endpoint

- Describe EC2 instances

Purpose

IAM determines **who** can establish a connection before any traffic reaches the VPC. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


## Step 8. Connect to the Private EC2

AWS Console

EC2

↓

Instances

↓

Select instance

↓

Connect

↓

EC2 Instance Connect

↓

Choose

```
`EC2 Instance Connect Endpoint`
```

↓

Connect

Alternatively, you can use the AWS CLI:

```
`aws ec2-instance-connect ssh --instance-id \<instance-id\>`
```

This command generates ephemeral SSH keys and connects through the endpoint. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


## Step 9. Verify Success

Successful verification includes:

- ✅ SSH session opens

- ✅ EC2 has **no public IP**

- ✅ No bastion host used

- ✅ No VPN used

- ✅ Connection authenticated with IAM

- ✅ Traffic flows through the EC2 Instance Connect Endpoint


# Key Concepts

| **Component** | **Purpose** |
| :-: | :-: |
| VPC | Private network |
| Public Subnet | Hosts the EC2 Instance Connect Endpoint |
| Private Subnet | Hosts the EC2 instance |
| Private EC2 | Workload with no public IP |
| EC2 Instance Connect Endpoint | Secure entry point into the VPC |
| IAM | Authenticates and authorizes users |
| Security Groups | Control network traffic |
| Route Tables | Define network routing |


# Security Benefits

Compared to traditional SSH access:

| **Traditional** | **EC2 Instance Connect Endpoint** |
| :-: | :-: |
| Public IP required | No public IP required |
| Bastion host required | No bastion host |
| Long-lived SSH keys common | Supports ephemeral SSH keys |
| Limited identity controls | IAM-based authentication |
| Extra servers to maintain | AWS-managed endpoint |
| Limited auditing | CloudTrail logs connection activity |


# Common Issues

If you receive:

> **WebSocket Closure Reason: Unable to connect to target**

check the following in order:

1. EC2 is **Running**.

2. EC2 has **only a private IP**.

3. EC2 security group allows **TCP 22** from the EICE security group.

4. The EICE and EC2 are in the **same VPC**.

5. The EICE can route to the EC2's subnet.

6. Your IAM user or role has permission to use the EC2 Instance Connect Endpoint. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))


## Final Deliverable

By the end of the project, you should be able to demonstrate:

- A private EC2 instance with **no public IP address**.

- An **EC2 Instance Connect Endpoint** in the same VPC.

- Successful SSH access from your laptop to the private EC2 through the endpoint.

- IAM-based authentication and security-group-controlled access without exposing SSH directly to the internet. This is the core outcome demonstrated in the AWS reference architecture. ([Amazon Web Services, Inc.](https://aws.amazon.com/blogs/compute/secure-connectivity-from-public-to-private-introducing-ec2-instance-connect-endpoint-june-13-2023//?utm_source=chatgpt.com))

