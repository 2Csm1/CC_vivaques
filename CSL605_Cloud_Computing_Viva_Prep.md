# ☁️ CSL605 – Cloud Computing Viva Preparation Guide
### Mumbai University | T.E. SEM VI | AWS Platform

> **How to use this document**: Read each section top-to-bottom. Every Q&A is written the way a faculty/external examiner would ask it and the way *you* should confidently answer it. Revisit the 🔴 **MOST LIKELY ASKED** tags first if you're short on time.

---

## 📌 TABLE OF CONTENTS

1. [Module 1 — Cloud Computing Fundamentals](#module-1)
2. [Module 2 — Virtualization](#module-2)
3. [Module 3 — Bare-Metal Hypervisors](#module-3)
4. [Lab 1 — IaaS on AWS (EC2)](#lab-1)
5. [Lab 2 — PaaS on AWS (Elastic Beanstalk)](#lab-2)
6. [Lab 3 — Storage as a Service (S3, Glacier)](#lab-3)
7. [Lab 4 — DBaaS (AWS RDS / DynamoDB)](#lab-4)
8. [Lab 5 — Security as a Service on AWS](#lab-5)
9. [Lab 6 — IAM on AWS](#lab-6)
10. [Lab 7 — Docker / Containerization](#lab-7)
11. [Lab 8 — Kubernetes Orchestration](#lab-8)
12. [Mini Project — SkyPulse Weather Dashboard](#mini-project)
13. [Assignments — Comparative Studies](#assignments)
14. [Quick Revision Cheat Sheet](#cheat-sheet)

---

## MODULE 1 — Cloud Computing Fundamentals {#module-1}

### 🔴 Q1. What is Cloud Computing? (Definition)
**Answer:** Cloud computing is the delivery of computing services — including servers, storage, databases, networking, software, analytics, and intelligence — over the Internet ("the cloud") to offer faster innovation, flexible resources, and economies of scale. You pay only for cloud services you use.

> **NIST Definition (Official):** "Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort."

---

### 🔴 Q2. What are the 5 NIST Essential Characteristics of Cloud Computing?

| # | Characteristic | Simple Explanation |
|---|---|---|
| 1 | **On-demand Self-service** | User can provision resources (VMs, storage) without human interaction from the provider |
| 2 | **Broad Network Access** | Accessible over the network from any device — phone, laptop, tablet |
| 3 | **Resource Pooling** | Provider's resources are pooled to serve multiple consumers using multi-tenancy |
| 4 | **Rapid Elasticity** | Resources can be scaled up or down quickly, sometimes automatically |
| 5 | **Measured Service** | Usage is monitored, controlled, reported → pay-as-you-go model |

---

### 🔴 Q3. What are the Service Models of Cloud? Give examples.

| Model | Full Form | What the provider gives you | Examples |
|---|---|---|---|
| **IaaS** | Infrastructure as a Service | VMs, storage, networking | AWS EC2, Azure VMs, GCP Compute Engine |
| **PaaS** | Platform as a Service | Runtime, OS, middleware — just deploy your app | AWS Elastic Beanstalk, Azure App Service, Heroku |
| **SaaS** | Software as a Service | Full software over internet | Gmail, Salesforce, Zoom, Office 365 |
| **DBaaS** | Database as a Service | Managed databases | AWS RDS, AWS DynamoDB, Firebase, MongoDB Atlas |
| **SECaaS** | Security as a Service | Managed security (WAF, threat detection) | AWS Shield, AWS GuardDuty, Azure Defender |
| **STaaS** | Storage as a Service | Scalable object/file/block storage | AWS S3, AWS Glacier, Azure Blob |

---

### 🔴 Q4. What are the Deployment Models?

| Model | Who accesses it | Owner | Example |
|---|---|---|---|
| **Public Cloud** | Anyone on the internet | Cloud Provider (AWS, Azure, GCP) | AWS, Google Cloud |
| **Private Cloud** | Only one organization | The organization itself | On-premises OpenStack, VMware |
| **Hybrid Cloud** | Combination of both | Shared responsibility | AWS Outposts + on-prem |
| **Community Cloud** | Shared by specific group | Group of organizations | Government clouds, Healthcare clouds |

---

### Q5. What is the Cloud Cube Model?
**Answer:** The Cloud Cube Model (developed by Jericho Forum) classifies cloud computing by four dimensions:
- **Internal / External** — Where is the cloud hosted? (within or outside your organization boundary)
- **Proprietary / Open** — Is the technology vendor-locked or standards-based?
- **Perimeterized / De-perimeterized** — Is traditional security perimeter present or not?
- **Insourced / Outsourced** — Who manages the service?

> It helps organizations evaluate and classify cloud options for their security needs.

---

### Q6. What are the advantages and disadvantages of Cloud Computing?

**Advantages:**
- Cost savings (no upfront capital)
- Scalability and flexibility
- Disaster recovery built-in
- Global reach
- Auto-updates / maintenance by provider
- Pay-as-you-go

**Disadvantages:**
- Internet dependency
- Security and privacy concerns
- Vendor lock-in
- Limited control over infrastructure
- Downtime risk (SLA-dependent)

---

### Q7. How is Cloud Computing different from Grid, Cluster, and Distributed Computing?

| Technology | Definition | Key Difference |
|---|---|---|
| **Cloud Computing** | On-demand services over internet | Pay-per-use, consumer-facing, managed |
| **Grid Computing** | Multiple computers solving one large problem | Task-based, scientific, no SLAs |
| **Cluster Computing** | Group of computers working as one unit | Tightly coupled, local network |
| **Distributed Computing** | Geographically spread computation | No central control, fault tolerant |
| **Parallel Computing** | Simultaneous processing on multiple cores | Processor-level, not network-based |
| **Quantum Computing** | Uses qubits and quantum mechanics | Next-gen, for complex optimization problems |

---

### Q8. What is an SLA in cloud computing?
**Answer:** SLA = **Service Level Agreement**. It is a contract between the cloud provider and the customer that defines:
- **Uptime guarantee** (e.g., AWS guarantees 99.99% uptime for S3)
- **Response time**
- **Support levels**
- **Penalties for violations** (credits/refunds)

> Example: AWS S3 SLA guarantees 99.9% monthly uptime. If they fail, you get a service credit.

---

### Q9. What is Scalability vs Elasticity?
**Answer:**
- **Scalability** = The ability of a system to handle increased workload by adding resources (either **vertical** — bigger machine, or **horizontal** — more machines). It's a design property.
- **Elasticity** = The ability to **automatically** scale up and scale down based on real-time demand. It implies automation.

> **Example**: AWS Auto Scaling is elastic — it adds EC2 instances when traffic spikes and removes them when traffic drops.

---

### Q10. What is Multi-tenancy?
**Answer:** Multiple customers (tenants) share the same physical infrastructure but their data and applications are isolated from each other. It's the core model that makes cloud economically viable.

---

## MODULE 2 — Virtualization {#module-2}

### 🔴 Q11. What is Virtualization?
**Answer:** Virtualization is the process of creating a **virtual (software-based) version** of something — a server, storage device, network, or operating system. It allows multiple virtual machines (VMs) to run on a single physical machine, each thinking it has its own dedicated hardware.

---

### 🔴 Q12. What is a Hypervisor? What are its types?
**Answer:** A Hypervisor (also called Virtual Machine Monitor — VMM) is software that **creates and manages VMs** by abstracting the physical hardware.

| Feature | Type 1 (Bare-Metal) | Type 2 (Hosted) |
|---|---|---|
| Runs on | Directly on hardware | On top of a host OS |
| Performance | High (no extra OS layer) | Lower (extra OS overhead) |
| Use case | Enterprise, Data Centers, Production | Development, Testing, Learning |
| Examples | VMware ESXi, Microsoft Hyper-V, Xen, KVM | VirtualBox, VMware Workstation, QEMU |

---

### 🔴 Q13. What types of Virtualization exist?

| Type | What is virtualized | Example |
|---|---|---|
| **Server Virtualization** | Physical servers → multiple VMs | VMware ESXi, KVM |
| **Desktop Virtualization** | Run desktop OS in VM | VirtualBox, VMware Workstation |
| **Network Virtualization** | Create logical networks over physical network | VLAN, SDN |
| **Storage Virtualization** | Pool physical storage devices into one logical unit | AWS EBS, SAN |
| **Application Virtualization** | Run apps without full install | Citrix |
| **OS-Level Virtualization** | Containers — lightweight virtualization | Docker |

---

### Q14. What is the difference between a Virtual Machine and a Container?

| Feature | Virtual Machine | Container |
|---|---|---|
| Includes | Full OS + App | App + dependencies only (shares host OS kernel) |
| Size | GBs | MBs |
| Start time | Minutes | Seconds |
| Isolation | Strong (hardware-level) | Process-level |
| Overhead | Heavy | Lightweight |
| Portability | Less portable | Highly portable |
| Example | AWS EC2 (AMI) | Docker container |

---

### Q15. What is KVM? How does it compare with VirtualBox?
**Answer:**
- **KVM (Kernel-based Virtual Machine)** — A Type 1 hypervisor built into the Linux kernel. Uses hardware virtualization extensions (Intel VT-x / AMD-V). High performance, enterprise-grade.
- **VirtualBox** — A Type 2 hosted hypervisor by Oracle. Runs on Windows/Linux/Mac. Good for learning and development.

**Comparison:**
| Parameter | KVM | VirtualBox |
|---|---|---|
| Type | Type 1 (Bare-metal, Linux kernel module) | Type 2 (Hosted) |
| OS Host | Linux only | Windows, Mac, Linux |
| Performance | Very high | Moderate |
| GUI | Virt-Manager (separate tool) | Built-in GUI |
| Use case | Cloud servers (AWS uses KVM!) | Dev/test on desktop |
| Cost | Free (open source) | Free (open source) |

> **Fun fact**: AWS EC2 instances run on a modified KVM-based hypervisor called **Nitro**.

---

### Q16. What is a Snapshot in Virtualization?
**Answer:** A snapshot captures the **exact state** of a VM at a particular point in time — including memory, disk, and configuration. You can **restore** a VM to that state if something goes wrong. Used heavily for backups.

> AWS equivalent: **EC2 EBS Snapshots** (stored in S3 internally)

---

## MODULE 3 — Bare-Metal Hypervisors {#module-3}

### Q17. What is a Bare-Metal Hypervisor?
**Answer:** A bare-metal hypervisor (Type 1) runs directly on the physical hardware without any underlying OS. It has direct access to hardware resources, making it faster and more secure than hosted hypervisors.

**Examples:** VMware ESXi, Microsoft Hyper-V, Citrix XenServer, KVM

---

### Q18. What is VMware ESXi?
**Answer:** VMware ESXi is a bare-metal hypervisor from VMware (now Broadcom). It installs directly on server hardware. VMs are managed through **vCenter Server** or the local **vSphere Client**. It's the industry standard for enterprise private clouds.

---

### Q19. What additional services do hypervisors like VMware provide?
- **Live Migration (vMotion)** — Move a running VM from one host to another with zero downtime
- **High Availability (HA)** — Automatically restart VMs on another host if one fails
- **Load Balancing (DRS)** — Distribute VMs across hosts for optimal resource use
- **Auto-Scaling** — Add resources dynamically
- **Snapshot & Backup**
- **Security** — VM isolation, network segmentation

---

## LAB 1 — IaaS using AWS EC2 {#lab-1}

### 🔴 Q20. What is IaaS? How did you implement it?
**Answer:** IaaS = **Infrastructure as a Service**. The cloud provider gives you virtualized infrastructure — compute (VMs), networking, storage. You manage the OS and everything above.

**How we implemented it**: Used **AWS EC2 (Elastic Compute Cloud)** to launch a virtual machine.

---

### 🔴 Q21. What are the steps to create and launch an EC2 instance?
**Steps:**
1. Login to **AWS Console → EC2 → Launch Instance**
2. Choose **AMI** (Amazon Machine Image) — e.g., Ubuntu 22.04 or Amazon Linux 2
3. Choose **Instance Type** — e.g., `t2.micro` (Free Tier eligible)
4. Configure **Key Pair** — create/download `.pem` file for SSH access
5. Configure **Security Group** — open port 22 (SSH) or 3389 (RDP)
6. Configure **Storage** — default 8 GB EBS root volume
7. Click **Launch Instance**
8. **Access the VM**:
   - Linux: `ssh -i mykey.pem ubuntu@<public-ip>`
   - Windows: Use RDP client with public IP

---

### 🔴 Q22. What is an AMI?
**Answer:** AMI = **Amazon Machine Image**. It is a pre-configured template containing the OS, application server, and application used to launch EC2 instances. Think of it as a VM snapshot/image.

> You can use AWS-provided AMIs, marketplace AMIs, or create your own custom AMI.

---

### Q23. What is an Instance Type? What is t2.micro?
**Answer:** Instance types define the hardware of the host computer — how much CPU, RAM, and network performance you get.

- `t2.micro` = 1 vCPU, 1 GB RAM — **Free Tier eligible** for 750 hours/month
- `m5.xlarge` = 4 vCPU, 16 GB RAM — production workload
- **T** = burstable performance instances
- **M** = general purpose
- **C** = compute optimized
- **R** = memory optimized
- **G** = GPU instances

---

### Q24. What is a Security Group in AWS?
**Answer:** A Security Group acts as a **virtual firewall** for EC2 instances. It controls **inbound and outbound traffic** at the instance level.
- **Inbound rules**: What traffic is allowed *into* the instance (e.g., allow SSH on port 22 from my IP)
- **Outbound rules**: What traffic is allowed *out* of the instance (default: all traffic allowed)
- Security groups are **stateful** — if you allow inbound port 80, the response automatically goes out

---

### Q25. What is the difference between a Public IP and Elastic IP in AWS?
- **Public IP** — Dynamic, changes every time you stop/start the instance. Free but temporary.
- **Elastic IP (EIP)** — Static, persistent IP address. It stays the same even after restart. Charged if not associated with a running instance.

---

### Q26. What is RDP? What is VNC? Why do we use them?
- **RDP (Remote Desktop Protocol)** — Microsoft protocol (port 3389) used to access Windows VMs graphically
- **VNC (Virtual Network Computing)** — Cross-platform protocol for remote graphical desktop access (port 5900+)
- **SSH** — Terminal (command-line) access to Linux VMs (port 22)

---

### Q27. What is an EBS volume? How is it different from instance storage?

| Feature | EBS (Elastic Block Store) | Instance Store |
|---|---|---|
| Persistence | Persists after instance stop/restart | **Lost** when instance stops |
| Type | Network-attached SSD/HDD | Physically attached to host |
| Backup | Can take snapshots | Cannot snapshot |
| Use | OS disk, databases | Temporary cache, buffer |

---

## LAB 2 — PaaS using AWS Elastic Beanstalk {#lab-2}

### 🔴 Q28. What is PaaS? How did you implement it?
**Answer:** PaaS = **Platform as a Service**. The provider manages everything from the OS up — runtime, middleware, web server. You only manage your **application code**.

**How we implemented it**: Used **AWS Elastic Beanstalk** to deploy a web application.

---

### 🔴 Q29. What is AWS Elastic Beanstalk?
**Answer:** Elastic Beanstalk is a fully managed PaaS from AWS. You upload your application code (Python, Node.js, Java, PHP, Ruby, .NET, Docker) and Beanstalk:
- Automatically provisions EC2 instances
- Sets up load balancer
- Configures auto-scaling
- Manages health monitoring
- Handles deployments and rollbacks

> You still **own** the underlying EC2 instances — unlike Lambda where you have zero server management.

---

### Q30. What languages/runtimes does Elastic Beanstalk support?
- Python (Flask, Django)
- Node.js (Express)
- Java (Tomcat)
- PHP
- Ruby on Rails
- .NET (IIS)
- Go
- Docker (any language)

---

### Q31. Elastic Beanstalk vs EC2 — when to use which?

| Scenario | Use |
|---|---|
| You want full control over server config | EC2 |
| You just want to deploy an app quickly | Elastic Beanstalk |
| You need auto-scaling without manual setup | Elastic Beanstalk |
| You need to install custom system software | EC2 |

---

### Q32. What is the difference between IaaS, PaaS, SaaS in terms of responsibility?

```
                  You manage    Provider manages
IaaS:    App, Runtime, OS   |  Virtualization, Servers, Storage, Networking
PaaS:    App only           |  Runtime, OS, Middleware, and all below
SaaS:    Nothing            |  Everything
```

> Think of pizza analogy: IaaS = you cook; PaaS = restaurant prepares but you serve; SaaS = restaurant delivers ready to eat 🍕

---

## LAB 3 — Storage as a Service (AWS S3 & Glacier) {#lab-3}

### 🔴 Q33. What is Amazon S3?
**Answer:** S3 = **Simple Storage Service**. It is AWS's **object storage** service — store any type of file (images, videos, code, backups) as objects in **buckets**. S3 is:
- Highly durable: **99.999999999% (11 nines)** durability
- Highly available: **99.99%** availability
- Scalable: No storage limit
- Serverless: Fully managed, no servers to manage

---

### 🔴 Q34. What is an S3 Bucket? What is an Object?
- **Bucket** = The top-level container (like a folder) to store objects. Name must be globally unique.
- **Object** = A file stored in S3. Has a **Key** (filename/path), **Value** (data), **Metadata**, and **Version ID**.
- S3 uses a **flat namespace** — there are no real folders, just key prefixes.

---

### Q35. What are the types of S3 Storage Classes?

| Storage Class | Use case | Retrieval time | Cost |
|---|---|---|---|
| **S3 Standard** | Frequently accessed data | Immediate | Highest |
| **S3 Standard-IA** | Infrequently Accessed | Immediate | Lower |
| **S3 One Zone-IA** | Infrequent, one AZ only | Immediate | Even lower |
| **S3 Glacier Instant** | Archival, millisecond retrieval | Milliseconds | Low |
| **S3 Glacier Flexible** | Archival data | Minutes to hours | Very low |
| **S3 Glacier Deep Archive** | Long-term archival (years) | 12 hrs | Cheapest |
| **S3 Intelligent-Tiering** | Unknown access patterns | Automatic | Variable |

---

### 🔴 Q36. What is AWS Glacier used for?
**Answer:** Glacier is an extremely low-cost storage service for **long-term archival** of data that is rarely accessed. Backup tapes, compliance data, old logs.
- Retrieval takes minutes to hours (not immediate like S3 Standard)
- 3 retrieval options: **Expedited** (1-5 min), **Standard** (3-5 hrs), **Bulk** (5-12 hrs)

---

### Q37. How did you use S3 in your mini project?
**Answer:** We hosted our **SkyPulse weather dashboard frontend** (HTML, CSS, JavaScript files) on an S3 bucket with **Static Website Hosting** enabled. The S3 bucket served the `index.html` as a public website without needing any web server.

Steps we followed:
1. Created S3 bucket `skypulse-weather-dashboard`
2. Disabled "Block all public access"
3. Uploaded `index.html`, `style.css`, `app.js`
4. Enabled **Static Website Hosting** → set index document as `index.html`
5. Added **Bucket Policy** to allow `s3:GetObject` for everyone (`Principal: *`)
6. Accessed the website via the S3 website endpoint URL

---

### Q38. What is the difference between Object, File, and Block Storage?

| Type | Description | Example |
|---|---|---|
| **Object Storage** | Store data as objects with metadata | AWS S3 |
| **File Storage** | Hierarchical folders and files | AWS EFS, NFS |
| **Block Storage** | Raw storage blocks, like a hard disk | AWS EBS, SAN |

---

### Q39. What is OwnCloud?
**Answer:** OwnCloud is an **open-source, self-hosted** cloud storage solution. It's the private cloud alternative to Dropbox. Organizations can set it up on their own servers to keep data in-house — gives them full control and privacy.

---

### Q40. What are CORS headers? Why did we need them in S3?
**Answer:** CORS = **Cross-Origin Resource Sharing**. When your S3-hosted frontend (e.g., `http://s3bucket.s3-website.amazonaws.com`) calls an API Gateway endpoint (different domain), the browser blocks it by default (same-origin policy).

CORS headers tell the browser: "This server allows requests from this other origin."

We handled CORS in our Lambda by returning:
```python
CORS_HEADERS = {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Headers": "Content-Type",
    "Access-Control-Allow-Methods": "GET,OPTIONS",
}
```

---

## LAB 4 — Database as a Service (AWS RDS / DynamoDB) {#lab-4}

### 🔴 Q41. What is DBaaS?
**Answer:** DBaaS = **Database as a Service**. The cloud provider manages the database server — installation, patching, backups, scaling. You just connect to it and use it.

---

### 🔴 Q42. What is AWS RDS?
**Answer:** RDS = **Relational Database Service**. Fully managed **SQL database** service. Supported engines:
- MySQL
- PostgreSQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Amazon Aurora (AWS's own, MySQL/PostgreSQL compatible, 5× faster)

---

### Q43. What does AWS RDS manage for you?
- OS patching
- DB engine upgrades
- Automated backups (up to 35 days retention)
- Multi-AZ failover (high availability)
- Read replicas (for read scaling)
- Encryption at rest (KMS) and in transit (SSL/TLS)
- Monitoring via CloudWatch

---

### Q44. What is the difference between SQL and NoSQL?

| Feature | SQL (Relational) | NoSQL |
|---|---|---|
| Data Model | Tables with rows/columns | Documents, key-value, graphs, columns |
| Schema | Fixed schema | Dynamic / schema-less |
| Scale | Vertical (scale-up) | Horizontal (scale-out) |
| ACID | Full ACID compliance | Eventual consistency (usually) |
| Examples | MySQL, PostgreSQL, Oracle | DynamoDB, MongoDB, Cassandra, Firebase |
| Use case | Structured data, banking | Unstructured data, real-time, IoT |

---

### 🔴 Q45. What is Amazon DynamoDB?
**Answer:** DynamoDB is AWS's fully managed **NoSQL key-value and document database**. It provides:
- Single-digit millisecond latency
- Serverless — no provisioning
- Auto-scaling
- Built-in replication across multiple AZs
- Used for: gaming, IoT, e-commerce (Amazon uses it for shopping cart)

---

### Q46. What is Firebase? What is MongoDB Atlas?
- **Firebase** — Google's BaaS (Backend as a Service). Has Firestore (NoSQL) and Realtime Database. Good for mobile apps.
- **MongoDB Atlas** — Cloud-hosted MongoDB. Managed NoSQL document DB. Works on AWS/Azure/GCP.

---

### Q47. What is Multi-AZ in RDS?
**Answer:** Multi-AZ = Multi-Availability Zone. RDS automatically creates a **standby replica** in a different Availability Zone. If the primary DB fails, RDS **automatically fails over** to the standby with no manual intervention. This gives **high availability**, not performance improvement (for reads, use Read Replicas with Multi-AZ).

---

## LAB 5 — Security as a Service on AWS {#lab-5}

### 🔴 Q48. What is Security as a Service (SECaaS)?
**Answer:** SECaaS = **Security as a Service**. Cloud providers offer managed security services — threat detection, DDoS protection, firewall, encryption — as a service. You don't need to manage the security infrastructure.

---

### 🔴 Q49. What are the key AWS Security services? (Name and explain each)

| Service | What it does |
|---|---|
| **AWS IAM** | Identity and Access Management — controls who can do what |
| **AWS Shield** | DDoS protection (Standard = free, Advanced = paid) |
| **AWS WAF** | Web Application Firewall — filter malicious HTTP requests (SQL injection, XSS) |
| **AWS GuardDuty** | Threat detection using ML — monitors VPC flow logs, DNS, CloudTrail |
| **AWS Inspector** | Automated security assessments for EC2 instances and container images |
| **AWS Macie** | Uses ML to discover and protect sensitive data in S3 (PII, credit cards) |
| **AWS KMS** | Key Management Service — create and manage encryption keys |
| **AWS CloudTrail** | Logs **all API calls** made in your AWS account — audit trail |
| **AWS Config** | Tracks configuration changes to AWS resources |
| **AWS Security Hub** | Centralized security findings dashboard |

---

### Q50. What is the AWS Shared Responsibility Model?
**Answer:** Security responsibilities are SHARED between AWS and the customer:

- **AWS is responsible for** security **OF** the cloud:
  - Physical security of data centers
  - Hardware, software, networking of the cloud infrastructure
  - Hypervisor security

- **You (customer) are responsible for** security **IN** the cloud:
  - What you put in: data, applications
  - IAM users, permissions, passwords
  - Network configuration (security groups, NACLs)
  - Operating system patching
  - Encryption of data

> 💡 Memory trick: "AWS protects the house; you protect what's inside the house."

---

### Q51. What is AWS Shield?
**Answer:** AWS Shield protects against **DDoS (Distributed Denial of Service)** attacks.
- **Shield Standard** — Free, automatically enabled for all AWS customers. Protects against common Layer 3/4 attacks.
- **Shield Advanced** — Paid (~$3000/month), gives 24/7 DDoS response team access, detailed attack diagnostics, cost protection.

---

### Q52. What is AWS WAF?
**Answer:** WAF = **Web Application Firewall**. Sits in front of your web application and filters HTTP/HTTPS traffic based on rules you define.
- Blocks **SQL Injection**
- Blocks **Cross-Site Scripting (XSS)**
- Rate limiting (block IPs sending too many requests)
- Works with **API Gateway, CloudFront, ALB**

---

### Q53. What is AWS GuardDuty?
**Answer:** GuardDuty is a **threat detection service** that uses machine learning to analyze:
- **VPC Flow Logs** — unusual network patterns
- **CloudTrail events** — suspicious API activity
- **DNS logs** — communication with known malicious domains

If it detects something suspicious, it raises a **finding** that you can act on.

---

### Q54. What is encryption? What is encryption at rest vs in transit?
- **At rest** = Data stored on disk is encrypted (using AES-256). AWS KMS manages the keys. Example: S3 server-side encryption.
- **In transit** = Data moving over the network is encrypted using **TLS/SSL** (HTTPS). Prevents man-in-the-middle attacks.

---

## LAB 6 — Identity and Access Management (IAM) {#lab-6}

### 🔴 Q55. What is AWS IAM?
**Answer:** IAM = **Identity and Access Management**. It is a global AWS service that lets you control **who** (authentication) can do **what** (authorization) on your AWS account.

Core IAM components:
- **Users** — Individual accounts (humans or apps)
- **Groups** — Collection of users
- **Roles** — Temporary permissions (assigned to services like EC2, Lambda)
- **Policies** — JSON documents that define permissions

---

### 🔴 Q56. What is an IAM Policy? Give an example.
**Answer:** A Policy is a **JSON document** that grants or denies specific actions on specific resources.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```
This policy allows reading objects from `my-bucket`.

Key fields:
- **Effect**: `Allow` or `Deny`
- **Action**: AWS API actions (e.g., `s3:PutObject`, `ec2:StartInstances`)
- **Resource**: Which AWS resource this applies to (ARN)

---

### Q57. What is the Principle of Least Privilege?
**Answer:** Give users/services **only the minimum permissions** they need to do their job — nothing more. This limits the blast radius if credentials are compromised.

> Example: A Lambda function that only reads from S3 should have a role with only `s3:GetObject` — NOT full admin access.

---

### 🔴 Q58. What is an IAM Role? Why is it better than using IAM User credentials in code?
**Answer:** An IAM Role is an identity with permissions that can be **assumed temporarily** by AWS services, users, or applications.

- **Never hardcode IAM user credentials** (Access Key ID + Secret) in application code — it's a security risk.
- Instead, **attach an IAM Role to the EC2 instance or Lambda function**. AWS automatically provides temporary credentials to the service.
- In our SkyPulse Lambda, we attached a role that allowed Lambda to log to **CloudWatch Logs** and call the OpenWeatherMap API.

---

### Q59. What are IAM Best Practices?
1. **Never use root account** for daily tasks
2. Enable **MFA (Multi-Factor Authentication)** for all privileged accounts
3. Use **Roles** for services, not Access Keys
4. Apply **Least Privilege** principle
5. Regularly **rotate credentials**
6. Use **CloudTrail** to audit IAM activity
7. Create individual users — do not share accounts

---

### Q60. What is MFA in AWS?
**Answer:** MFA = **Multi-Factor Authentication**. Adds a second layer of security beyond password. AWS supports:
- Virtual MFA (Google Authenticator, Authy)
- Hardware MFA (physical key)
- U2F security key (YubiKey)

---

### Q61. What is an ARN?
**Answer:** ARN = **Amazon Resource Name**. A unique identifier for every AWS resource.

Format: `arn:partition:service:region:account-id:resource`

Example: `arn:aws:s3:::skypulse-weather-dashboard` (S3 bucket)
Example: `arn:aws:lambda:ap-south-1:123456789:function:skypulse-weather`

---

## LAB 7 — Containerization using Docker {#lab-7}

### 🔴 Q62. What is Docker? What problem does it solve?
**Answer:** Docker is an open-source platform for **containerization** — packaging an application with all its dependencies (libraries, configs, runtime) into a lightweight, portable **container**.

**Problem it solves**: "It works on my machine but not on yours." With Docker, the entire environment is packaged together → runs identically everywhere.

---

### 🔴 Q63. What is the difference between Image and Container?
- **Docker Image** = A read-only template/blueprint (like a class in OOP or a VM snapshot). Built from a Dockerfile.
- **Docker Container** = A running instance of an image (like an object from a class). Multiple containers can run from one image.

---

### 🔴 Q64. What is a Dockerfile?
**Answer:** A text file containing instructions to **build a Docker Image**.

Example:
```dockerfile
FROM python:3.11-slim          # Base image
WORKDIR /app                   # Set working directory
COPY requirements.txt .        # Copy requirements file
RUN pip install -r requirements.txt  # Install dependencies
COPY . .                       # Copy app code
EXPOSE 5000                    # Open port 5000
CMD ["python", "app.py"]       # Command to run app
```

---

### 🔴 Q65. What are the most important Docker commands?

| Command | What it does |
|---|---|
| `docker pull nginx` | Download image from Docker Hub |
| `docker build -t myapp .` | Build image from Dockerfile |
| `docker run -d -p 80:80 nginx` | Run container in background, map port |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers (including stopped) |
| `docker stop <id>` | Stop a running container |
| `docker rm <id>` | Remove a stopped container |
| `docker images` | List all local images |
| `docker rmi <image>` | Remove an image |
| `docker logs <id>` | View container logs |
| `docker exec -it <id> bash` | Open shell inside running container |
| `docker-compose up` | Start multi-container apps |

---

### Q66. What is Docker Hub?
**Answer:** Docker Hub is the **public registry** for Docker images. It's like GitHub but for container images. You can:
- Pull official images (nginx, mysql, python, node)
- Push your own images (public or private)

Other registries: **AWS ECR (Elastic Container Registry)**, Docker Registry (private self-hosted)

---

### Q67. What is Docker Compose?
**Answer:** Docker Compose is a tool to **define and run multi-container applications** using a `docker-compose.yml` file.

Example (web app + database):
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: secret
```

Run with: `docker-compose up`

---

### Q68. What are Docker Volumes?
**Answer:** Volumes are the way to **persist data** generated by containers. Containers are ephemeral (data is lost when they stop). Volumes store data on the host filesystem.

```bash
docker run -v /host/path:/container/path nginx
```

---

### Q69. What is the difference between VM and Container (detailed)?

| Aspect | Virtual Machine | Container |
|---|---|---|
| OS | Each VM has its own full OS | Shares host OS kernel |
| Isolation | Hardware-level (hypervisor) | Process-level (namespaces, cgroups) |
| Boot time | 1-5 minutes | Seconds |
| Size | GBs (includes OS) | MBs (app + libs only) |
| Performance | Near native but overhead from hypervisor | Near native, minimal overhead |
| Portability | Harder (large, OS-specific) | Very easy (run anywhere Docker is installed) |
| Security | Stronger isolation | Less isolated (kernel shared) |
| Use case | Legacy apps, Windows workloads | Microservices, CI/CD, cloud-native |

---

## LAB 8 — Kubernetes Orchestration {#lab-8}

### 🔴 Q70. What is Kubernetes (K8s)?
**Answer:** Kubernetes is an open-source **container orchestration platform** originally developed by Google. It automates:
- **Deployment** of containers
- **Scaling** (horizontal pod autoscaling)
- **Load balancing**
- **Self-healing** (restart failed containers)
- **Rolling updates and rollbacks**

> K8s = K + 8 letters + s (kubernetes)

---

### 🔴 Q71. What are the key Kubernetes components?

**Control Plane (Master):**
- **API Server** — Entry point for all K8s commands
- **etcd** — Key-value store that holds cluster state
- **Scheduler** — Decides which node runs which pod
- **Controller Manager** — Ensures desired state is maintained

**Worker Nodes:**
- **kubelet** — Agent on each node, ensures containers are running
- **kube-proxy** — Network proxy, handles routing to pods
- **Container Runtime** — Docker or containerd

---

### 🔴 Q72. What is a Pod?
**Answer:** A Pod is the **smallest deployable unit** in Kubernetes. It contains one or more containers that share:
- The same IP address
- The same storage volumes
- The same network namespace

> Usually, 1 pod = 1 container. But sidecar pattern uses 2 containers in one pod.

---

### Q73. What is a Deployment in Kubernetes?
**Answer:** A Deployment is a K8s object that manages **replica sets** of pods. It defines:
- Which container image to run
- How many replicas (copies) to run
- Update strategy (rolling update)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: weather-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: weather
  template:
    metadata:
      labels:
        app: weather
    spec:
      containers:
      - name: weather
        image: myweatherapp:latest
        ports:
        - containerPort: 80
```

---

### Q74. What is a Service in Kubernetes?
**Answer:** A Service is a **stable network endpoint** to access a group of pods. Pods can die and be replaced (with new IPs), but the Service keeps a fixed DNS name and IP.

Types:
- **ClusterIP** — Internal only (default)
- **NodePort** — Exposes on a port of each node
- **LoadBalancer** — Creates a cloud load balancer (works on AWS EKS, GKE, AKS)
- **ExternalName** — Maps to an external DNS name

---

### Q75. What is the difference between Docker and Kubernetes?
- **Docker** = a tool to create and run individual containers
- **Kubernetes** = a tool to manage and orchestrate MANY containers across many machines

> Docker is like a single car; Kubernetes is like the traffic management system for hundreds of cars.

---

### Q76. What is kubectl?
**Answer:** `kubectl` is the **command-line tool** to interact with a Kubernetes cluster.

Common commands:
```bash
kubectl get pods                    # List all pods
kubectl get deployments             # List deployments
kubectl apply -f deployment.yaml   # Create/update resources from YAML
kubectl delete pod mypod           # Delete a pod
kubectl logs mypod                 # View pod logs
kubectl exec -it mypod -- bash     # Shell into a pod
kubectl scale deployment weather-app --replicas=5  # Scale
kubectl describe pod mypod        # Detailed info about pod
```

---

### Q77. What is minikube?
**Answer:** Minikube is a tool to run a **single-node Kubernetes cluster locally** on your computer. Used for learning and testing K8s without needing a cloud cluster. Starts with:
```bash
minikube start
kubectl get nodes
```

---

## MINI PROJECT — SkyPulse Weather Dashboard {#mini-project}

### 🔴 Q78. Explain your mini project in brief.
**Answer:**

**SkyPulse** is a real-time weather dashboard web application deployed on **AWS Free Tier**. It allows users to search for any city and get:
- Current weather (temperature, humidity, wind speed, pressure, cloud cover)
- 5-day daily forecast
- 12-hour hourly forecast
- Dynamic weather-based background themes

**Architecture (3-tier)**:
```
User's Browser
     │  (HTTPS)
     ▼
Amazon S3 (Static Website Hosting) — serves HTML/CSS/JS
     │  fetch() HTTP call
     ▼
Amazon API Gateway (REST API, /weather, /forecast endpoints)
     │  Lambda proxy integration
     ▼
AWS Lambda (Python — weather_lambda.py)
     │  HTTPS call
     ▼
OpenWeatherMap API (external weather data)
```

**AWS Services Used:**
- **S3** — Frontend hosting (IaaS/SaaS pattern)
- **API Gateway** — REST API endpoint (PaaS pattern)
- **Lambda** — Serverless backend (FaaS — Function as a Service)
- **IAM** — Lambda execution role for CloudWatch logging
- **CloudWatch** — Auto-logs Lambda invocations and errors
- **Environment Variables** — API key secured in Lambda config

---

### 🔴 Q79. Why did you use Lambda instead of putting the API key directly in JavaScript?
**Answer:** **Security** — JavaScript runs in the browser and can be viewed by anyone (View Source). If the API key were in `app.js`, any user could see and steal it, using up our API quota or causing charges.

By using **Lambda**:
- API key is stored server-side as an **environment variable** in Lambda (`OWM_API_KEY`)
- The browser only talks to our API Gateway URL — never directly to OpenWeatherMap
- The key is never exposed to the client

---

### 🔴 Q80. What is AWS Lambda? What is Serverless Computing?
**Answer:** Lambda is AWS's **serverless compute** service. You write code (functions) and AWS runs them when triggered — no server provisioning, no OS management.

**Serverless characteristics:**
- You pay per **invocation** (not for idle time)
- AWS manages the infrastructure completely
- Auto-scales from 0 to thousands of invocations
- Max execution time: 15 minutes per invocation
- Triggered by: API Gateway, S3 events, DynamoDB streams, CloudWatch, SNS/SQS, etc.

**In our project**: Lambda was triggered by **API Gateway GET requests**.

---

### 🔴 Q81. What is API Gateway?
**Answer:** API Gateway is a fully managed service to **create, publish, maintain, and secure APIs** at any scale. In our project:
- Created a **REST API** with two resources: `/weather` and `/forecast`
- Each resource has a **GET method** integrated with Lambda
- **CORS** enabled so S3 frontend can call it cross-origin
- Deployed to a **prod stage** → generates an Invoke URL

---

### Q82. Explain the flow when a user types "Mumbai" and presses Enter.

1. User types "Mumbai" in search box and presses Enter
2. `fetchWeather()` function in `app.js` is called
3. Since `USE_LAMBDA = true`, the app fires two parallel `fetch()` calls:
   - `GET https://kf7n4k0a4d.execute-api.ap-south-1.amazonaws.com/prod/weather?city=Mumbai`
   - `GET https://kf7n4k0a4d.execute-api.ap-south-1.amazonaws.com/prod/forecast?city=Mumbai`
4. API Gateway routes both requests to the **Lambda function** (`weather_lambda.py`)
5. Lambda reads `city` from query params, constructs OpenWeatherMap URL
6. Lambda calls `https://api.openweathermap.org/data/2.5/weather?q=Mumbai&appid=<KEY>`
7. Lambda receives JSON from OpenWeatherMap, returns it with CORS headers
8. API Gateway sends response back to browser
9. `app.js` calls `renderAll(current, forecast)`:
   - `renderCurrentWeather()` — shows temp, description, feels like
   - `renderStats()` — shows humidity, pressure, wind, sunrise/sunset with animated bars
   - `renderForecast()` — shows 5-day cards
   - `renderHourly()` — shows 12-hour scroll cards
   - `updateBackground()` — changes body class for weather theme

---

### Q83. What is the temperature conversion formula used in the project?
**Answer:** OpenWeatherMap API returns temperatures in **Kelvin**.

- **Kelvin to Celsius**: `°C = K - 273.15`
- **Kelvin to Fahrenheit**: `°F = (K - 273.15) × 9/5 + 32`

In code:
```javascript
function toDisplay(kelvin) {
  return currentUnit === 'C'
    ? Math.round(kelvin - 273.15)
    : Math.round((kelvin - 273.15) * 9 / 5 + 32);
}
```

---

### Q84. What is CORS? Why did you handle it in Lambda?
**Answer:** CORS = **Cross-Origin Resource Sharing**. A browser security mechanism that blocks web pages from making requests to a different domain than the one that served the page.

Our S3 URL (`*.s3-website.amazonaws.com`) and API Gateway URL (`*.execute-api.amazonaws.com`) are **different origins**. Without CORS headers, the browser would block the API calls.

Our Lambda returns these headers with every response:
```python
CORS_HEADERS = {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Headers": "Content-Type",
    "Access-Control-Allow-Methods": "GET,OPTIONS",
}
```

We also handle **OPTIONS preflight** requests (browser sends before actual request).

---

### Q85. What cloud concepts does your mini project demonstrate?

| Concept | How it's demonstrated |
|---|---|
| **IaaS** | Underlying EC2 compute for Lambda (abstracted away) |
| **PaaS** | Lambda + API Gateway = managed platform |
| **SaaS** | The weather dashboard itself is Software as a Service |
| **Storage as a Service** | S3 hosts the frontend |
| **Security as a Service** | IAM role for Lambda, CORS, API key protection |
| **Serverless/FaaS** | AWS Lambda — no servers to manage |
| **Scalability** | Lambda auto-scales with each request |
| **Measured Service** | Pay-per-invocation (Free Tier: 1M requests/month) |
| **Broad Network Access** | Accessible from any browser globally |

---

### Q86. How did you secure the API key?
**Answer:** The API key is stored as a **Lambda environment variable** (`OWM_API_KEY`). In Python: `API_KEY = os.environ.get("OWM_API_KEY", "")`. It is never hardcoded in source code and never sent to the client/browser.

---

### Q87. What is Static Website Hosting on S3?
**Answer:** S3 can serve HTML/CSS/JS files as a static website directly — no web server (Apache/Nginx) needed.

Steps:
1. Enable "Static website hosting" in S3 bucket properties
2. Set `index.html` as index document
3. Make bucket public with bucket policy
4. S3 generates an endpoint URL like: `http://bucket-name.s3-website-region.amazonaws.com`

---

### Q88. What AWS Free Tier limits did you stay within?

| Service | Free Tier Limit | Our Usage |
|---|---|---|
| S3 | 5 GB storage, 20,000 GET requests/month | < 1 MB storage, few GETs |
| Lambda | 1 million requests + 400,000 GB-seconds compute/month | 1 invocation per search |
| API Gateway | 1 million calls/month | 1 call per search |
| CloudWatch Logs | 5 GB ingestion/month | Minimal logs |

**Estimated monthly cost: $0** for typical student/demo usage.

---

## ASSIGNMENTS — Comparative Studies {#assignments}

### Q89. Assignment 1: AWS vs Azure — Comparing 10 Similar Services

| # | Category | AWS Service | Azure Service |
|---|---|---|---|
| 1 | Compute (IaaS) | EC2 | Azure Virtual Machines |
| 2 | PaaS | Elastic Beanstalk | Azure App Service |
| 3 | Serverless | Lambda | Azure Functions |
| 4 | Object Storage | S3 | Azure Blob Storage |
| 5 | Archival Storage | Glacier | Azure Archive Storage |
| 6 | Relational DB | RDS | Azure SQL Database |
| 7 | NoSQL DB | DynamoDB | Azure Cosmos DB |
| 8 | Container Orchestration | EKS | Azure Kubernetes Service (AKS) |
| 9 | CDN | CloudFront | Azure CDN |
| 10 | Identity & Access | IAM | Azure Active Directory (Entra ID) |

---

### Q90. Assignment 4: Hosted vs Bare-Metal Hypervisors

| Parameter | Bare-Metal (Type 1) | Hosted (Type 2) |
|---|---|---|
| **Examples** | VMware ESXi, Hyper-V, Xen, KVM | VirtualBox, VMware Workstation |
| **Runs on** | Directly on hardware | On top of Host OS |
| **Performance** | High | Moderate (extra OS layer) |
| **Security** | Better isolation | Less isolated |
| **Use in Cloud** | AWS, Azure data centers use Type 1 | Developer workstations |
| **Cost** | Enterprise licensed (VMware) or free (KVM) | Free (VirtualBox) |
| **Hardware access** | Direct | Via Host OS |

---

### Q91. Assignment 3: Computing Technologies Comparison

| Technology | Focus | Key Trait |
|---|---|---|
| **Parallel** | Multiple processors, one problem | Speed — simultaneous computation |
| **Distributed** | Multiple computers, network | Fault tolerance, geography |
| **Cluster** | Tightly coupled group of servers | Single system image |
| **Grid** | Loosely coupled, global, shared resources | Scientific computing |
| **Cloud** | On-demand, internet, pay-per-use | Elasticity, managed services |
| **Quantum** | Qubits, quantum superposition | Complex optimization problems |

---

## QUICK REVISION CHEAT SHEET {#cheat-sheet}

### 🚀 AWS Services Used In Your Labs

| Service | What It Is | Lab Used In |
|---|---|---|
| EC2 | Virtual Machines | Lab 1 (IaaS) |
| Elastic Beanstalk | Managed PaaS | Lab 2 (PaaS) |
| S3 | Object Storage | Lab 3 + Mini Project |
| Glacier | Archival Storage | Lab 3 |
| RDS | Managed SQL DB | Lab 4 |
| DynamoDB | Managed NoSQL DB | Lab 4 |
| Lambda | Serverless Functions | Mini Project |
| API Gateway | Managed REST API | Mini Project |
| IAM | Auth & Access Control | Lab 6 + Mini Project |
| GuardDuty | Threat Detection | Lab 5 |
| Shield | DDoS Protection | Lab 5 |
| WAF | Web App Firewall | Lab 5 |
| KMS | Encryption Key Mgmt | Lab 5 |
| CloudTrail | API Audit Logs | Lab 5 |
| CloudWatch | Monitoring & Logs | Throughout |

---

### 🔢 Key Numbers to Remember

| Fact | Value |
|---|---|
| S3 Durability | 99.999999999% (11 nines) |
| S3 Availability (Standard) | 99.99% |
| Lambda max runtime | 15 minutes |
| Lambda Free Tier | 1 million requests/month |
| EC2 Free Tier | `t2.micro`, 750 hours/month |
| RDS Free Tier | `db.t2.micro`, 750 hours/month |
| NIST Cloud Characteristics | 5 (On-demand, Broad access, Resource pooling, Elasticity, Measured) |
| Cloud Service Models | 3 main: IaaS, PaaS, SaaS |
| Cloud Deployment Models | 4: Public, Private, Hybrid, Community |
| Hypervisor Types | 2: Type 1 (bare-metal), Type 2 (hosted) |

---

### 🎯 Likely Viva Questions Summary (Ranked by Importance)

**MUST KNOW (100% will be asked):**
1. What is cloud computing? 5 NIST characteristics?
2. Difference between IaaS, PaaS, SaaS — with examples
3. What is virtualization? Types of hypervisors?
4. Explain your mini project — architecture, services used, flow
5. What is Lambda and why did you use it?
6. What is S3 and how did you host the frontend?
7. What is Docker and how is it different from a VM?
8. What is IAM and what is least privilege?

**LIKELY TO BE ASKED:**
9. What is a Security Group?
10. What is CORS and why did you handle it?
11. What is Kubernetes and what is a Pod?
12. How does AWS Shared Responsibility Model work?
13. What is GuardDuty? WAF? Shield?
14. What is DynamoDB vs RDS?
15. What is an AMI? What did you use for EC2?

**BONUS (shows depth of knowledge):**
16. What is the Nitro Hypervisor? (AWS uses a custom KVM-based hypervisor)
17. What is a CDN? How would you improve this project? (Add CloudFront)
18. What is Auto Scaling? How would you add it?
19. What is a VPC? What subnets did you use?
20. What are environment variables and why are they important for security?

---

### 💬 How to Answer "Explain Your Project" in 60 Seconds

> "Sir/Ma'am, I built the SkyPulse Weather Dashboard — a web application deployed entirely on AWS Free Tier. The frontend is HTML, CSS, and JavaScript hosted on Amazon S3 as a static website. When a user searches for a city, the JavaScript makes a fetch call to our Amazon API Gateway endpoint. API Gateway routes the request to an AWS Lambda function written in Python, which securely calls the OpenWeatherMap API using an API key stored in Lambda environment variables — so the key is never exposed to the browser. The Lambda returns current weather, 5-day forecast, and hourly data, which the frontend renders with a glassmorphism UI and weather-based animated backgrounds. This project demonstrates IaaS, PaaS, Storage as a Service, Serverless computing, and Security best practices — all on AWS."

---

*Document prepared for: CSL605 Cloud Computing Viva | Mumbai University | Semester VI*
*Platform: AWS | Mini Project: SkyPulse Weather Dashboard*
