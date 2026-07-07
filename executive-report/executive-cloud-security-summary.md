# Executive Cloud Security Summary

## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Reviewed By: Fictional Operations Manager
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Executive Overview

ShopSmart Online LLC is a fictional US-based small-to-medium eCommerce business using Google Cloud Platform to support selected cloud services, including application hosting, storage, identity and access management, logging, secrets management, and basic cloud governance.

The purpose of this cloud security review is to assess the security posture of a realistic GCP lab environment and provide practical recommendations that reduce business risk without requiring enterprise-level tooling.

The review focuses on key cloud security areas that are highly relevant to a small eCommerce business:
- IAM and privileged access.
- Service account permissions.
- Service account key exposure.
- Cloud Storage permissions.
- Secret Manager access.
- Cloud Logging and Audit Logs.
- Security Command Center findings.
- VPC firewall exposure.
- Billing budget alerts.
- Contractor and third-party access governance.

This project uses a fictional non-production lab environment only. No real customer data, payment data, credentials, or production workloads are included.

## 2. Business Context
ShopSmart Online LLC sells consumer products through an online store. The business depends on cloud services to support digital operations, customer-facing systems, file storage, access control, and security visibility.

The fictional business has approximately 35 employees across operations, customer support, marketing, finance, fulfilment coordination, and technology support.

The business does not have a large internal cyber security team. Cloud administration is handled by a small technical team with support from an external development contractor.

Because eCommerce businesses handle customer and order-related information, weak cloud security could affect:
- Customer trust.
- Online sales availability.
- Business reputation.
- Operational continuity.
- Sensitive configuration and secrets.
- Cloud cost control.
- Contractor and third-party access risk.

## 3. Cloud Environment Reviewed

The review covers a small GCP lab environment designed to simulate a realistic SME cloud setup.

| Area |	GCP Component |
| --- | --- |
| Cloud project |	Dedicated GCP lab project |
| Identity and access |	IAM users, roles, and permissions |
| Workload identities |	Service accounts |
| Application hosting	| Optional Cloud Run demo web app |
| File storage |	Cloud Storage buckets |
| Secrets management |	Secret Manager |
| Logging |	Cloud Logging and Cloud Audit Logs |
| Security visibility |	Security Command Center Standard |
| Network exposure |	VPC firewall rules |
| Cost governance |	Billing budgets and alerts |

The environment is intentionally simple. The goal is to review cloud security controls, not to build a full production eCommerce platform.

## 4. Key Security Findings

The review identified several important cloud security risk areas.

| Finding Area |	Summary |	Business Risk |
| --- | --- | --- |
| IAM permissions |	Broad roles such as Owner or Editor may create excessive access. |	Account compromise or accidental changes could affect the whole project. |
| Privileged access |	Administrative access requires regular review and strong account protection. |	Unauthorised users may gain control over cloud resources. |
| Service accounts |	Service accounts may become overprivileged or poorly documented. |	Workload compromise could lead to wider cloud access. |
| Service account keys |	Downloaded keys can be leaked, reused, or accidentally committed to GitHub. |	Credential exposure may allow unauthorised cloud access. |
| Cloud Storage permissions |	Storage buckets may be misconfigured or accidentally exposed. |	Customer, order, or business data could become publicly accessible. |
| Secret Manager access |	Secrets require strict access control and careful screenshot handling. |	API keys, tokens, or credentials may be exposed or misused. |
| Logging visibility |	IAM, storage, service account, and secret activity should be visible in logs. |	Weak visibility may delay detection and investigation. |
| Log access |	Logs may contain sensitive operational information. |	Excessive log access may expose security evidence or system details. |
| Contractor access |	External access should be time-limited and reviewed. |	Former contractors may retain access after work ends. |
| Billing governance |	Budget alerts are needed to detect unexpected spending. |	Misconfigured or unused resources may create unexpected costs. |

## 5. Highest Priority Risks

The highest-priority risks identified are:

| Risk |	Priority |	Reason |
| --- | --- | --- |
| Overprivileged IAM access |	High |	Excessive roles can allow broad modification of cloud resources. |
| Service account key exposure |	High |	Keys can be copied, leaked, or reused outside GCP. |
| Public Cloud Storage exposure |	High |	Sensitive files may become accessible to unauthorised users. |
| Secret Manager overexposure |	High |	API keys and credentials could be accessed by unauthorised users. |
| Weak logging review |	High |	Important security events may not be detected quickly. |
| Unreviewed contractor access |	Medium |	External access may remain active longer than required. |
| Limited alerting |	Medium |	Important cloud changes may not trigger timely review. |
| Poor resource ownership |	Low to Medium |	Unclear ownership can delay remediation and increase cost. |

## 6. Current Security Maturity Assessment

The current cloud security maturity is assessed as `developing`.

