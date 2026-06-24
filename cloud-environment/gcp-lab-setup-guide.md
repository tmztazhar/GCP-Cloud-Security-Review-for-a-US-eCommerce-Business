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
- `screenshots/iam/iam-overview.png` (Soon)
- `screenshots/iam/iam-roles-review.png` (Soon)

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
- `screenshots/iam/service-accounts-overview.png` (Soon)
- `screenshots/iam/service-account-permissions.png` (Soon)

### 4.6 Step 6: Create Cloud Storage Buckets
Create one or two Cloud Storage buckets for review.

Recommended buckets:
| Bucket Name Example | Purpose |
| --- | --- |
| shopsmart-product-images-lab | Simulates public or semi-public product images. |
| shopsmart-order-documents-lab | Simulates sensitive order-related documents using dummy data only. |

Use dummy files only.

Example dummy files:
- `sample-product-image-placeholder.txt`
- `dummy-order-record.csv`
- `sample-shipping-note.txt`

Do not upload:
- Real customer names.
- Real addresses.
- Real order records.
- Real payment information.
- Real invoices.
- Real credentials.

Security review checks:
- Is public access prevention enabled?
- Are bucket permissions appropriate?
- Are object permissions appropriate?
- Are unnecessary users granted access?
- Is uniform bucket-level access enabled?
- Is versioning required?
- Is retention required?
- Is the bucket labelled or named clearly?
- Is sensitive data separated from public data?

Screenshots to capture:
- `screenshots/storage/storage-buckets-overview.png` (Soon)
- `screenshots/storage/bucket-permissions-review.png` (Soon)
- `screenshots/storage/public-access-prevention.png` (Soon)

### 4.7 Step 7: Create Dummy Secret in Secret Manager
Create one dummy secret to demonstrate secrets management review.

Recommended secret name: `shopsmart-demo-api-key`

Recommended dummy value: `dummy-api-key-do-not-use`

Do not store:
- Real API keys.
- Real passwords.
- Real database credentials.
- Real tokens.
- Real OAuth secrets.

Security review checks:
- Is the secret stored in Secret Manager instead of code or files?
- Who can access the secret?
- Are permissions limited?
- Is access logged?
- Is rotation considered?
- Are old secret versions disabled or destroyed when no longer needed?

Screenshots to capture:
- `screenshots/secrets/secret-manager-overview.png` (Soon)
- `screenshots/secrets/secret-permissions-review.png` (Soon)

Sanitize before publishing:
- Do not show the secret value.
- Do not show sensitive project identifiers.

### 4.8 Step 8: Review Cloud Logging and Audit Logs
Review logging visibility for the lab project.

Areas to review:
| Area | Review Question |
| --- | --- |
| Admin Activity logs | Can administrative actions be reviewed? |
| Data Access logs | Are data access logs enabled where appropriate? |
| Log Explorer | Can IAM, storage, and service account activity be found? |
| Alerting | Are important alerts configured? |
| Retention | Is default retention understood? |
| Access | Who can view logs? |

Example activities to generate logs:
- Create a storage bucket.
- Update bucket permissions.
- Create a service account.
- Add or remove an IAM role.
- Create a dummy secret.
- Deploy optional Cloud Run service.

Screenshots to capture:
- `screenshots/logging/log-explorer-admin-activity.png` (Soon)
- `screenshots/logging/audit-log-review.png` (Soon)
- `screenshots/logging/logging-permissions.png` (Soon)

Sanitize before publishing:
- Email addresses.
- IP addresses if shown.
- Project ID if required.
- Any sensitive log content.

### 4.8 Step 8: Review Cloud Logging and Audit Logs
Review logging visibility for the lab project. Areas to review:

| Area | Review Question |
| --- | --- |
| Admin Activity Logs | Can administrative actions be reviewed? |
| Data Access Logs | Are data access logs enabled where appropriate? |
| Log Explorer | Can IAM, storage, and service account activity be found? |
| Alerting | Are important alerts configured? |
| Retention | Is default retention understood? |
| Access | Who can view logs? |

Example activities to generate logs:
- Create a storage bucket.
- Update bucket permissions.
- Create a service account.
- Add or remove an IAM role.
- Create a dummy secret.
- Deploy optional Cloud Run service.

Screenshots to capture:
- `screenshots/logging/log-explorer-admin-activity.png` (Soon)
- `screenshots/logging/audit-log-review.png` (Soon)
- `screenshots/logging/logging-permissions.png` (Soon)

