# Cloud Environment Overview
## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this Cloud Environment Overview is to describe the Google Cloud Platform environment used for the ShopSmart Online LLC cloud security review.

This document provides a clear summary of the GCP project structure, cloud services, information assets, users, service accounts, security controls, logging visibility, and review boundaries.

It supports the security review by explaining what exists in the lab environment before findings, risks, and recommendations are documented.

## 2. Environment Summary
ShopSmart Online LLC is a fictional US eCommerce business using a small GCP environment for selected cloud workloads.

The lab environment is designed to simulate a realistic SME cloud environment without creating a full production eCommerce platform.

The environment includes:
- One dedicated GCP project.
- Cloud IAM users and roles.
- Service accounts.
- Cloud Storage buckets.
- Secret Manager.
- Cloud Logging and Cloud Audit Logs.
- Security Command Center Standard.
- VPC firewall rules.
- Billing budget and alerts.
- Optional Cloud Run demo application.

This environment is used only for portfolio, learning, and cloud security review purposes.

## 3. Environment Type
| Item | Description |
| --- | --- |
| Environment name | ShopSmart GCP Security Lab |
| Cloud provider | Google Cloud Platform |
| Business type | US eCommerce |
| Environment purpose | Portfolio lab and security review |
| Production status | Non-production |
| Data type | Dummy data only |
| Payment processing | Not included |
| Customer data | Not included |
| Main review focus | IAM, storage, logging, service accounts, secrets, governance, and exposure review |

## 4. GCP Project Details
| Field | Example Value |
| --- | --- |
| Project display name | GCP Security Review - ShopSmart Online |
| Project ID | gcp-security-review-shopsmart |
| Project purpose | Cloud security review lab |
| Project owner | Cloud Security Analyst |
| Business owner | Fictional Operations Manager |
| Technical owner | Fictional IT Administrator |
| Environment classification | Lab |
| Data classification | Dummy / non-production |
| Biling status | Billing enabled with budget alert |
| Review status | In scope for portfolio security review |

Before publishing screenshots, project IDs, project numbers, billing details, and personal email addresses should be blurred or removed.

## 5. High-Level Architecture
The lab environment follows a simple cloud architecture:

<img width="408" height="349" alt="High-Level Architecture" src="https://github.com/user-attachments/assets/261b14d2-cb5e-47cc-8906-12957d5b7dbd" />

The environment is intentionally simple because the goal is to assess cloud security controls, not to build a full production eCommerce system.

## 6. Cloud Services in Scope
| GCP Service | Purpose in Lab | Security Review Focus |
| --- | --- | --- |
| IAM | Manage users, roles, and access permissions. | Least privilege, privileged access, external users, role assignment. |
| Service Accounts | Support application or automation access. | Overprivileged service accounts, unused accounts, key exposure. |
| Cloud Storage | Store dummy product and order-related files. | Public access, bucket permissions, uniform access, versioning. |
| Secret Manager | Store dummy API key or application secret. | Secret access, permissions, storage method, rotation considerations. |
| Cloud Logging | Record activity and operational events. | Log visibility, admin actions, useful evidence for investigation. |
| Cloud Audit Logs | Record administrative and data access activity. | Audit coverage, investigation readiness, sensitive activity visibility. |
| Cloud Monitoring | Basic visibility and alerting. | Monitoring readiness and incident visibility. |
| Security Command Center Standard | Security posture visibility. | Findings review and prioritisation. |
| VPC Firewall Rules | Review network exposure. | Broad access, unnecessary rules, public exposure. |
| Cloud Run | Optional demo web application. | Public access, service identity, logs, configuration review. |
| Biling | Cost governance. | Budget alerts and cost control. |

## 7. Cloud Services Out of Scope
| GCP Service / Area | Reason |
| --- | --- |
| GKE | Avoided due to cost and complexity for this SME portfolio lab. |
| Large Compute Engine deployment | Not required for the review objective. |
| Large Cloud SQL deployment | Optional only; not required for the core project. |
| BigQuery heavy workloads | Avoided to prevent unnecessary cost. |
| Payment processing systems | No real payment or PCI review is included. |
| Production CI/CD pipelines | Not required for this project. |
| Enterprise SIEM integration | Not realistic for this SME scenario. |
| Paid Security Command Center tiers | Free or standard visibility is sufficient for this project. |
| Penetration testing | The project focuses on security review and governance. |

