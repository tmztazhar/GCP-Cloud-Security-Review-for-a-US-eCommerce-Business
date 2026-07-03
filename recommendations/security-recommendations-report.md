# Security Recommendations Report

## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this Security Recommendations Report is to provide practical remediation guidance based on the GCP cloud security review performed for ShopSmart Online LLC.

This report translates technical review findings into business-focused recommendations that can reduce cloud security risk, improve governance, strengthen access control, improve logging visibility, and support safer cloud operations for a small-to-medium eCommerce business.

The recommendations are designed to be realistic, cost-conscious, and suitable for a small GCP environment without assuming enterprise-level tooling or a dedicated security operations centre.

## 2. Executive Summary
The GCP security review identified several important areas where ShopSmart Online LLC can improve its cloud security posture. The highest-priority recommendations are:
1. Reduce excessive IAM permissions.
2. Limit Project Owner and Editor access.
3. Review and harden service accounts.
4. Avoid service account keys where possible.
5. Restrict access to Secret Manager.
6. Review Cloud Storage bucket permissions.
7. Confirm public access prevention for sensitive buckets.
8. Improve logging review for IAM, storage, service account, and secret activity.
9. Configure billing alerts and basic security monitoring.
10. Formalise access reviews and contractor access removal.

The review found that most improvements are practical and low-cost. The business does not need complex enterprise tooling to significantly reduce its cloud risk.

## 3. Recommendation Priority Model
Recommendations are prioritised using the following model:

| Priority | Recommendation | Action Expectation |
| --- | --- | --- |
| Critical | Immediate risk to sensitive data, privileged access, or business availability. | Address as soon as possible. |
| High | Significant risk that could lead to account compromise, data exposure, or major disruption. | Address within 30 days. |
| Medium | Important control weakness that increases risk over time. | Address within 60 to 90 days. |
| Low | Good practice improvement or documentation enhancement. | Address as part of normal improvement cycle. |

## 4. Summary of Key Recommendations

| Recommendation ID | Recommendation | Priority | Owner |
| --- | --- | --- | --- |
| REC-01 | Limit Project Owner access. | High | Cloud Administrator |
| REC-02 | Remove or reduce Editor roles. | High | Cloud Administrator |
| REC-03 | Review service account permissions. | High | Cloud Administrator |
| REC-04 | Avoid service account keys. | High | Cloud Administrator |
| REC-05 | Restrict Secret Manager access. | High | Cloud Administrator |
| REC-06 | Review Cloud Storage bucket permissions. | High | Cloud Administrator |
| REC-07 | Confirm public access prevention for sensitive buckets. | High | Cloud Administrator |
| REC-08 | Review IAM and service account activity in Cloud Logging. | High | Security Reviewer |
| REC-09 | Restrict log access to authorised users. | Medium | Cloud Administrator |
| REC-10 | Configure billing budget alerts. | Medium | Finance Manager |
| REC-11 | Review Security Command Center findings. | Medium | Security Reviewer |
| REC-12 | Implement access review process. | Medium | Operations Manager |
| REC-13 | Time-limit contractor access. | Medium | Operations Manager |
| REC-14 | Label resources for ownership and governance. | Low | Cloud Administrator |
| REC-15 | Maintain a cloud risk register. | Medium | Security Reviewer |

### 4.1 Limit Project Owner Access

**Recommendation ID**: REC-01

**Priority**: High

**Related Risks**:
- Overprivileged IAM access.
- Privileged account compromise.
- Unauthorised cloud resource changes.
- Accidental deletion or modification of resources.

**Issue**

Project Owner access provides broad administrative control over the GCP project. If too many users have Owner access, the risk of misuse, accidental changes, or account compromise increases significantly.

**Business Impact**

If a Project Owner account is compromised or misused, an attacker or unauthorised user may be able to:
- Modify IAM permissions.
- Access sensitive configuration.
- Create or delete resources.
- Disable security controls.
- Increase cloud costs.
- Affect application availability.
- Remove security evidence.

**Recommended Action**

ShopSmart should limit Project Owner access to a small number of trusted administrators. Recommended actions:
1. Review all users and service accounts with Owner access.
2. Confirm whether Owner access is still required.
3. Remove Owner access where not justified.
4. Replace Owner access with more specific predefined roles.
5. Document business justification where Owner access remains.
6. Review Owner access every three months.

