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
