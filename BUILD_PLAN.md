# Build Plan — CLF-C02 Hands-On Track

Four free-tier projects, two per week over two weeks, at roughly 10 hours per week. Each project owns one exam domain so that building the project doubles as studying for it. Nothing here is complete yet — checkboxes track real progress.

---

## Sequencing

1. **Day 1, before anything billable:** complete the Budget alarm setup from Project 4 first. This protects against surprise charges on EC2/RDS later.
2. **Week 1:** Project 1, then Project 2 (both effectively free, lowest risk, fastest confidence wins).
3. **Week 2:** Project 3 (the only project with real billing exposure), then finish the Project 4 writeup last so it can review the VPC you just built.
4. Publish each project as you finish it — README + diagram + LinkedIn post — rather than batching at the end.

---

## Project 1 — Static site on S3 + CloudFront + Route 53

**Objective:** Host a static site in an S3 bucket, serve it through CloudFront with HTTPS via an ACM certificate, and point an owned domain at it through Route 53.

**Core services:** S3, CloudFront, Route 53, ACM, IAM (bucket policy / origin access control)

**Domains covered:** Cloud Technology and Services (storage, CDN, DNS) · Cloud Concepts (global infrastructure, edge locations, regions/AZs) · light Security (encryption in transit and at rest)

**Free-tier safety:** S3 within the always-free 5 GB allowance; CloudFront within the always-free 1 TB allowance; Route 53 hosted zone is a small fixed monthly cost. Low risk.

**Estimated time:** 4–5 hours

**Build checklist**
- [ ] Create an S3 bucket and enable static website hosting
- [ ] Upload site content (reuse portfolio content or a fresh landing page)
- [ ] Block public bucket access and serve only through CloudFront (origin access control)
- [ ] Request an ACM certificate for the domain (HTTPS)
- [ ] Create a CloudFront distribution with the S3 origin
- [ ] Create/point a Route 53 record at the distribution
- [ ] Confirm the live HTTPS URL resolves

**Publish checklist**
- [ ] Architecture diagram (User → Route 53 → CloudFront → S3)
- [ ] Project README with the live URL and design notes
- [ ] LinkedIn post with a console screenshot

---

## Project 2 — IAM and account-hardening security lab

**Objective:** Build a realistic least-privilege identity setup in IAM, harden the account, and document it against the Shared Responsibility Model.

**Core services:** IAM (users, groups, roles, policies), MFA, CloudTrail, IAM Access Analyzer

**Domains covered:** Security and Compliance (30% — second-heaviest domain). Shared Responsibility Model, IAM, MFA, least privilege.

**Free-tier safety:** IAM is free; first CloudTrail trail is free. No real billing risk.

**Estimated time:** 4–5 hours

**Build checklist**
- [ ] Create IAM users grouped by job function
- [ ] Write at least one custom least-privilege policy by hand (JSON)
- [ ] Enforce MFA on users
- [ ] Create a cross-service role (e.g., EC2 instance role that can read one S3 bucket)
- [ ] Enable CloudTrail
- [ ] Run IAM Access Analyzer and review findings
- [ ] Write the Shared Responsibility Model in your own words against what you built

**Publish checklist**
- [ ] Repo with custom policy JSON files
- [ ] SHARED_RESPONSIBILITY.md
- [ ] Short writeup on least-privilege decisions and why
- [ ] LinkedIn post

---

## Project 3 — Multi-AZ VPC with EC2 and RDS

**Objective:** Build a two-tier network from scratch with public and private subnets across two availability zones; web-tier EC2 in public, RDS in private, locked down so only the EC2 security group can reach the database.

**Core services:** VPC, subnets, internet gateway, route tables, security groups, network ACLs, EC2, RDS

**Domains covered:** Cloud Technology and Services (34% — largest domain) · Cloud Concepts (high availability across AZs)

**Free-tier safety:** This is the one project with real billing exposure. EC2 and RDS draw from the credit pool, not always-free. Stop or terminate both immediately after screenshots. Rely on the budget alarm from Project 4, set up first. Completes two of the five credit-earning onboarding tasks (EC2 + RDS).

**Estimated time:** 5–6 hours

**Build checklist**
- [ ] Create a VPC with public + private subnets across two AZs
- [ ] Attach an internet gateway and configure route tables
- [ ] Configure security groups and network ACLs
- [ ] Launch a web-tier EC2 instance in a public subnet
- [ ] Launch an RDS database in a private subnet
- [ ] Restrict the DB security group to the EC2 security group only
- [ ] Verify connectivity, capture screenshots
- [ ] **Stop / terminate EC2 and RDS**

**Publish checklist**
- [ ] Architecture diagram (subnets, AZs, gateway, security-group flow)
- [ ] Project README explaining each design choice
- [ ] LinkedIn post with the diagram

---

## Project 4 — Cost governance and Well-Architected review

**Objective:** Stand up cost guardrails, tag resources, review costs, and write a Well-Architected self-review of the VPC project.

**Core services:** AWS Budgets, Cost Explorer, CloudWatch (billing alarm), SNS, cost-allocation tags, Trusted Advisor, Pricing Calculator

**Domains covered:** Billing, Pricing, and Support (12%) · Cloud Concepts (Well-Architected Framework, part of 24%)

**Free-tier safety:** All free / always-free. Budget setup completes another credit-earning onboarding task.

**Estimated time:** ~4 hours

**Build checklist (do the budget alarm on Day 1)**
- [ ] Create an AWS Budget with email alerts **(Day 1)**
- [ ] Create a CloudWatch billing alarm wired to an SNS email topic **(Day 1)**
- [ ] Apply cost-allocation tags across resources from the other projects
- [ ] Pull a Cost Explorer report
- [ ] Review Trusted Advisor checks
- [ ] Estimate a production version of Project 3 in the Pricing Calculator
- [ ] Write a Well-Architected self-review of the VPC against the pillars

**Publish checklist**
- [ ] COST_GOVERNANCE.md with budget + alarm screenshots
- [ ] Tagging scheme documented
- [ ] Well-Architected review writeup
- [ ] LinkedIn post

---

## Domain coverage matrix

P = primary owner, S = secondary coverage.

| Domain (weight) | P1 Static site | P2 IAM lab | P3 VPC/EC2/RDS | P4 Cost/WA |
|---|---|---|---|---|
| Cloud Concepts (24%) | S | — | S | P |
| Security and Compliance (30%) | S | P | S | — |
| Cloud Technology and Services (34%) | P | — | P | — |
| Billing, Pricing, and Support (12%) | — | — | — | P |

Core service coverage: **S3** (P1), **IAM** (P2), **VPC + EC2 + RDS** (P3), billing tooling (P4). All five exam-critical services covered.
