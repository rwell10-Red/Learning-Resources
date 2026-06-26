# **1. AWS Global Infrastructure**

## **Definition**

AWS Global Infrastructure is the worldwide physical and network foundation that powers all AWS services. It includes **Regions**, **Availability Zones**, **Local Zones**, **Edge Locations**, and **Wavelength Zones**, all interconnected by the AWS global backbone network.

## **Why**

- Ensure **high availability** through AZ isolation

- Provide **low latency** to global users

- Meet **data residency** and compliance requirements

- Enable **global-scale** applications and DR strategies

## **When**

- Designing **multi‑AZ** or **multi‑Region** architectures

- Deploying workloads with **global users**

- Building **DR/BCP** strategies

- Meeting **regulatory** or **sovereignty** requirements

## **How**

1. Choose Regions based on latency, compliance, and service availability

2. Deploy workloads across **multiple AZs**

3. Use **CloudFront**, **Route 53**, and **Global Accelerator** for global performance

4. Use **Local Zones** for ultra‑low latency

5. Use **Wavelength** for 5G edge computing

## **Diagram Option A — Clean Hierarchy**

Code

```
`AWS GLOBAL INFRASTRUCTURE`

`│`

`├── Regions (e.g., us-east-1, eu-west-1)`

`│     ├── Availability Zones (AZ1, AZ2, AZ3)`

`│     ├── Local Zones`

`│     └── Wavelength Zones`

`│`

`└── Edge Network`

`      ├── CloudFront Edge Locations`

`      ├── Regional Edge Caches`

`      └── Route 53 DNS Network`
```

## **Diagram Option B — Flow Architecture**

Code

```
`Users → Edge Locations → Regions → AZs → VPC → Workloads`
```

## **Diagram Option C — Multi‑Region DR**

Code

```
`Region A (Primary)  ⇄  Region B (DR)`

`     |                        |`

`   AZ1—AZ2—AZ3            AZ1—AZ2`
```

## **Relationship Table**

| Related Topic | Relationship |
| :-: | :-: |
| Multi‑Account Strategy | Accounts operate **within Regions/AZs** defined by global infra |
| Landing Zone | Landing Zone chooses **Regions, AZs, and global services** |
| Governance & Guardrails | Guardrails often **restrict Regions**, enforce multi‑AZ usage |

# **2. Multi‑Account Strategy**

## **Definition**

A multi‑account strategy is the practice of using **multiple AWS accounts** to isolate workloads, apply governance, manage cost, and reduce blast radius. It is implemented using **AWS Organizations**.

## **Why**

- Strong **security isolation**

- Clear **cost allocation**

- Different **compliance boundaries**

- Reduced **blast radius**

- Easier **governance** and **delegation**

## **When**

- Multiple teams or business units

- Need for strict prod vs dev separation

- Regulated workloads

- Large-scale migrations

## **How**

1. Create an **AWS Organization**

2. Define **OUs** (Security, Infrastructure, Sandbox, Workloads)

3. Apply **SCPs** to OUs

4. Create accounts via **Control Tower** or custom automation

5. Centralize logging, security, and networking

## **Diagram Option A — Organizational Tree**

Code

```
`Management Account`

`│`

`└── AWS Organizations`

`      │`

`      ├── Security OU`

`      │     ├── Security Account`

`      │     └── Logging Account`

`      │`

`      ├── Infrastructure OU`

`      │     ├── Network Account`

`      │     └── Shared Services Account`

`      │`

`      └── Workloads OU`

`            ├── App1 Dev`

`            ├── App1 Prod`

`            ├── App2 Dev`

`            └── App2 Prod`
```

## **Diagram Option B — Environment Model**

Code

```
`Dev Account → Test Account → Staging Account → Prod Account`
```

## **Relationship Table**

| Related Topic | Relationship |
| :-: | :-: |
| AWS Global Infrastructure | Accounts are deployed **in Regions/AZs** |
| Landing Zone | Landing Zone **implements** the multi‑account strategy |
| Governance & Guardrails | Guardrails are applied **per OU/account** |

