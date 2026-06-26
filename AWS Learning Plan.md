**AWS DevOps Learning Path**


| **Outcome** **By the end of this path, you should be able to design, build, automate, secure, and operate production-grade AWS systems using DevOps principles.** |
| - |

# How to Use This Plan

| **Bullet point** | **Answer / learning target** | **Resources** |
| - | - | - |
| **Foundation & Governance** | **Learn how AWS accounts, organizations, identity, guardrails, and logging form the enterprise foundation before workloads are deployed.** | [AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html)**; **[Building a landing zone](https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-aws-environment/building-landing-zones.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Infrastructure & Networking** | **Learn how VPCs, routing, DNS, private endpoints, and hybrid connectivity create a secure network platform for applications.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)**; **[Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html)**; **[AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) |
| **Compute & Application Platforms** | **Learn when to use VMs, containers, Kubernetes, and serverless so each workload lands on the right runtime.** | [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)**; **[Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)**; **[AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| **DevOps & Automation** | **Build repeatable CI/CD, Infrastructure as Code, release, rollback, patching, and operational workflows.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)**; **[AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |
| **Observability, Security & Reliability** | **Instrument systems with logs, metrics, traces, audit trails, compliance checks, threat detection, and recovery automation.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[Choosing AWS security services](https://docs.aws.amazon.com/decision-guides/latest/security-on-aws-how-to-choose/choosing-aws-security-services.html) |
| **CI/CD pipelines** | **Treat build, test, scan, deploy, and rollback as versioned automation rather than manual console steps.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)**; **[AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| **Infrastructure as Code** | **Define accounts, networks, IAM, compute, data, and monitoring in code so environments can be reviewed and recreated.** | [Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)**; **[AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |
| **Container orchestration** | **Package services into images and let ECS or EKS schedule, scale, update, and recover them.** | [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)**; **[Docker getting started](https://docs.docker.com/get-started/) |
| **Monitoring & incident response** | **Use metrics, logs, traces, alarms, audit events, and runbooks to detect and resolve production issues.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Security & compliance automation** | **Continuously detect drift, secrets exposure, vulnerable workloads, and policy violations before they become incidents.** | [AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)**; **[Amazon GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html)**; **[AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html) |


# Suggested 4-Week Flow

| **Week** | **Focus** | **Deliverable** |
| - | - | - |
| **Week 1** | **Governance, identity, networking, and account structure.** | **Create a simple multi-account design with IAM roles, central logging, and VPC layout.** |
| **Week 2** | **Compute, storage, databases, and event-driven architecture.** | **Deploy a small app using one compute option, one data store, and one async integration.** |
| **Week 3** | **CI/CD, IaC, containers, Kubernetes, and release strategies.** | **Build a pipeline that provisions infrastructure and deploys a containerized service.** |
| **Week 4** | **Observability, security operations, migration, and cost optimization.** | **Add dashboards, alarms, vulnerability checks, cost review, and a runbook.** |


# Detailed Learning Plan

## 1. Foundation & Multi-Account Governance

| **Goal** **Understand how enterprises structure AWS.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **AWS Global Infrastructure** | **Know Regions, Availability Zones, edge locations, and how they shape latency, resilience, data residency, and DR choices.** | [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Multi-account strategy** | **Use separate accounts for isolation, billing boundaries, blast-radius reduction, delegated ownership, and environment separation.** | [AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html)**; **[AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) |
| **Landing Zone design** | **Create a governed starting point with core accounts, network, identity, centralized logging, and security controls.** | [Building a landing zone](https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-aws-environment/building-landing-zones.html)**; **[AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html) |
| **Governance & guardrails** | **Use preventive and detective controls to keep teams fast while limiting risky configurations.** | [AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html)**; **[AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **AWS Organizations** | **Manages multiple AWS accounts, consolidated billing, organizational units, and service control policies.** | [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) |
| **AWS Control Tower** | **Automates a governed landing zone and account vending based on AWS multi-account best practices.** | [AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html)**; **[AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html) |
| **IAM Identity Center** | **Centralizes workforce access to AWS accounts and applications with permission sets and SSO.** | [IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Separate accounts for Dev / QA / Prod** | **Create clean environment boundaries so deployment failures, permissions, and cost attribution do not bleed across stages.** | [AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html)**; **[AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html) |
| **Centralized security + logging** | **Send CloudTrail, Config, and service logs to protected security/log archive accounts for audit and incident response.** | [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)**; **[AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html) |


## 2. Identity, Security & Compliance

| **Goal** **Secure everything by design.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **IAM deep dive (RBAC, ABAC)** | **Master policies, roles, permission boundaries, tags, and least privilege so access can scale safely.** | [AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) |
| **Temporary credentials (STS)** | **Prefer short-lived assumed-role credentials over static keys, especially for pipelines and automation.** | [Temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html) |
| **Secrets management** | **Store, rotate, audit, and retrieve application secrets without hardcoding them in repositories or build logs.** | [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)**; **[AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) |
| **Zero trust access** | **Require explicit identity, least privilege, short-lived credentials, private paths, and continuous verification.** | [AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)**; **[IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)**; **[Choosing AWS security services](https://docs.aws.amazon.com/decision-guides/latest/security-on-aws-how-to-choose/choosing-aws-security-services.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **IAM** | **Defines users, groups, roles, and policies for AWS access control.** | [AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) |
| **STS** | **Issues temporary security credentials for assumed roles and federated identities.** | [Temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html) |
| **Secrets Manager** | **Stores and rotates secrets such as database credentials, API keys, and tokens.** | [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) |
| **KMS** | **Creates and manages encryption keys used across AWS services and custom applications.** | [AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **CI/CD roles assume permissions** | **Let deployment systems assume scoped roles per account/environment instead of storing long-lived access keys.** | [Temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)**; **[AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) |
| **No hardcoded credentials** | **Pull secrets at runtime from managed stores and scan repositories/pipelines for accidental exposure.** | [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)**; **[AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) |
| **Secure pipeline execution** | **Give each pipeline stage only the permissions it needs and log every deployment action for auditability.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) |


## 3. Networking & Hybrid Architecture

| **Goal** **Build enterprise network architecture.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **VPC design (Hub-Spoke)** | **Use a central connectivity VPC or transit hub with separate workload VPCs for isolation and shared routing.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)**; **[Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html) |
| **Private vs Public workloads** | **Place only edge-facing components in public subnets; keep app, data, runners, and admin paths private.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)**; **[AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) |
| **Hybrid connectivity** | **Connect AWS and on-premises networks through VPN, Direct Connect, and Transit Gateway patterns.** | [Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html)**; **[Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **VPC** | **Provides isolated networking, subnets, route tables, gateways, network ACLs, and security groups.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| **Transit Gateway** | **Connects VPCs and on-premises networks through a scalable hub.** | [Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html) |
| **PrivateLink** | **Privately exposes services across VPCs and accounts without public internet paths.** | [AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) |
| **Route 53** | **Provides DNS, routing policies, health checks, and domain registration.** | [Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Private CI/CD runners** | **Run build agents in private subnets with controlled egress and private access to internal services.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)**; **[AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) |
| **Secure service-to-service communication** | **Use private endpoints, security groups, DNS, and encryption to keep east-west traffic controlled.** | [AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)**; **[Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)**; **[Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |


## 4. Compute & Application Hosting Models

| **Goal** **Choose the right runtime.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **VM-based -\> EC2** | **Use EC2 when you need OS-level control, custom agents, specialized networking, or lift-and-shift compatibility.** | [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)**; **[EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| **Container-based -\> ECS/EKS** | **Use containers for packaged services, repeatable deployments, service scaling, and microservices.** | [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)**; **[Docker getting started](https://docs.docker.com/get-started/) |
| **Serverless -\> Lambda** | **Use Lambda for event-driven functions, background jobs, APIs, and automation that should scale without server management.** | [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)**; **[Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **EC2 + Auto Scaling** | **Runs virtual machines and adjusts capacity based on demand or schedules.** | [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)**; **[EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| **ALB/NLB** | **Distributes HTTP/HTTPS or TCP/UDP traffic across targets and supports health-based routing.** | [Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html) |
| **ECS / EKS** | **Runs containers through AWS-native orchestration or managed Kubernetes.** | [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) |
| **Lambda** | **Runs code on demand for events without provisioning servers.** | [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Blue/Green deployments** | **Deploy a new version beside the current one, test it, then shift traffic for low-risk release.** | [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)**; **[ECS blue/green deployment](https://aws.amazon.com/blogs/devops/blue-green-deployments-to-amazon-ecs-using-aws-cloudformation-and-aws-codedeploy/) |
| **Auto-scaling apps** | **Scale EC2, ECS, EKS, or Lambda-backed workloads based on metrics and demand.** | [EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)**; **[Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| **Immutable infrastructure** | **Replace servers or containers with new versions instead of patching production hosts in place.** | [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)**; **[AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)**; **[Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) |


## 5. Storage & Data Strategy

| **Goal** **Understand persistence and performance.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **Object vs Block vs File** | **Use object storage for durable objects, block storage for low-latency disks, and file storage for shared filesystems.** | [Block vs file vs object](https://aws.amazon.com/compare/the-difference-between-block-file-object-storage/)**; **[Choosing AWS storage](https://docs.aws.amazon.com/decision-guides/latest/storage-on-aws-how-to-choose/choosing-aws-storage-service.html) |
| **Backup & disaster recovery** | **Automate backup policies, cross-account/cross-region copies, restore testing, and retention rules.** | [AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Data lifecycle** | **Move data between storage classes, expire old data, and align retention with compliance and cost targets.** | [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)**; **[Choosing AWS storage](https://docs.aws.amazon.com/decision-guides/latest/storage-on-aws-how-to-choose/choosing-aws-storage-service.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **S3** | **Durable object storage for artifacts, logs, backups, websites, data lakes, and lifecycle-managed data.** | [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) |
| **EBS / EFS** | **EBS provides block volumes for EC2; EFS provides shared elastic file storage across instances.** | [Amazon EBS](https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html)**; **[Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html) |
| **FSx** | **Managed high-performance file systems such as Windows File Server, Lustre, NetApp ONTAP, and OpenZFS.** | [Amazon FSx](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/what-is.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Artifact storage (S3)** | **Store build artifacts, deployment bundles, logs, Terraform state, and release assets in versioned buckets.** | [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| **Backup automation** | **Define backup plans as policy, monitor job success, and test restores regularly.** | [AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html) |
| **Log storage** | **Centralize application, access, audit, and infrastructure logs for investigation and compliance.** | [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)**; **[Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |


## 6. Databases & Data Layer

| **Goal** **Managed database operations.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **HA design (Multi-AZ)** | **Use Multi-AZ deployments for automatic failover and availability across Availability Zones.** | [RDS Multi-AZ](https://aws.amazon.com/rds/features/multi-az/)**; **[Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html) |
| **Read scaling** | **Use read replicas or distributed/cached data patterns to handle read-heavy workloads.** | [RDS Read Replicas](https://aws.amazon.com/rds/features/read-replicas/)**; **[Amazon ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.html) |
| **NoSQL vs SQL** | **Use SQL for relational consistency/querying; use NoSQL for key-value/document access at massive scale and flexible schemas.** | [Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)**; **[Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **RDS / Aurora** | **Managed relational databases with backups, patching, replication, and high availability options.** | [Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)**; **[Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html) |
| **DynamoDB** | **Serverless NoSQL database for key-value and document workloads with high scale and low latency.** | [Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html) |
| **ElastiCache** | **Managed Redis or Memcached-compatible caching to reduce database load and latency.** | [Amazon ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Automated backups** | **Use native automated backups, snapshots, point-in-time recovery, and backup policy compliance.** | [Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)**; **[AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html) |
| **DB migration pipelines** | **Use repeatable schema/data migration steps, DMS when needed, and deployment gates for database changes.** | [AWS DMS](https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |


## 7. Serverless & Event-Driven Architecture

| **Goal** **Build loosely coupled systems.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **Event-driven design** | **Model systems as producers and consumers of events so services can evolve independently.** | [Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)**; **[AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| **Async communication** | **Use queues, topics, and workflows to buffer work, absorb spikes, and decouple failure domains.** | [Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)**; **[Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)**; **[AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **Lambda** | **Runs event handlers, API backends, file processors, and automation functions.** | [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| **API Gateway** | **Publishes, secures, throttles, and monitors REST, HTTP, and WebSocket APIs.** | [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html) |
| **SQS / SNS** | **SQS queues work for reliable processing; SNS fans messages out to subscribers.** | [Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)**; **[Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) |
| **EventBridge** | **Routes events from AWS services, SaaS apps, and custom applications.** | [Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html) |
| **Step Functions** | **Coordinates multi-step workflows, retries, branching, and human or service tasks.** | [AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Event-triggered pipelines** | **Start automation from code, security, data, or operational events instead of manual handoffs.** | [Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| **Microservices communication** | **Use events, queues, APIs, and workflows to avoid tight service coupling.** | [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)**; **[Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)**; **[Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html) |


## 8. DevOps & Automation

| **Goal** **Make delivery repeatable, secure, and observable.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **CI/CD pipelines** | **Automate build, test, scan, deploy, approval, and rollback steps for every application.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)**; **[AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| **Infrastructure as Code** | **Version and review cloud resources the same way you review application code.** | [Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)**; **[AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |
| **GitOps** | **Use Git as the source of truth for desired state and reconcile environments from approved changes.** | [OpenGitOps principles](https://opengitops.dev/)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) |
| **Release strategies** | **Use rolling, blue/green, canary, and feature-flag approaches to lower deployment risk.** | [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)**; **[ECS blue/green deployment](https://aws.amazon.com/blogs/devops/blue-green-deployments-to-amazon-ecs-using-aws-cloudformation-and-aws-codedeploy/) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **CodePipeline / CodeBuild / CodeDeploy** | **AWS-native CI/CD services for orchestration, builds/tests, and deployments.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)**; **[AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| **Terraform** | **Popular multi-cloud IaC tool with an AWS provider and strong module ecosystem.** | [Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) |
| **CloudFormation** | **AWS-native declarative IaC service for provisioning AWS resources.** | [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |
| **Systems Manager** | **Automates patching, run commands, parameter storage, fleet visibility, and operational tasks.** | [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Build -\> Test -\> Deploy pipeline** | **Build once, test automatically, scan artifacts, deploy through environments, and keep audit history.** | [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)**; **[AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |
| **Blue/Green & Canary deployments** | **Shift traffic gradually or all at once after validation, while preserving a fast rollback path.** | [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)**; **[ECS blue/green deployment](https://aws.amazon.com/blogs/devops/blue-green-deployments-to-amazon-ecs-using-aws-cloudformation-and-aws-codedeploy/) |
| **Automated rollback** | **Use health checks, alarms, deployment hooks, and previous versions to recover quickly.** | [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)**; **[Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html) |


## 9. Containers & Kubernetes

| **Goal** **Deploy modern containerized workloads.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **Docker fundamentals** | **Understand images, Dockerfiles, registries, tags, layers, and local container workflows.** | [Docker getting started](https://docs.docker.com/get-started/)**; **[Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html) |
| **Container orchestration** | **Learn how schedulers place containers, restart failed tasks, scale services, and manage networking.** | [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) |
| **Service mesh basics** | **Understand traffic policy, mutual TLS, retries, observability, and service-to-service controls.** | [Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **ECR** | **Private managed container image registry integrated with IAM and vulnerability scanning.** | [Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html) |
| **ECS / Fargate** | **AWS-native container orchestration with optional serverless compute through Fargate.** | [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html) |
| **EKS** | **Managed Kubernetes control plane for teams standardizing on Kubernetes APIs and ecosystem tools.** | [Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **Microservices deployment** | **Build images, push to ECR, deploy services, expose through load balancers, and monitor health.** | [Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html)**; **[Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html) |
| **CI/CD to Kubernetes** | **Promote images and manifests through environments with tests, policy checks, and rollout controls.** | [Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| **Helm + GitOps** | **Package Kubernetes releases with Helm and apply desired state through Git-driven automation.** | [Helm documentation](https://helm.sh/docs/)**; **[OpenGitOps principles](https://opengitops.dev/)**; **[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) |


## 10. Observability & Monitoring

| **Goal** **Operate production systems.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **Metrics, logs, traces** | **Collect the three core telemetry types so you can see symptoms, request paths, and root causes.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[Amazon Managed Prometheus](https://docs.aws.amazon.com/prometheus/latest/userguide/what-is-Amazon-Managed-Service-Prometheus.html)**; **[Amazon Managed Grafana](https://docs.aws.amazon.com/grafana/latest/userguide/what-is-Amazon-Managed-Service-Grafana.html) |
| **Alerting** | **Convert service-level symptoms into actionable alarms with clear ownership and runbooks.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Incident response** | **Use dashboards, audit trails, alarms, and runbooks to triage, mitigate, and learn from events.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **CloudWatch** | **Collects metrics, logs, alarms, dashboards, events, and application signals.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html) |
| **CloudTrail** | **Records account activity and API calls for audit, investigation, and compliance.** | [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| **AWS Config** | **Tracks resource configuration history and evaluates compliance rules.** | [AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html) |
| **Managed Prometheus / Grafana** | **Provides managed metrics collection and visualization for cloud-native observability.** | [Amazon Managed Prometheus](https://docs.aws.amazon.com/prometheus/latest/userguide/what-is-Amazon-Managed-Service-Prometheus.html)**; **[Amazon Managed Grafana](https://docs.aws.amazon.com/grafana/latest/userguide/what-is-Amazon-Managed-Service-Grafana.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **SLA monitoring** | **Track user-facing availability, latency, error rates, and saturation against agreed targets.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[Amazon Managed Grafana](https://docs.aws.amazon.com/grafana/latest/userguide/what-is-Amazon-Managed-Service-Grafana.html) |
| **Root cause analysis** | **Correlate deployment events, logs, metrics, traces, and CloudTrail activity.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| **Auto-remediation** | **Trigger Systems Manager, Lambda, or Step Functions from alarms/events to fix known failure modes.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)**; **[AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |


## 11. Security Operations (SecDevOps)

| **Goal** **Continuous security.** |
| - |

### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **GuardDuty** | **Threat detection for suspicious account, workload, network, and data activity.** | [Amazon GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html) |
| **Inspector** | **Automated vulnerability management for EC2, container images, and Lambda functions.** | [Amazon Inspector](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html) |
| **Security Hub** | **Aggregates findings, checks security standards, and centralizes security posture.** | [AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html) |
| **WAF / Shield** | **WAF filters web requests; Shield provides DDoS protection for internet-facing applications.** | [AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html)**; **[AWS Shield](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html) |


### DevOps Mapping

| **Bullet point** | **How it applies in DevOps** | **Resources** |
| - | - | - |
| **DevSecOps pipelines** | **Shift security left with IaC checks, image scans, secrets checks, and deployment gates.** | [Amazon Inspector](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html)**; **[AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| **Vulnerability scanning** | **Continuously scan images, functions, and instances and route findings to owners.** | [Amazon Inspector](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html)**; **[Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html) |
| **Compliance automation** | **Use Config and Security Hub standards to detect drift and report policy compliance.** | [AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)**; **[AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html) |


## 12. Migration, Cost & Optimization

| **Goal** **Enterprise efficiency.** |
| - |

### Topics

| **Bullet point** | **Answer / what to learn** | **Resources** |
| - | - | - |
| **Migration strategies (7 Rs)** | **Assess whether to retire, retain, rehost, relocate, repurchase, replatform, or refactor each workload.** | [AWS migration strategies](https://docs.aws.amazon.com/prescriptive-guidance/latest/large-migration-guide/migration-strategies.html) |
| **Cost optimization** | **Measure spend, tag resources, right-size capacity, remove waste, and use commitment discounts carefully.** | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)**; **[AWS Savings Plans](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html)**; **[AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| **Performance tuning** | **Tune compute, database, storage, caching, networking, and concurrency based on measured bottlenecks.** | [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html)**; **[Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html) |


### Key Services

| **Bullet point** | **Answer / what it does** | **Resources** |
| - | - | - |
| **DMS** | **Migrates databases to AWS with minimal downtime for supported engines.** | [AWS DMS](https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html) |
| **Migration Hub** | **Tracks migration progress across applications and tools.** | [AWS Migration Hub](https://docs.aws.amazon.com/migrationhub/latest/ug/whatishub.html) |
| **Cost Explorer** | **Analyzes historical and forecasted AWS cost and usage.** | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| **Savings Plans** | **Provides discounted compute pricing in exchange for committed hourly spend.** | [AWS Savings Plans](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html) |


# Capstone Project

| **Component** | **What to build** | **Resources** |
| - | - | - |
| **Foundation** | **Use a dev/prod account pattern, central logging, IAM Identity Center access, and least-privilege deployment roles.** | [AWS multi-account strategy](https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html)**; **[IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)**; **[AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) |
| **Network** | **Deploy a VPC with public/private subnets, load balancer ingress, private app/data subnets, and clear routing.** | [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)**; **[Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)**; **[AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) |
| **Application** | **Containerize a small web app, push it to ECR, and deploy it to ECS Fargate or EKS.** | [Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html)**; **[Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)**; **[AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html) |
| **Automation** | **Provision infrastructure with Terraform or CloudFormation and deploy through a CI/CD pipeline.** | [Terraform AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)**; **[AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)**; **[AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| **Operations** | **Add CloudWatch dashboards, alarms, CloudTrail auditing, Config rules, Inspector scans, and rollback steps.** | [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)**; **[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)**; **[AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)**; **[Amazon Inspector](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html) |
| **Cost** | **Tag resources, review Cost Explorer, and document one right-sizing or cleanup action.** | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)**; **[AWS Savings Plans](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html) |

