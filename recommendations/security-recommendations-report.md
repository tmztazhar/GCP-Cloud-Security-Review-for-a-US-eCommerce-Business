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