## 8. Information Assets in the Environment
| Information Asset | Example | Classification | Business Importance |
| --- | --- | --- | --- |
| Dummy customer records | Sample name, email, and shipping address data using fake values only | Confidential in scenario | High |
| Dummy order records | Sample order ID and delivery status | Confidential in scenario | High |
| Product catalogue files | Sample product image or text placeholder | Public or Internal | Medium |
| Application configuration | Demo configuration values | Internal | Medium |
| Dummy API secret | Fake API key stored in Secret Manager | Restricted in scenario | High |
| IAM configuration | Users, roles, and permissions | Restricted | High |
| Service account configuration | Service account names, roles, and access | Restricted | High |
| Audit logs | Administrative and access activity | Confidential | High |
| Biling alerts | Budget and cost alert configuration | Internal | Medium |
| Security findings | Security Command Center observations | Confidential | High |

No real customer data, payment information, credentials, or business records should be stored in the lab.

## 9. User and Access Model
The environment uses a simple access model suitable for a small business.

| Role | Fictional Responsibility | Expected Access |
| --- | --- | --- |
| Cloud Administrator | Manages the GCP project and core configuration. | Project administration access. |
| Security Reviewer | Reviews IAM, logging, storage, and security findings. | Read-only security and logging access. |
| Internal Developer | Supports optional Cloud Run demo app. | Limited deployment access. |
| External Developer Contractor | Supports application updates temporarily. | Time-limited and least-privilege access. |
| Finance Manager | Reviews billing and budget alerts. | Billing viewer access. |
| Operations Manager | Business owner for the environment. | Summary reporting and risk ownership. |

For the actual portfolio lab, these roles may be represented in documentation without inviting real external users.

## 10. Service Account Model
The lab may include the following service accounts:

| Service Account | Intended Use | Security Review Focus |
| --- | --- | --- |
| shopsmart-cloudrun-sa | Used by optional Cloud Run demo app. | Confirm least privilege and no unnecessary broad roles. |
| shopsmart-storage-review-sa | Used to simulate storage-related access. | Review storage role assignment and necessity. |
| shopsmart-logging-review-sa | Used to simulate log access or review activity. | Confirm whether access is needed and limited. |

Service account review should check:
- Whether the service account is still required.
- Whether the account has excessive roles.
- Whether service account keys exist.
- Whether keys are avoidable.
- Whether the service account is used by a specific workload.
- Whether the service account has owner or editor permissions.
- Whether the account follows least privilege.

## 11. Storage Model
The lab may include two Cloud Storage buckets.

| Bucket | Purpose | Expected Classification | Security Expectation |
| --- | --- | --- | --- |
| shopsmart-product-images-lab | Stores dummy product image placeholders. | Public or Internal | Public access must be intentional and documented. |
| shopsmart-order-documents-lab | Stores dummy order-related sample files. | Confidential in scenario | Public access should be blocked. |

Storage review should confirm:
- Public access prevention status.
- Uniform bucket-level access status.
- Bucket IAM permissions.
- Object-level permissions.
- External access.
- Versioning needs.
- Retention needs.
- Whether sensitive and public data are separated.

## 12. Secrets Model
The lab may include one dummy secret.

| Secret Name | Purpose | Classification | Security Expectation |
| --- | --- | --- | --- |
| shopsmart-demo-api-key | Demonstrates Secret Manager review. | Restricted in scenario | Access must be limited and logged. |

The secret value must be fake, for example: `dummy-api-key-do-not-use`

The secret review should confirm:
- The secret is not stored in code.
- Access is limited to authorised accounts.
- Secret access is logged.
- Rotation is considered.
- Old versions are removed when no longer needed.
- Secret values are not shown in screenshots.

## 13. Logging and Monitoring Model
Logging and monitoring are important for cloud investigation and security visibility.

The review should consider:
| Logging Area | Review Question |
| --- | --- |
| Admin Activity Logs | Can administrative changes be reviewed? |
| IAM activity | Can role changes and permission changes be investigated? |
| Storage activity | Can bucket changes or access changes be reviewed? |
| Service account activity | Can service account creation and key activity be reviewed? |
| Secret Manager activity | Can secret access and changes be reviewed? |
| Cloud Run Logs | Are application logs available if Cloud Run is used? |
| Alerting | Are alerts configured for important risks? |
| Log access | Who can view sensitive logs? |

