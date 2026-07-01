# Logging and Monitoring Review
## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this Logging and Monitoring Review is to assess whether the ShopSmart Online LLC Google Cloud Platform lab environment has sufficient visibility to detect, investigate, and respond to security-relevant activity.

This review focuses on Cloud Logging, Cloud Audit Logs, monitoring visibility, log access, alerting considerations, and evidence that can support incident response.

The goal is to determine whether important cloud activities can be reviewed by the business and whether logging is suitable for a small-to-medium eCommerce environment.

## 2. Review Scope
This review covers:

| Area | In Scope |
| --- | --- |
| Cloud Logging | Availability of logs for cloud activity and resources. |
| Cloud Audit Logs | Visibility of administrative and access-related events. |
| IAM activity logs | Ability to review IAM role and permission changes. |
| Service account activity | Ability to review service account creation, role assignment, and key activity. |
| Cloud Storage activity | Ability to review bucket creation, permission changes, and access-related events. |
| Secret Manager logs | Ability to review secret creation, update, and access events. |
| Cloud Run logs | Optional review if Cloud Run demo app is used. |
| VPC firewall logs | Review whether firewall logging is enabled or required. |
| Monitoring | Basic visibility of cloud resources and service health. |
| Alerting | Whether important security events should trigger alerts. |
| Log access | Who can view logs and whether log access is appropriate. |
| Evidence | Screenshots from Log Explorer, Audit Logs, Monitoring, and related services. |

## 3. Out of Scope
The following areas are outside the scope of this review:

| Out of Scope | Reason |
| --- | --- |
| Enterprise SIEM deployment | Not required for this SME portfolio lab. |
| Security Operations Centre | The fictional business does not have a dedicated SOC. |
| Paid threat detection services | The project uses practical low-cost or free-tier visibility. |
| Full log pipeline engineering | Not required for this portfolio scenario. |
| Production incident investigation | No real production workload or customer data is used. |
| Advanced detection engineering | The focus is review and governance, not custom detection rules. |
| Long-term log archive design | Not required unless the business later matures. |
| Legal evidence handling | This project is not a legal or forensic investigation. |

## 4. Logging and Monitoring Objectives
The review supports the following objectives:

| Objective | Description |
| --- | --- |
| Detect suspicious activity | Ensure important cloud activities can be identified. |
| Support investigation | Confirm that logs can help investigate incidents. |
| Improve accountability | Ensure administrative actions are traceable. |
| Support access governance | Review whether IAM and service account changes are visible. |
| Improve incident response | Ensure evidence is available during security events. |
| Reduce blind spots | Identify areas where important logging is missing or incomplete. |
| Support business reporting | Translate logging gaps into practical business recommendations. |

## 5. Logging Principles Used
The review uses the following principles:

| Principle | Description |
| --- | --- |
| Security visibility | Important cloud activity should be visible. |
| Auditability | Administrative and privileged actions should be traceable. |
| Least privilege for logs | Log access should be limited to authorised users. |
| Retention awareness | The business should understand how long logs are available. |
| Useful alerting | Alerts should focus on high-value events, not noise. |
| Investigation readiness | Logs should support incident response and root cause analysis. |
| Data sensitivity | Logs may contain sensitive operational details and should be protected. |
| Practicality | Logging should be suitable for an SME environment. |

## 6. Logging Sources Reviewed

| Logging Source | Review Purpose |
| --- | --- |
| Admin Activity Audit Logs | Review administrative changes such as IAM updates and resource changes. |
| Data Access Audit Logs | Review access to data where enabled and appropriate. |
| System Event Logs | Review Google-managed service events. |
| Policy Denied Logs | Review denied access attempts where available. |
| Cloud Storage Logs | Review bucket creation, configuration, and permission changes. |
| IAM Logs | Review role assignments and access changes. |
| Service Account Logs | Review service account creation, updates, and key activity. |
| Secret Manager Logs | Review secret creation, update, and access-related events. |
| Cloud Run Logs | Review application and service logs if Cloud Run is used. |
| VPC Firewall Logs | Review firewall traffic visibility if enabled. |
| Security Command Center Findings | Review security findings and posture observations. |

## 7. Key Review Questions
This review answers the following questions:
1. Can administrative activity be reviewed in Cloud Logging?
2. Can IAM changes be investigated?
3. Can service account creation and key activity be identified?
4. Can storage bucket permission changes be reviewed?
5. Can Secret Manager activity be reviewed?
6. Are Cloud Run logs available if a demo app is used?
7. Are logs accessible only to authorised users?
8. Are important security findings visible in Security Command Center?
9. Are alerts configured or recommended for important risks?
10. Are there logging gaps that may affect incident response?
11. Are screenshots available as evidence for the portfolio?
12. Are logs protected from unnecessary exposure?

## 8. Logging Review Summary

| Review Area | Expected State | Review Status |
| --- | --- | --- |
| Admin Activity logs | Available for administrative activity review. | Review Required |
| IAM activity logs | IAM changes visible in Log Explorer. | Review Required |
| Service account logs | Service account creation and key activity visible. | Review Required |
| Cloud Storage activity | Bucket and permission changes visible. | Review Required |
| Secret Manager activity | Secret creation and access events visible where available. | Review Required |
| Cloud Run logs | Available if optional Cloud Run service is deployed. | Optional |
| Security Command Center findings | Findings reviewed and documented. | Review Required |
| Log access permissions | Limited to authorised users. | Review Required |
| Alerting | Basic alerts considered for high-risk activities. | Recommended |
| Evidence screenshots | Captured and sanitised before publishing. | Required |
