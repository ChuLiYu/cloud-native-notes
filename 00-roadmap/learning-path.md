# Learning Path — Cloud-Native Notes

> Roadmap toward backend/cloud engineering roles in North American big tech companies.  
> Focus areas: AWS, Kubernetes, IaC, Distributed Systems, Observability.

---

## Phase 1: AWS Foundations (Weeks 1–4)
**Topics**
- Cloud Essentials: IaaS/PaaS/SaaS, global infrastructure (Regions/AZs)
- IAM basics (users, roles, policies), least privilege
- Networking: VPC, subnets, routing, SG/NACL
- Compute & Storage: EC2, S3 (classes, lifecycle), ECS/Fargate overview

**Hands-on**
- Lightsail LAMP deploy
- Free Tier guardrails (billing alarms, budgets)

**Deliverables**
- Notes: `01-aws/notes/*`
- Labs: `01-aws/labs/lightsail-lamp.md`, `free-tier-usage-guardrails.md`

---

## Phase 2: Kubernetes & Containers (Weeks 5–8)
**Topics**
- Core objects: Pod, Deployment, Service
- Config: ConfigMap, Secret
- Networking: CNI, Ingress, Service types
- Security & multi-tenancy: RBAC, Namespaces

**Hands-on**
- Minikube local cluster
- Containerize a simple API; expose via Ingress

**Deliverables**
- Notes: `02-kubernetes/notes/*`
- Labs: `02-kubernetes/labs/minikube-local-setup.md`

---

## Phase 3: Infrastructure as Code (Weeks 9–12)
**Topics**
- Terraform: providers, resources, variables, state, modules
- AWS CDK (TS/Python): stacks, constructs, CI integration
- CloudFormation snippets & change sets

**Hands-on**
- Terraform → S3 static site with versioning + CloudFront (optional)
- CDK → ECS Fargate service (public endpoint)

**Deliverables**
- `03-iac/terraform/examples/01-s3-static-site/`
- `03-iac/cdk/examples/ts-ecs-fargate-sample/`

---

## Phase 4: Distributed Systems (Weeks 13–16)
**Topics**
- CAP theorem; consistency models (strong, eventual, causal)
- Sharding & consistent hashing; quorum: `R + W > N`
- Messaging & streaming: Kafka concepts (topic, partition, consumer group)

**Hands-on**
- Model a read-heavy vs write-heavy workload; pick storage patterns
- Kafka local demo: keyed partitioning + consumer groups

**Deliverables**
- Notes: `04-distributed-systems/notes/*`
- Patterns: `04-distributed-systems/patterns/*`

---

## Phase 5: Observability (Weeks 17–20)
**Topics**
- Logging: structured logs, correlation IDs
- Metrics: SLI/SLO; RED/USE methods
- Tracing: OpenTelemetry, context propagation

**Hands-on**
- Run OTel Collector locally; export to Jaeger/Prometheus
- Instrument demo app for logs/metrics/traces

**Deliverables**
- Notes: `05-observability/notes/*`
- Lab: `05-observability/labs/otel-collector-local.md`

---

## Phase 6: Projects (Weeks 21+)
**Project 1 — URL Shortener (Cloud-Native)**
- Microservices, IaC (Terraform/CDK), K8s/EKS or ECS, OTel
- CI/CD pipeline, cost + teardown scripts

**Project 2 — Event-Driven Orders**
- Kafka (or MSK), Lambda, DynamoDB; idempotency & exactly-once semantics (as feasible)

**Deliverables**
- `07-projects/01-url-shortener-cloudnative/`
- `07-projects/02-event-driven-orders/`
- Diagrams in `08-diagrams/`

---

## Long-Term Direction
- Multi-region & failover; data sovereignty
- Service Mesh (Istio/Linkerd)
- Cost optimization playbook
- Certifications: AWS SAA → SAP; CKA/CKAD

---

## Tracking
Maintain progress in `00-roadmap/progress-checklist.md` (checkboxes per topic/lab/project).
