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

## 9. Admin Activity Audit Logs Review
Admin Activity logs are important because they show administrative changes in the GCP environment.

Review questions:
- Can project-level administrative changes be found?
- Can IAM role changes be reviewed?
- Can service account creation or deletion be reviewed?
- Can Cloud Storage bucket configuration changes be reviewed?
- Can Secret Manager configuration changes be reviewed?
- Can Cloud Run deployment or configuration changes be reviewed?
- Are logs understandable for investigation?

Examples of activities to generate useful Admin Activity logs:
- `Create a Cloud Storage bucket`
- `Update bucket permissions`
- `Create a service account`
- `Assign a role to a service account`
- `Create a Secret Manager secret`
- `Deploy optional Cloud Run service`
- `Modify IAM role assignment`

`Risk`: Without administrative activity visibility, the business may not know who changed permissions, created resources, modified access, or changed security settings.

`Recommendation`: Admin Activity logs should be reviewed during security investigations and periodically checked for high-risk changes such as IAM updates, service account key creation, and storage permission changes.

## 10. IAM Logging Review
IAM logs help identify changes to users, roles, permissions, and project access. Review questions:
- Can IAM role changes be found in Log Explorer?
- Can new principals added to the project be identified?
- Can role removals be reviewed?
- Can privileged access changes be investigated?
- Can changes to Owner, Editor, IAM Admin, or Service Account roles be detected?

`Risk`: Unauthorised or accidental IAM changes can increase the risk of privilege misuse, account compromise, unauthorised access, and data exposure.

`Recommendation`: IAM changes should be treated as high-value security events. Privileged role changes should be reviewed and, where possible, monitored through alerts.

Suggested high-risk IAM events:

| Event | Reason |
| --- | --- |
| New Project Owner added | Full administrative access granted. |
| Editor role assigned | Broad modification access granted. |
| IAM Admin assigned | User can modify access. |
| Service Account User assigned | User may act as a service account. |
| Secret Manager access granted | User may access sensitive secrets. |
| External user added | Third-party access risk. |

## 11. Service Account Logging Review
Service account activity should be visible because service accounts can be high-risk cloud identities. Review questions:
- Can service account creation be found in logs?
- Can service account deletion be found in logs?
- Can role changes for service accounts be reviewed?
- Can service account key creation be identified?
- Can service account key deletion be identified?
- Can service account usage be linked to a workload?

`Risk`: If service account activity is not reviewed, the business may miss key creation, excessive role assignment, or workload identities being misused.

`Recommendation`: Service account key creation should be treated as a high-risk event. Service accounts should be reviewed regularly, and unnecessary keys should be avoided or deleted.

## 12. Cloud Storage Logging Review
Cloud Storage logging supports investigation of bucket configuration and access-related changes. Review questions:
- Can bucket creation be reviewed?
- Can bucket deletion be reviewed?
- Can bucket IAM permission changes be found?
- Can public access changes be identified?
- Can object upload or deletion activity be reviewed where logging is available?
- Are sensitive buckets separated from public or product image buckets?

`Risk`: Cloud Storage misconfiguration can expose sensitive customer, order, or business data. Poor logging may delay detection and investigation.

`Recommendation`: Bucket permission changes should be reviewed, especially for buckets representing confidential or restricted business information. Public access changes should be treated as high-priority events.

Suggested high-risk storage events:
| Event | Reason |
| --- | --- |
| Public access granted | Possible data exposure. |
| Bucket IAM changed | Access boundary modified. |
| Public access prevention disabled | Increased exposure risk. |
| Sensitive bucket created without controls | Governance gap. |
| Unusual object deletion | Possible data loss or misuse. |

## 13. Secret Manager Logging Review
Secret Manager activity should be reviewed because secrets may contain API keys, credentials, tokens, or sensitive application configuration. Review questions:
- Can secret creation be reviewed?
- Can secret version changes be reviewed?
- Can secret access events be reviewed where logging is available?
- Who can access secrets?
- Are secret values excluded from screenshots?
- Are secrets stored in Secret Manager instead of code or files?

`Risk`: If secrets are accessed or changed without visibility, the business may not detect credential misuse, exposed tokens, or unauthorised access.

`Recommendation`: Secret Manager access should be limited and monitored. Secret values should never appear in screenshots, GitHub repositories, documentation, or logs.

## 14. Cloud Run Logging Review
Cloud Run is optional in this project. If used, logs should be reviewed for basic operational and security visibility. Review questions:
- Are request logs visible?
- Are deployment events visible?
- Are configuration changes visible?
- Is the service publicly accessible?
- Is unauthenticated access enabled intentionally?
- Which service account does the Cloud Run service use?
- Are errors visible in logs?
- Are logs useful for basic troubleshooting?

`Risk`: Without application and service logs, the business may not detect application errors, unexpected access patterns, configuration changes, or service availability issues.

`Recommendation`: If Cloud Run is used, logs should be captured as part of the evidence set. Public access should be intentional and documented.

## 15. VPC Firewall Logging Review
Firewall logging is optional depending on whether network resources are used. Review questions:
- Are any firewall rules allowing access from `0.0.0.0/0`?
- Are SSH, RDP, HTTP, or HTTPS rules exposed?
- Is firewall logging enabled for high-risk rules?
- Are unused firewall rules present?
- Is the project using Compute Engine resources?
- Is network exposure relevant to this lab?

`Risk`: Broad firewall rules can expose resources to the internet. Without firewall logging, suspicious access attempts may not be visible.

`Recommendation`: Avoid creating unnecessary public firewall rules. If public rules are required, document the business reason and consider enabling firewall logging for high-risk rules.

## 16. Security Command Center Review
Security Command Center Standard provides security posture visibility for the GCP environment. Review questions:
- Is Security Command Center available for the project?
- Are any findings shown?
- Are findings related to IAM, storage, service accounts, network, or public exposure?
- Are findings prioritised?
- Are findings linked to recommendations?
- Are findings included in the risk register where relevant?

`Risk`: If security findings are not reviewed, the business may miss cloud misconfigurations or high-priority risks.

`Recommendation`: Security Command Center findings should be reviewed during the security assessment and documented in the security checklist and risk register.

## 17. Log Access Review
Logs may contain sensitive information, including user activity, IP addresses, resource names, access changes, service activity, and incident evidence. Review questions:
- Who can view logs?
- Are log viewers limited to authorised users?
- Do developers need full log access?
- Does the security reviewer have appropriate log visibility?
- Are logs exposed to users who do not need them?
- Are logs treated as sensitive information?

`Risk`: Excessive log access may expose sensitive operational information and security evidence.

`Recommendation`: Grant log access only to users with a clear operational, security, or audit need. Use roles such as Logging Viewer or Logs Viewer where appropriate.

## 18. Monitoring and Alerting Review
Monitoring and alerting help identify issues before they become major incidents. For this SME lab scenario, alerting should remain simple and practical. Recommended alerting areas:

| Alert Area | Why It Matters |
| --- | --- |
| Billing budget alert | Detects unexpected cost increases. |
| Cloud Run service errors | Helps identify application issues if Cloud Run is used. |
| High-risk IAM changes | Helps detect privileged access changes. |
| Service account key creation | Helps detect risky credential creation. |
| Cloud Storage public access change | Helps detect accidental exposure. |
| Secret access or change | Helps monitor sensitive configuration. |

`Risk`: Without useful alerts, important security or operational events may go unnoticed until customers or staff report a problem.

`Recommendation`: At minimum, billing budget alerts should be configured. Security alerts for high-risk IAM and storage events should be considered as the environment matures.