Sanitize before publishing:
- Email addresses.
- IP addresses if shown.
- Project ID if required.
- Any sensitive log content.

### 4.9 Step 9: Review Security Command Center Standard
Use Security Command Center Standard to review available findings.

Review questions:
- Are there any active findings?
- Are findings relevant to IAM, storage, networking, or service accounts?
- Are findings prioritised?
- Is Security Command Center enabled for the project?
- Are findings understood by a business user?
- Are recommendations documented?

Screenshots to capture:
- `screenshots/security-command-center/scc-overview.png` (Soon)
- `screenshots/security-command-center/scc-findings.png` (Soon)

If there are no findings, document that no findings were observed during the review period.

### 4.10 Step 10: Review VPC Firewall Rules
Review default VPC firewall rules and any lab-created rules.

Review questions:
- Are there firewall rules allowing access from 0.0.0.0/0?
- Are SSH, RDP, HTTP, or HTTPS rules exposed?
- Are unused firewall rules present?
- Are rules clearly named?
- Are rules required for the lab?
- Are broad rules justified?

For this portfolio project, avoid creating unnecessary Compute Engine VMs.

If no VM is created, the firewall review can still discuss default VPC exposure and whether the project uses public compute resources.

Screenshots to capture:
- `screenshots/networking/vpc-firewall-rules.png` (Soon)

### 4.11 Step 11: Optional Cloud Run Demo App
Cloud Run is optional. Use it only if you want a simple application hosting example for screenshots.

Possible demo app: `Simple static "ShopSmart Demo Store" web service`

Review questions:
- Is the service publicly accessible?
- Does the service use a dedicated service account?
- Does the service account have least privilege?
- Are logs available?
- Are environment variables used safely?
- Are secrets stored in Secret Manager instead of plain text?
- Is unauthenticated access required or unnecessary?

Screenshots to capture:
- `screenshots/cloud-run/cloud-run-service-overview.png`
- `screenshots/cloud-run/cloud-run-permissions.png`
- `screenshots/cloud-run/cloud-run-logs.png`

Important:
- Do not deploy a real eCommerce app.
- Do not connect to real payment systems.
- Do not store real customer data.
- Delete the service when no longer needed.

### 4.12 Step 12: Labels and Governance
Apply simple labels to lab resources where supported.

Recommended labels:
| Label Key | Label Value |
| --- | --- |
| environment | lab |
| project | gcp-security-review |
| business | ecommerce |
| owner | cloud-security-analyst |

Review questions:
- Are resources labelled?
- Can the business identify ownership?
- Can cost and security review scope be understood?
- Are lab resources separated from production-like resources?

### 4.13 Step 13: Screenshots Checklist
Capture screenshots for evidence.

| Area | Screenshot |
| --- | --- |
| Project overview | GCP project dashboard |
| Biling | Budget and alert configuration |
| IAM | IAM permissions overview |
| IAM | Service accounts overview |
| Storage | Bucket list |
| Storage | Bucket permissions |
| Storage | Public access prevention |
| Secrets | Secret Manager overview |
| Logging | Log Explorer showing admin activity |
| Logging | Audit log review |
| Security | Security Command Center overview |
| Networking | VPC firewall rules |
| Cloud Run | Optional service overview |
| Cloud Run | Optional service logs |

Before publishing screenshots:
- Blur personal email addresses.
- Blur billing information.
- Blur project number if required.
- Blur any tokens, secrets, keys, or internal identifiers.
- Do not show real credentials or real customer information.

### 4.14 Step 14: Resource Cleanup
After completing screenshots and review documentation, delete unused resources.

Cleanup checklist:
| Resource | Action |
| --- | --- |
| Cloud Run service | Delete if no longer required. |
| Cloud Storage test buckets | Delete after screenshots and review. |
| Dummy files | Delete from buckets. |
| Secret Manager dummy secret | Destroy or delete. |
| Service account keys | Delete immediately if created. |
| Service accounts | Delete if no longer required. |
| Test IAM access | Remove unnecessary roles. |
| Firewall rules | Remove unnecessary lab-created rules. |
| Budgets | Keep if project remains active. |
| GCP project | Shut down project if no longer needed. |

Important:

If the project is no longer needed, shutting down the entire GCP project is the safest way to stop future charges.