| Security Area |	Current Position |	Target Position |
| --- | --- | --- |
| IAM governance |	Access can be reviewed manually but may rely on broad roles. |	Least-privilege access with regular access reviews. |
| Privileged access |	Owner and Editor roles require review. |	Minimal privileged access with documented justification. |
| Service accounts |	Service accounts exist or are planned for lab workloads. |	Workload-specific service accounts with narrow permissions. |
| Service account keys |	Keys should be avoided unless clearly required. |	No user-managed keys unless approved and documented. |
| Storage security |	Buckets require permission and public access review. |	Sensitive buckets private with public access blocked. |
| Secrets management |	Dummy secrets can be stored in Secret Manager. |	Secret access restricted and never published in screenshots. |
| Logging visibility |	Cloud Logging and Audit Logs are available for review. |	High-risk IAM, storage, secret, and service account changes reviewed. |
| Security monitoring |	Security Command Center Standard can be reviewed. |	Relevant findings tracked in the risk register. |
| Cost governance |	Billing budget alerts should be configured. |	Budget alerts active and reviewed by the owner. |
| Cloud governance |	Documentation and review process are being established. |	Repeatable review process with risk tracking and executive reporting. |

## 7. Key Recommendations

The most important recommendations are listed below.

| Recommendation |	Priority |	Owner |
| --- | --- | --- |
| Limit Project Owner access to trusted administrators only. |	High |	Cloud Administrator |
| Remove or reduce Editor roles. |	High |	Cloud Administrator |
| Review all service account permissions. |	High |	Cloud Administrator |
| Avoid service account keys where possible. |	High |	Cloud Administrator |
| Restrict Secret Manager access to approved users and workloads. |	High |	Cloud Administrator |
| Review Cloud Storage bucket permissions. |	High |	Cloud Administrator |
| Confirm public access prevention for sensitive buckets. |	High |	Cloud Administrator |
| Review IAM and service account activity in Cloud Logging. |	High |	Security Reviewer |
| Restrict log access to authorised users only. |	Medium |	Cloud Administrator |
| Configure billing budget alerts. |	Medium |	Finance Manager |
| Review Security Command Center findings. |	Medium |	Security Reviewer |
| Implement formal access reviews. |	Medium |	Operations Manager |
| Time-limit contractor access. |	Medium |	Operations Manager |
| Label resources for ownership and governance. |	Low	| Cloud Administrator |
| Maintain a cloud risk register. |	Medium |	Security Reviewer |

## 8. Recommended 90-Day Cloud Security Roadmap

### Days 1–30

| Action |	Owner |	Priority |
| --- | --- | --- |
| Review Project Owner access. |	Cloud Administrator |	High |
| Remove unnecessary Editor roles. |	Cloud Administrator |	High |
| Review service account permissions. |	Cloud Administrator |	High |
| Delete unnecessary service account keys. |	Cloud Administrator |	High |
| Restrict Secret Manager access. |	Cloud Administrator |	High |
| Review Cloud Storage public access settings. |	Cloud Administrator |	High |
| Configure billing budget alerts. |	Finance Manager |	Medium |
| Capture IAM, storage, logging, and billing screenshots. |	Security Reviewer |	Medium |

### Days 31–60

| Action |	Owner |	Priority |
| --- | --- | --- |
| Review Cloud Logging for IAM and service account changes. |	Security Reviewer |	High |
| Review Security Command Center findings. |	Security Reviewer |	Medium |
| Create access review record. |	Operations Manager |	Medium |
| Review external contractor access. |	Operations Manager |	Medium |
| Restrict log access to authorised users. |	Cloud Administrator |	Medium |
| Apply labels to key resources. |	Cloud Administrator |	Low |
| Update cloud risk register. |	Security Reviewer |	Medium |

### Days 61–90

| Action |	Owner |	Priority |
| --- | --- | --- |
| Complete formal IAM access review. |	Operations Manager |	Medium |
| Complete service account review. |	Cloud Administrator |	Medium |
| Confirm storage bucket classification and ownership. |	Security Reviewer |	Medium |
| Document cloud security baseline. |	Security Reviewer |	Medium |
| Review whether additional alerts are needed. |	Security Reviewer |	Medium |
| Present cloud risk summary to business leadership. |	Cloud Security Analyst |	Medium |
| Finalise GitHub and Medium documentation. |	Cloud Security Analyst |	Low |

## 9. Suggested Security Metrics

ShopSmart should track a small number of practical cloud security metrics.

| Metric |	Target |
| --- | --- |
| Project Owner accounts |	Limited and reviewed every three months |
| Editor role assignments |	Zero or documented exception only |
| Service accounts with Owner or Editor |	Zero |
| User-managed service account keys |	Zero unless approved |
| Sensitive buckets with public access |	Zero |
| Critical secrets with broad access |	Zero |
| IAM access reviews completed |	Every three to six months |
| Contractor access reviewed |	Monthly or after engagement completion |
| Security Command Center findings reviewed |	Monthly or after major changes |
| High-risk findings open |	Trending downward |
| Billing alert configured |	Yes |
| Cloud risk register updated |	Monthly or quarterly |

## 10. Business Benefits

The recommended improvements provide the following business benefits.

| Benefit |	Explanation |
| --- | --- |
| Reduced account compromise impact |	Least-privilege IAM limits what a compromised account can do. |
| Better protection of customer trust |	Storage and secrets controls reduce data exposure risk. |
| Stronger contractor governance |	Temporary and reviewed access reduces third-party access risk. |
| Improved investigation capability |	Logging helps identify who changed what and when. |
| Better executive visibility |	Risk register and summary reporting make cloud risks easier to manage. |
| Lower cost exposure |	Billing alerts help detect unexpected spending. |
| Stronger operational resilience |	Clear ownership and review cycles reduce misconfiguration risk. |
| Practical security maturity |	Improvements are realistic for an SME without expensive tooling. |