# **3. Landing Zone Design**

## **Definition**

A Landing Zone is a **pre‑configured, secure, multi‑account AWS environment** that provides identity, networking, logging, and governance foundations for all workloads.

## **Why**

- Standardized, secure starting point

- Faster onboarding for teams

- Consistent identity, network, and security patterns

- Scalable and auditable environment

## **When**

- Beginning cloud adoption

- Migrating multiple workloads

- Needing compliance-ready environments

- When ad‑hoc accounts become unmanageable

## **How**

1. Choose **Control Tower** or custom Landing Zone

2. Create core accounts:

   - Management

   - Security

   - Logging

   - Network

   - Shared Services

3. Implement identity (IAM Identity Center + IdP)

4. Build network foundation (TGW, shared VPCs)

5. Enable org‑level CloudTrail, Config, GuardDuty

6. Automate account vending

## **Diagram Option A — Control Tower Blueprint**

Code

```
`Management Account`

`│`

`└── Control Tower`

`      │`

`      ├── Security Account (GuardDuty, Security Hub)`

`      ├── Logging Account (CloudTrail, Config)`

`      ├── Network Account (TGW, DX, Shared VPCs)`

`      └── Workload Accounts (Dev, Test, Prod)`
```

## **Diagram Option B — Layered Architecture**

Code

```
`Identity Layer     → IAM Identity Center, IdP`

`Network Layer      → VPCs, TGW, DX/VPN`

`Security Layer     → GuardDuty, Security Hub, Config`

`Logging Layer      → CloudTrail, S3, Config Aggregator`

`Workload Layer     → Application Accounts`
```

## **Relationship Table**

| Related Topic | Relationship |
| :-: | :-: |
| AWS Global Infrastructure | Landing Zone chooses **Regions/AZs** |
| Multi‑Account Strategy | Landing Zone is the **implementation** of the strategy |
| Governance & Guardrails | Guardrails are **embedded** into the Landing Zone |

# **4. Governance & Guardrails**

## **Definition**

Governance is the set of rules and controls that ensure AWS environments operate securely and consistently. Guardrails are **preventive**, **detective**, and **responsive** controls that enforce governance.

## **Why**

- Prevent misconfigurations

- Enforce compliance

- Detect threats

- Automate remediation

- Maintain consistent operations

## **When**

- From day one (minimum guardrails)

- Before production workloads

- After audits or incidents

- As part of continuous improvement

## **How**

### **Preventive**

- SCPs

- IAM permission boundaries

- Region restrictions

- Service restrictions

### **Detective**

- AWS Config rules

- CloudTrail

- Security Hub

- GuardDuty

### **Responsive**

- EventBridge → Lambda

- SSM Automation

- SNS notifications

## **Diagram Option A — Guardrail Types**

Code

```
`Governance`

`│`

`├── Preventive`

`│     ├── SCPs`

`│     ├── IAM Policies`

`│     └── Region Restrictions`

`│`

`├── Detective`

`│     ├── Config Rules`

`│     ├── CloudTrail`

`│     └── Security Hub`

`│`

`└── Responsive`

`      ├── EventBridge`

`      ├── Lambda`

`      └── SSM Automation`
```

## **Diagram Option B — Enforcement Flow**

Code

```
`Action Occurs`

`│`

`├── Preventive Guardrail → Blocked`

`│`

`└── Allowed Action`

`       │`

`       ├── Detective Guardrail → Alert`

`       │`

`       └── Responsive Guardrail → Auto‑Remediation`
```

## **Relationship Table**

| Related Topic | Relationship |
| :-: | :-: |
| AWS Global Infrastructure | Guardrails may **restrict Regions**, enforce multi‑AZ |
| Multi‑Account Strategy | Guardrails applied **per OU/account** |
| Landing Zone | Guardrails are **built into** the Landing Zone |