**Suggested Target State**

| Area |	Target State |
| --- | --- |
| Project Owner users |	Limited to one or two trusted administrators. |
| Project Owner service accounts |	None, unless clearly justified. |
| Review frequency |	Every three months. |
| Evidence |	IAM screenshot and access review record. |

### 4.2 Remove or Reduce Editor Roles
**Recommendation ID**: REC-02

**Priority**: High

**Related Risks**:
- Excessive permissions.
- Unauthorised cloud changes.
- Service account misuse.
- Poor separation of duties.

**Issue**

The Editor role grants broad permissions across many GCP services. It is often more access than users or workloads need.

**Business Impact**

Excessive Editor access may allow users or service accounts to modify resources unrelated to their role. This increases the risk of accidental misconfiguration, data exposure, and unauthorised activity.

**Recommended Action**

ShopSmart should avoid using the Editor role for normal users, contractors, and service accounts. Recommended actions:
1. Identify all users and service accounts with Editor access.
2. Confirm whether Editor access is required.
3. Replace Editor with narrower roles.
4. Use role-specific access such as Cloud Run Developer, Storage Object Viewer, Logging Viewer, Security Reviewer, or Secret Manager
5. Secret Accessor only where needed.
6. Document any temporary Editor access.
7. Remove temporary broad access after work is completed.

**Suggested Target State**

| Area |	Target State |
| --- | --- |
| Editor assigned to users |	Avoided where possible. |
| Editor assigned to service accounts |	Avoided. |
| Temporary broad access |	Approved, documented, and time-limited. |
| Review frequency |	Every three months. |

### 4.3 Review Service Account Permissions

**Recommendation ID**: REC-03

**Priority**: High

**Related Risks**:
- Overprivileged service accounts.
- Workload compromise.
- Unauthorised access to storage, secrets, or logs.
- Cloud resource misuse.

**Issue**

Service accounts are cloud identities used by workloads and automation. If service accounts have excessive permissions, compromise of one workload may lead to wider cloud access.

**Business Impact**

An overprivileged service account could allow unauthorised access to sensitive storage buckets, secrets, logs, or application resources.

**Recommended Action**

ShopSmart should review all service accounts and confirm that each one has a clear purpose and least-privilege permissions. Recommended actions:
1. List all service accounts.
2. Identify the workload or purpose for each service account.
3. Review assigned roles.
4. Remove unused service accounts.
5. Remove Owner or Editor roles from service accounts.
6. Assign narrow roles based on actual workload requirements.
7. Add ownership notes in documentation.
8. Review service accounts every six months.

**Suggested Target State**

| Area |	Target State |
| --- | --- |
| Service account purpose |	Clearly documented. |
| Service account owner |	Assigned. |
| Broad roles |	Removed where possible. |
| Unused service accounts |	Disabled or deleted. |
| Review frequency |	Every six months. |

### 4.4 Avoid Service Account Keys

**Recommendation ID**: REC-04

**Priority**: High

**Related Risks**:
- Credential leakage.
- Unauthorised cloud access.
- Key reuse outside GCP.
- Secrets committed to GitHub.

**Issue**

User-managed service account keys can be downloaded and used outside the GCP environment. If a key is leaked, an attacker may be able to authenticate as the service account.

**Business Impact**

A leaked service account key could allow unauthorised access to cloud resources, depending on the permissions assigned to that service account.

**Recommended Action**

ShopSmart should avoid creating service account keys unless there is a clear business and technical requirement. Recommended actions:
1. Review all service accounts for user-managed keys.
2. Delete unnecessary keys.
3. Avoid creating new keys for the lab.
4. Use managed service identities where possible.
5. If a key is required, document the reason, owner, storage location, and expiry.
6. Rotate keys where required.
7. Never upload keys to GitHub.
8. Monitor service account key creation events.

**Suggested Target State**

| Area |	Target State |
| --- | --- |
| User-managed service account keys |	None unless approved. |
| Key storage |	Secure and documented. |
| Key publication |	Never published. |
| Key review |	Every three months. |
| Key creation events |	Reviewed in logs. |

