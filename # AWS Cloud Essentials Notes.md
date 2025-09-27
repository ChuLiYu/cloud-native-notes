# AWS Cloud Essentials Notes

## 1. What is Cloud Computing?
- **Definition**: On-demand delivery of compute, storage, database, applications, and IT resources via the internet, with **pay-as-you-go** pricing.
- **Traditional (On-Premises)**: Requires hardware procurement, setup, and maintenance.
- **Cloud**: Instant access, scalable, only pay for what you use.

### Advantages
- **Pay as you go**: No upfront hardware investment.
- **Economies of scale**: AWS aggregates usage → lower costs.
- **Stop guessing capacity**: Scale up/down in minutes.
- **Speed & agility**: Provision resources in minutes instead of weeks.
- **Cost savings**: Focus on innovation, not infrastructure.
- **Global reach**: Deploy worldwide in minutes → lower latency.

---

## 2. What is AWS Cloud?
- **AWS Cloud**: 200+ fully featured services (compute, storage, databases, analytics, networking, IoT, security, etc.).
- **Example**: Spin up EC2 VM with specific vCPUs/memory → pay per second.
- **Flexibility**: Provision in best Region, delete anytime.
- **Scalability**: From 1 user → 100M users.

---

## 3. On-Premises vs Cloud
- **On-Premises**:
  - Buy & install hardware
  - Cabling, power, OS installation
  - Expensive and time-consuming
- **Cloud**:
  - Replicate full environments in minutes
  - Managed over the internet
  - Remove undifferentiated heavy lifting
- **Case Study**: Clemson University ran 1.1M vCPUs on EC2 Spot in <24h.

---

## 4. Cloud Computing Models
### IaaS (Infrastructure as a Service)
- Building blocks: networking, compute, storage.
- Highest control & flexibility.
- **Example**: Amazon Lightsail.

### PaaS (Platform as a Service)
- Manage applications, not infrastructure.
- No hardware/OS patching.
- **Example**: AWS Elastic Beanstalk.

### SaaS (Software as a Service)
- Completed products managed by provider.
- **Example**: Web-based email.

---

## 5. AWS Global Infrastructure
- **Regions**: Physical locations.
- **Availability Zones (AZs)**: One or more data centers, redundant power/network.
- **Global reach**: Deploy closer to users → lower latency.

---

## 6. Developer Tools
### Ways to interact with AWS
- **Management Console**: GUI, beginner-friendly.
- **CLI**: Command-line, scriptable, reduces manual errors.
- **IDEs & Toolkits**: Cloud9, IntelliJ, VS Code, etc.
- **SDKs**: Programmatic access via Python, Java, Node.js, etc.

### Infrastructure as Code (IaC)
- **AWS CDK**: Define infra in code (TypeScript, Python, Java, etc.).
- **AWS CloudFormation**: Template-driven infra management, dependency handling.

---

## 7. Security in AWS
### AWS Responsibility
- Security **of the cloud**:
  - Physical security (data centers, AZs, hardware).
  - Networking, virtualization, host OS.

### Customer Responsibility
- Security **in the cloud**:
  - Data, applications, configurations.
  - Depends on service level (IaaS vs PaaS vs SaaS).

---

## 8. AWS Well-Architected Framework (6 Pillars)
1. **Operational Excellence**: Monitor, automate, improve processes.
2. **Security**: Protect data, manage permissions, detect threats.
3. **Reliability**: Fault tolerance, recovery planning, adapt to changes.
4. **Performance Efficiency**: Optimize resource types/sizes, monitor performance.
5. **Cost Optimization**: Avoid unnecessary spend, scale efficiently.
6. **Sustainability**: Minimize environmental impact.

---


