# GCP Lab Setup Guide
## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this GCP Lab Setup Guide is to document how the Google Cloud Platform demo environment for ShopSmart Online LLC is created, configured, reviewed, and safely managed for this cloud security portfolio project.

This guide supports a practical cloud security review by creating a small, controlled GCP environment that can be assessed for identity and access management, service accounts, storage permissions, logging, monitoring, firewall exposure, secrets management, and basic cloud governance.

This lab environment is not a production environment and must not contain real customer data, real payment data, real credentials, or confidential business information.

## 2. Lab Scenario
ShopSmart Online LLC is a fictional US-based eCommerce business that uses Google Cloud Platform to support selected parts of its online business environment.

The lab simulates a small eCommerce cloud environment with:
- A dedicated GCP project.
- Cloud IAM users and roles.
- Service accounts.
- Cloud Storage buckets.
- Cloud Logging and Audit Logs.
- Secret Manager.
- Basic networking review.
- Optional Cloud Run demo application.
- Billing alerts and cost control.
- Security Command Center Standard visibility.

The goal is not to build a full eCommerce platform. The goal is to create enough cloud resources to perform a realistic security review.

## 3. Lab Safety Rules
The following rules must be followed throughout the project:

| Rule | Requirement |
| --- | --- |
| Use dummy data only | Do not upload real customer, payment, order, or business data. |
| Use a dedicated project | Do not use a personal, production, client, or work project. |
| Control cost | Avoid expensive services and configure billing alerts. |
| Limit resources | Create only the resources needed for screenshots and security review. |
| Avoid public exposure | Do not intentionally expose sensitive data publicly. |
| Remove resources after use | Delete unused resources after screenshots and review are completed. |
| Protect credentials | Do not publish real account emails, project IDs, keys, tokens, or secrets. |
| Sanitize screenshots | Blur personal email addresses, billing details, project IDs, and sensitive identifiers before publishing. |

## 4. Lab Build Overview

The lab should be created in the following order:
1. Create dedicated GCP project
2. Configure billing budget and alerts
3. Enable required APIs
4. Create basic IAM review scenario
5. Create service accounts
6. Create Cloud Storage buckets
7. Add Secret Manager test secret
8. Enable or review Cloud Logging and Audit Logs
9. Review Security Command Center Standard
10. Create optional Cloud Run demo app
11. Capture screenshots
12. Complete security review documentation
13. Delete unnecessary resources

### 4.1 Step 1: Create Dedicated GCP Project
Create a new project in the Google Cloud Console. Recommended project details:

| Field | Recommended Value |
| --- | --- |
| Project name | GCP Security Review - ShopSmart Online |
| Project ID | gcp-security-review-shopsmart |
| Organisation | No organisation or personal lab account |
| Environment | Portfolio lab |
| Business scenario | Fictional US eCommerce business |

After creating the project, confirm that the correct project is selected before creating resources.

Important:
- Do not use an existing personal or business project.
- Do not create lab resources in a project connected to real workloads.
- Do not upload real data into this project.

### 4.2 Step 2: Configure Billing Budget and Alerts
Before creating resources, configure a billing budget.

Recommended budget: `USD 5 to USD 10`

Recommended alert thresholds:
| Alert | Threshold |
| --- | --- |
| First alert | 50% |
| Second alert | 75% |
| Final alert | 90% or 100% |

Purpose:
- Reduce the risk of unexpected charges.
- Demonstrate basic cloud governance.
- Provide a screenshot for the portfolio.

Screenshot to capture: `screenshots/billing/billing-budget-alert.png` (Soon)

Sanitize before publishing:
- Billing account ID.
- Personal email.
- Payment details.
- Any sensitive billing information.

### 4.3 Step 3: Enable Required APIs
Enable only the APIs required for the lab.

Recommended APIs:
| API / Service | Purpose |
| --- | --- |
| IAM | Review users, roles, and permissions. |
| Cloud Resource Manager | Manage project-level resources. |
| Cloud Storage | Create and review storage buckets. |
| Cloud Loggings | Review logs and audit events. |
| Cloud Monitoring | Review monitoring visibility. |
| Secret Manager | Store a dummy secret for review. |
| Security Command Center | Review standard security findings. |
| Cloud Run | Optional demo application hosting. |
| Artifact Registry | Required only if using Cloud Run container deployment. |

Avoid enabling unnecessary services. Do not enable expensive services unless required.

### 4.4 Step 4: Create IAM Review Scenario
The IAM review scenario should show realistic access control issues and improvement opportunities.

Recommended IAM roles to review:
| Role Type | Example |
| --- | --- |
| Project Owner | High-risk privileged access. |
| Editor | Broad access that may be excessive. |
| Viewer | Read-only access. |
| Storage Admin | Storage management access. |
| Logging Viewer | Log review access. |
| Security Reviewer | Security review access. |
| Service Account User | Ability to act as service accounts. |

For this portfolio project, it is enough to review your own account and service accounts. Do not invite unnecessary external users.

If you want to simulate a contractor, use a placeholder in documentation instead of giving real access to another person.

Example fictional IAM users:
| Fictional User | Role |
| --- | --- |
| Cloud Administrator | Project Owner |
| Internal Developer | Cloud Run Developer |
| External Developer Contractor | Limited application deployment access |
| Finance Manager | Billing viewer |
| Security Reviewer | Security Reviewer / Logging Viewer |

These users can be represented in documentation without creating real accounts.

Screenshots to capture:
`screenshots/iam/iam-overview.png` (Soon)
`screenshots/iam/iam-roles-review.png` (Soon)

Sanitize before publishing:
- Email addresses.
- Project number.
- Project ID if you prefer to hide it.
- Any personal account details.

### 4.5 Step 5: Create Service Accounts
Create service accounts to support the lab scenario.

Recommended service accounts:
| Service Account | Purpose |
| --- | --- |
| shopsmart-cloudrun-sa | Used by optional Cloud Run demo app. |
| shopsmart-storage-review-sa | Used to demonstrate storage-related access review. |
| shopsmart-logging-review-sa | Used to demonstrate logging access review. |

Service account review should check:
- Whether the service account is still needed.
- What roles are assigned.
- Whether roles are too broad.
- Whether service account keys exist.
- Whether keys are unnecessary.
- Whether the account follows least privilege.
- Whether the account has owner/editor permissions.

Important:
- Avoid creating service account keys unless needed for the review.
- Do not publish service account keys.
- Delete any test keys immediately after screenshots if created.

Screenshots to capture:
`screenshots/iam/service-accounts-overview.png` (Soon)
`screenshots/iam/service-account-permissions.png` (Soon)