### 4.5 Restrict Secret Manager Access

**Recommendation ID**: REC-05

**Priority**: High

**Related Risks**:
- Secret exposure.
- API key misuse.
- Unauthorised application access.
- Credential compromise.

**Issue**

Secret Manager may contain sensitive values such as API keys, tokens, database credentials, or application secrets. Access must be tightly controlled.

**Business Impact**

If a secret is accessed by an unauthorised user or overprivileged service account, the business may face account compromise, API misuse, data exposure, or service disruption.

**Recommended Action**

ShopSmart should restrict Secret Manager access to authorised users and workloads only. Recommended actions:
1. Identify all users and service accounts with Secret Manager access.
2. Confirm whether access is required.
3. Remove unnecessary access.
4. Avoid granting broad secret access at project level where possible.
5. Do not store secrets in code, spreadsheets, screenshots, or README files.
6. Review secret access logs where available.
7. Rotate secrets if exposure is suspected.
8. Ensure secret values are never shown in public screenshots.

**Suggested Target State**

| Area |	Target State |
| --- | --- |
| Secret access |	Limited to approved users and workloads. |
| Secret storage |	Secret Manager, not code or files. |
| Secret screenshots |	Secret values hidden. |
| Review frequency |	Every three months. |
| Rotation |	Considered for sensitive secrets. |

### 4.6 Review Cloud Storage Bucket Permissions
**Recommendation ID**: REC-06

**Priority**: High

**Related Risks**:
- Public data exposure.
- Sensitive order data leakage.
- Misconfigured bucket permissions.
- Unauthorised object access.

**Issue**

Cloud Storage buckets may store product files, order files, logs, exports, or application data. Misconfigured bucket permissions can expose sensitive data.

**Business Impact**

For an eCommerce business, storage exposure could affect customer trust, privacy expectations, operational records, and business reputation.

**Recommended Action**

ShopSmart should review all Cloud Storage bucket permissions and confirm that access is appropriate. Recommended actions:
1. List all Cloud Storage buckets.
2. Confirm the purpose of each bucket.
3. Classify each bucket as Public, Internal, Confidential, or Restricted.
4. Review bucket IAM permissions.
5. Confirm public access is intentional only for public product assets.
6. Ensure order-related or customer-related buckets are not public.
7. Enable uniform bucket-level access where appropriate.
8. Review object-level permissions.
9. Remove unnecessary users and service accounts.
10. Record screenshots as evidence.

**Suggested Target State**

| Bucket Type |	Target State |
| --- | --- |
| Product image bucket |	Public access only if required and documented. |
| Order document bucket |	Private with public access blocked. |
| Sensitive file bucket |	Restricted access only. |
| Unknown bucket |	Reviewed and classified. |
| Review frequency |	Every six months. |

### 4.7 Confirm Public Access Prevention

**Recommendation ID**: REC-07

**Priority**: High

**Related Risks**:
- Accidental public exposure.
- Customer or order data leakage.
- Misconfigured access settings.

**Issue**

Sensitive Cloud Storage buckets should not be publicly accessible. Public access prevention helps reduce the risk of accidental public exposure.

**Business Impact**

Accidental public exposure of customer or order-related files may lead to reputational damage, customer complaints, privacy concerns, and operational disruption.

**Recommended Action**

ShopSmart should confirm public access prevention is enabled for buckets containing sensitive or confidential information. Recommended actions:
1. Identify buckets containing sensitive or confidential data.
2. Confirm public access prevention is enabled.
3. Confirm no allUsers or allAuthenticatedUsers access exists.
4. Review whether any public bucket access is intentional.
5. Document business justification for public buckets.
6. Monitor changes to bucket public access settings.

**Suggested Target State**

| Area | Target State |
| --- | --- |
| Sensitive buckets |	Public access blocked. |
| Public buckets |	Business justification documented. |
| Anonymous access |	Not allowed for sensitive buckets. |
| Review frequency |	Every six months or after major changes. |

### 4.8 Review IAM and Service Account Activity in Cloud Logging
**Recommendation ID**: REC-08

**Priority**: High

**Related Risks**:
- Unnoticed privilege changes.
- Service account misuse.
- Weak incident investigation capability.
- Lack of security visibility.

**Issue**

