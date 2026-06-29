# AWS Certified Cloud Practitioner (CLF-C02) — Hands-On Build Track

A public, in-progress trail of my preparation for the AWS Certified Cloud Practitioner exam (CLF-C02). Instead of studying from videos alone, I'm backing every exam domain with a small, free-tier AWS project I build and document. Each project is scoped to own one of the four exam domains so that building doubles as studying.

**Status:** In progress — studying and building. Projects below are planned; this repo will fill in as each ships.

**By:** Mason · GitHub [@M6Jet](https://github.com/M6Jet) · Portfolio [m6jet.github.io](https://m6jet.github.io)

---

## Why this repo exists

The CLF-C02 is a foundational, mostly conceptual exam, but candidates who pair the reading with hands-on labs consistently outperform those who only watch videos. The four projects here are deliberately chosen so that, together, they cover all four exam domains in proportion to their weighting and touch every one of the five core services the exam fixates on: **EC2, S3, VPC, IAM, RDS** — plus the billing and cost tooling.

## The exam at a glance

| Domain | Weight | Owned by |
|---|---|---|
| Cloud Concepts | 24% | Project 1 + Project 4 |
| Security and Compliance | 30% | Project 2 |
| Cloud Technology and Services | 34% | Project 3 (with Project 1) |
| Billing, Pricing, and Support | 12% | Project 4 |

Passing score: 700 / 1000. Format: 65 questions, 90 minutes. No penalty for guessing.

## The four projects

| # | Project | Core services | Primary domain | Status |
|---|---|---|---|---|
| 1 | Static site on S3 + CloudFront + Route 53 | S3, CloudFront, Route 53, ACM, IAM | Cloud Technology / Cloud Concepts | Planned |
| 2 | IAM and account-hardening security lab | IAM, MFA, CloudTrail, Access Analyzer | Security and Compliance | Planned |
| 3 | Multi-AZ VPC with EC2 and RDS | VPC, EC2, RDS, Security Groups, NACLs | Cloud Technology and Services | Planned |
| 4 | Cost governance and Well-Architected review | Budgets, Cost Explorer, CloudWatch, SNS | Billing / Cloud Concepts | Planned |

Full scope, checklists, and the domain-coverage matrix live in [BUILD_PLAN.md](./BUILD_PLAN.md). Live progress and study tracking live in [PROGRESS.md](./PROGRESS.md).

## Repo structure (fills in as projects ship)

```
.
├── README.md              <- you are here
├── BUILD_PLAN.md          <- detailed plan, checklists, domain matrix
├── PROGRESS.md            <- living tracker for build + study + posts
├── 01-static-site-s3/     <- Project 1 (coming)
├── 02-iam-security-lab/   <- Project 2 (coming)
├── 03-vpc-ec2-rds/        <- Project 3 (coming)
└── 04-cost-governance/    <- Project 4 (coming)
```

Each project folder will ship with a README, an architecture diagram, the relevant config or policy files, and console/terminal screenshots.

## A note on cost (AWS Free Tier, 2025+ model)

New AWS accounts (created after July 15, 2025) get $100 in credits at sign-up plus up to $100 more by completing onboarding tasks (launch EC2, configure RDS, deploy Lambda, try Bedrock, set a Budget), on a free plan that lasts up to 6 months or until credits run out. Those onboarding tasks overlap directly with Projects 3 and 4. A budget alarm is set up before any billable resource is launched, and EC2/RDS are stopped or terminated immediately after screenshots. S3, CloudFront, IAM, Budgets, and CloudWatch work used here stays within always-free limits.

## License

MIT