The project should include screenshots from Cloud Logging or Log Explorer where possible.

## 14. Security Command Center Model 
Security Command Center Standard is used for basic cloud security visibility. Review focus:
- Whether Security Command Center is enabled.
- Whether active findings exist.
- Whether findings are relevant to IAM, storage, network, or service accounts.
- Whether findings are understood and prioritised.
- Whether findings are linked to recommendations.

If no findings are present, the review should state that no findings were observed during the review period.

## 15. Network and Exposure Model
The lab does not require a complex network design. Network review should focus on:
- Default VPC firewall rules.
- Any rules allowing access from `0.0.0.0/0`.
- Whether SSH or RDP exposure exists.
- Whether HTTP or HTTPS exposure is required.
- Whether unused rules are present.
- Whether Cloud Run public access is intentional.
- Whether public endpoints are documented.

The review should avoid creating unnecessary virtual machines or public services purely for screenshots.

## 16. Cloud Run Model
Cloud Run is optional. If used, the demo service should be simple, such as: `ShopSmart Demo Store`

Review focus:
- Is unauthenticated access enabled?
- Is public access required?
- Which service account is used?
- Does the service account have least privilege?
- Are logs available?
- Are secrets handled securely?
- Are environment variables safe?
- Is the service labelled?
- Is the service deleted after the project if no longer needed?

Cloud Run should not connect to real customer data, payment systems, or production APIs.

## 17. Cost Governance
Cost governance is included to demonstrate practical cloud management. Minimum cost controls:

| Control | Purpose |
| --- | --- |
| Biling budget | Limits unexpected cost exposure. |
| Budget alerts | Notifies when spending reaches selected thresholds. |
| Limited resources | Prevents unnecessary services from running. |
| No expensive workloads | Avoids GKE, GPUs, large VMs, or large databases. |
| Cleanup checklist | Removes unused resources after review. |

Recommended budget: `USD 5 to USD 10`

## 18. Labels and Ownership
Resources should be labelled where supported. Recommended labels:

| Label Key | Example Value |
| --- | --- |
| environment | lab |
| project | gcp-security-review |
| business | ecommerce |
| owner | cloud-security-analyst |

Labels help demonstrate:
- Cloud governance.
- Resource ownership.
- Environment separation.
- Cost tracking.
- Review scope clarity.

## 19. Review Boundaries
This project reviews the configuration and governance of the lab environment. The review does not include:
- Exploitation.
- Penetration testing.
- Vulnerability scanning against public targets.
- Production workload review.
- PCI DSS validation.
- Legal assessment.
- Real customer data handling.
- Real payment system assessment.

This keeps the project safe, realistic, and appropriate for a public portfolio.

## 20. Screenshot Evidence Plan
The following screenshots should be collected for the portfolio:

| Area | Screenshot |
| --- | --- |
| Project | GCP project dashboard |
| Biling | Budget and alert configuration |
| IAM | IAM roles and principals |
| IAM | Service accounts |
| Storage | Bucket list |
| Storage | Bucket permissions |
| Storage | Public access prevention |
| Secrets | Secret Manager overview |
| Logging | Log Explorer admin activity |
| Logging | Audit log example |
| Security | Security Command Center overview |
| Networking | VPC firewall rules |
| Cloud Run | Optional service overview |
| Cloud Run | Optional service logs |

Screenshots must be reviewed and sanitised before publishing.

## 21. Environment Cleanup Plan
At the end of the project, unused resources should be removed. Cleanup should include:
- Delete optional Cloud Run service.
- Delete Cloud Storage buckets and dummy files.
- Delete dummy Secret Manager secret.
- Delete unnecessary service accounts.
- Delete any service account keys immediately.
- Remove unnecessary IAM roles.
- Remove lab-created firewall rules.
- Shut down the GCP project if it is no longer needed.

Shutting down the project is the safest way to prevent future charges.

## 22. Portfolio Note
This Cloud Environment Overview is part of a fictional cloud security portfolio project. It demonstrates cloud environment scoping, review boundary definition, service inventory, security ownership, and safe lab planning for a US eCommerce business scenario.

This document does not represent a production architecture, formal compliance audit, penetration test, or legal assessment.