IAM and service account changes are high-value security events. If these events are not reviewed, unauthorised access changes may go unnoticed.

**Business Impact**

A malicious or accidental IAM change may grant excessive access, expose cloud resources, or weaken the security posture of the environment.

**Recommended Action**

ShopSmart should use Cloud Logging and Log Explorer to review high-risk IAM and service account activity. Recommended actions:
1. Confirm IAM changes are visible in Log Explorer.
2. Review role assignments and removals.
3. Review Project Owner and Editor changes.
4. Review service account creation.
5. Review service account key creation.
6. Review external user additions.
7. Consider alerts for high-risk access changes.
8. Include IAM log review in periodic security checks.

**Suggested Target State**

| Event Type |	Target State |
| --- | --- |
| Project Owner added |	Reviewed. |
| Editor assigned |	Reviewed. |
| Service account key created |	Reviewed and investigated. |
| External user added |	Reviewed and approved. |
| Secret access granted |	Reviewed. |

### 4.9 Restrict Log Access
**Recommendation ID**: REC-09

**Priority**: Medium

**Related Risks**:
- Sensitive log exposure.
- Unauthorised access to operational information.
- Excessive visibility into security activity.

**Issue**

Logs may contain sensitive operational and security information, including user activity, IP addresses, resource names, access changes, and investigation evidence.

**Business Impact**

If too many users can view logs, sensitive system details may be exposed. This can also reduce the integrity of incident investigations.

**Recommended Action**

ShopSmart should restrict log access to users with a valid security, operational, or audit need. Recommended actions:
1. Identify users with log access.
2. Confirm whether log access is required.
3. Remove unnecessary log access.
4. Use Logging Viewer or Logs Viewer roles appropriately.
5. Avoid granting log access through broad roles such as Owner or Editor.
6. Review log access every six months.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Log viewers |	Limited to authorised users. |
| Developers |	Access only where needed for troubleshooting. |
| Security reviewer |	Read-only logging access. |
| Review frequency |	Every six months. |

### 4.10 Configure Billing Budget Alerts
**Recommendation ID**: REC-10

**Priority**: Medium

**Related Risks**:
- Unexpected cloud costs.
- Resource misuse.
- Lack of cost governance.
- Accidental deployment of paid resources.

**Issue**

Cloud environments can generate unexpected charges if resources are deployed incorrectly, left running, or misused.

**Business Impact**

Unexpected billing can affect a small business financially and may indicate resource misuse or poor cloud governance.

**Recommended Action**

ShopSmart should configure billing budget alerts for the GCP project. Recommended actions:
1. Create a project-level budget.
2. Use a low threshold appropriate for the lab or SME environment.
3. Configure alerts at 50%, 75%, and 90% or 100%.
4. Send alerts to the appropriate owner.
5. Review billing dashboard periodically.
6. Shut down unused resources.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Budget configured |	Yes. |
| Alert thresholds |	50%, 75%, 90% or 100%. |
| Alert recipient |	Project owner or finance owner. |
| Review frequency |	Monthly. |

### 4.11 Review Security Command Center Findings

**Recommendation ID**: REC-11

**Priority**: Medium

**Related Risks**:
- Untracked misconfigurations.
- Poor security visibility.
- Missed cloud security findings.

**Issue**

Security Command Center can provide visibility into security posture and findings. If findings are not reviewed, issues may remain unresolved.

**Business Impact**

Unreviewed security findings may allow cloud risks to remain active and increase the chance of account compromise, data exposure, or misconfiguration.

**Recommended Action**

ShopSmart should review Security Command Center Standard findings and include relevant findings in the cloud risk register. Recommended actions:
1. Open Security Command Center.
2. Review active findings.
3. Confirm whether findings are relevant.
4. Prioritise findings based on business impact.
5. Add material findings to the risk register.
6. Track remediation actions.
7. Recheck findings after remediation.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Findings reviewed |	Yes. |
| Relevant findings tracked |	Added to risk register. |
| High-risk findings |	Assigned owner and target date. |
| Review frequency |	Monthly or after major changes. |

### 4.12 Implement Formal Access Reviews
**Recommendation ID**: REC-12

**Priority**: Medium

**Related Risks**:
- Former employee access.
- Excessive permissions.
- Unreviewed contractor access.
- Privilege creep.

**Issue**

Without regular access reviews, users and service accounts may retain permissions that are no longer required.

**Business Impact**

Unreviewed access increases the risk of unauthorised activity, data exposure, and cloud misconfiguration.

**Recommended Action**

ShopSmart should implement a simple access review process. Recommended actions:
1. Export or screenshot IAM roles.
2. Review users with project access.
3. Review service accounts and roles.
4. Confirm business need for each role.
5. Remove unnecessary access.
6. Document review results.
7. Repeat every three to six months.

**Suggested Target State**
| Access Type |	Review Frequency |
| --- | --- |
| Project Owner |	Every three months. |
| Editor and IAM Admin |	Every three months. |
| Service accounts |	Every six months. |
| Contractor access |	Monthly or after work completion. |
| Secret access |	Every three months. |
| General viewer access |	Every six to twelve months. |

### 4.13 Time-Limit Contractor Access
**Recommendation ID**: REC-13

**Priority**: Medium

**Related Risks**:
- Former contractor access.
- External account compromise.
- Unauthorised changes.
- Poor accountability.

**Issue**

External contractors may require temporary access to support application deployment or cloud configuration. If access is not time-limited, it may remain after the work is completed.

**Business Impact**

A former contractor account with active access may expose the business to unauthorised access, accidental changes, or compromised third-party account risk.

**Recommended Action**

ShopSmart should apply strict governance to contractor access. Recommended actions:
1. Approve contractor access before granting it.
2. Assign least-privilege roles only.
3. Set an access expiry date.
4. Review access monthly.
5. Remove access immediately when work is completed.
6. Avoid granting Owner, Editor, or IAM Admin roles to contractors.
7. Document contractor access in the access review record.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Contractor access |	Temporary and approved. |
| Privileged contractor access |	Avoided unless exceptional. |
| Access expiry |	Defined before access is granted. |
| Review frequency |	Monthly or after project completion. |

### 4.14 Label Resources for Ownership and Governance
**Recommendation ID**: REC-14

**Priority**: Low

**Related Risks**:
- Poor asset ownership.
- Unclear environment separation.
- Weak cost tracking.
- Difficulty reviewing resources.

**Issue**

Unlabelled cloud resources can make it difficult to identify purpose, owner, environment, and business relevance.

**Business Impact**

Poor labelling may lead to confusion, unnecessary cost, delayed remediation, and unclear accountability.

**Recommended Action**

ShopSmart should apply simple labels to cloud resources where supported. Recommended labels:

| Label Key |	Example Value |
| --- | --- |
| environment |	lab |
| project |	gcp-security-review |
| business |	ecommerce |
| owner |	cloud-security-analyst |

Recommended actions:
1. Identify resources that support labels.
2. Apply environment and owner labels.
3. Use labels consistently.
4. Include labels in future resource creation standards.
5. Review labels during cloud governance checks.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Critical resources |	Labelled. |
| Environment |	Clearly identified. |
| Owner |	Documented. |
| Cost tracking |	Supported through labels. |

### 4.15 Maintain Cloud Risk Register

**Recommendation ID**: REC-15

**Priority**: Medium

**Related Risks**:
- Untracked cloud risks.
- No clear treatment ownership.
- Poor executive visibility.
- Repeated misconfigurations.

**Issue**

Cloud security findings should not remain only as technical notes. They should be recorded, prioritised, assigned to owners, and tracked to closure.

**Business Impact**

Without a cloud risk register, business leadership may not understand which cloud risks matter most, who owns them, and what actions are being taken.

**Recommended Action**

ShopSmart should maintain a cloud risk register for material GCP security risks. Recommended actions:
1. Record all high and medium cloud security risks.
2. Assign a business or technical owner.
3. Score likelihood and impact.
4. Record existing controls.
5. Define treatment actions.
6. Set target dates.
7. Track status.
8. Review the register monthly or quarterly.

**Suggested Target State**
| Area |	Target State |
| --- | --- |
| Cloud risks |	Recorded in risk register. |
| Risk owners |	Assigned. |
| Treatment actions |	Documented. |
| Review frequency |	Monthly or quarterly. |
| Executive visibility |	Included in security summary. |
