# IAM and Access Review
## Project: GCP Cloud Security Review for a US eCommerce Business

### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this IAM and Access Review is to assess how identity and access management is configured within the ShopSmart Online LLC Google Cloud Platform lab environment.

This review focuses on whether users, service accounts, roles, and permissions follow the principle of least privilege. It also assesses privileged access, external access, service account usage, account review practices, and access governance.

The goal is to identify access-related risks and provide practical recommendations suitable for a small-to-medium eCommerce business using GCP.

## 2. Review Scope
This IAM and access review covers:

| Area | In Scope |
| --- | --- |
| GCP IAM principals | Users, groups, and service accounts assigned access to the project. |
| Project-level IAM roles | Owner, Editor, Viewer, Security Reviewer, Logging Viewer, and other assigned roles. |
| Privileged access | Accounts with administrative or broad permissions. |
| Service accounts | Service account roles, usage, keys, and permission scope. |
| External access | Contractor or third-party access to the GCP project. |
| MFA observations | Account security expectations for privileged users. |
| Access review process | Whether access is reviewed and removed when no longer needed. |
| Least privilege | Whether permissions are appropriate for job responsibilities. |
| Evidence | Screenshots and observations from the GCP lab environment. |

## 3. Out of Scope
The following areas are outside the scope of this review:

| Out of Scope | Reason |
| --- | --- |
| Real production IAM review | This is a fictional portfolio lab. |
| Google Workspace enterprise identity configuration | The lab uses a simple GCP access model. |
| Password policy enforcement review | Managed outside the GCP project in the user’s Google account or organisation settings. |
| Full identity governance platform review | Not required for this SME lab scenario. |
| Automated IAM recommender implementation | Observations may be documented, but full automation is not required. |
| Penetration testing or privilege escalation testing | This is a configuration and governance review only. |

## 4. Review Method
The review follows this process:
1. Identify all IAM principals with project access.
2. Review assigned roles for each principal.
3. Identify privileged roles such as Owner, Editor, and IAM Admin.
4. Review whether broad roles are required.
5. Review service accounts and assigned roles.
6. Check whether service account keys exist.
7. Review whether external or contractor access exists.
8. Assess whether access follows least privilege.
9. Record findings and risk impact.
10. Recommend practical access control improvements.

## 5. IAM Principles Used
The review uses the following IAM principles:

| Principle | Description |
| --- | --- |
| Least privilege | Users and service accounts should only receive access required for their role. |
| Need to know | Access should be based on business need. |
| Unique identity | Each user should use their own account. |
| Privileged access control | Administrative permissions should be limited and reviewed. |
| Separation of duties | No single user should have unnecessary control over all cloud activities. |
| Time-limited access | Contractor or temporary access should be removed when no longer needed. |
| Service account control | Service accounts should be workload-specific and not overprivileged. |
| No unnecessary keys | Service account keys should be avoided unless clearly required. |
| Regular access review | Access should be reviewed periodically. |
| Auditability | Access changes should be visible through logs. |

## 6. IAM Roles Reviewed
The following role types are relevant to this review:

| Role Type | Risk Consideration |
| --- | --- |
| Owner | Full administrative control. Should be highly restricted. |
| Editor | Broad access to modify many resources. Often excessive for normal users. |
| Viewer | Read-only access. Lower risk but still exposes configuration information. |
| IAM Admin | Can modify access and should be highly restricted. |
| Security Reviewer | Suitable for security review activity. Lower risk than Owner or Editor. |
| Logging Viewer | Allows log review. Useful for investigation but logs may contain sensitive information. |
| Storage Admin | Can manage storage buckets and data access. Should be limited. |
| Cloud Run Admin / Developer | Should be limited to application deployment responsibilities. |
| Service Account User | Can act as a service account. Should be carefully controlled. |
| Secret Manager | Can access secrets. |
| Secret Accessor | Should be restricted. |
| Biling Viewer | Allows billing visibility without resource administration. |

## 7. IAM Access Model
The fictional access model for ShopSmart is shown below.

| Role / User Type |	Business Responsibility |	Expected Access |
| --- | --- | --- |
| Cloud Administrator |	Manages GCP project and technical configuration. |	Limited number of privileged roles. |
| Security Reviewer |	Reviews IAM, logging, storage, and security posture. |	Security Reviewer and Logging Viewer. |
| Internal Developer |	Supports optional Cloud Run demo app. |	Limited Cloud Run and deployment access. |
| External Developer Contractor |	Supports temporary application updates. |	Time-limited least-privilege access only. |
| Finance Manager |	Reviews billing and budget alerts. |	Billing Viewer only. |
| Operations Manager |	Owns business risk and receives security reports. |	No direct admin access required unless justified. |
| Service Accounts |	Used by workloads or automation. |	Workload-specific access only. |

For the actual lab, these roles may be represented in documentation without creating real external user accounts.

## 8. IAM Review Findings Summary

| Finding ID | Finding | Severity | Status |
| --- | --- | --- | --- |
| IAM-01 | Project Owner access should be limited to the minimum number of trusted administrators. | High | Review Required |
| IAM-02 | Broad Editor roles should be avoided where specific roles are available. | High | Review Required |
| IAM-03 | Service accounts should not have Owner or Editor roles. | High | Review Required |
| IAM-04 | External contractor access should be time-limited and reviewed. | Medium | Review Required |
| IAM-05 | Billing access should be separated from technical administration. | Medium | Review Required |
| IAM-06 | Security reviewers should use read-only security and logging roles where possible. | Medium | Review Required |
| IAM-07 | Service account keys should be avoided unless required. | High | Review Required |
| IAM-08 | IAM access should be reviewed at least every six months. | Medium | Recommended |
| IAM-09 | Privileged access changes should be monitored in Cloud Logging. | Medium | Recommended |
| IAM-10 | Sensitive roles such as Secret Manager access should be limited. | High | Review Required |

## 9. Detailed IAM Review

### 9.1 Project Owner Access
Project Owner access gives broad administrative control over the GCP project. Review questions:
- Who has Project Owner access?
- Is Project Owner access required for daily work?
- Can the user perform their role with a more limited role?
- Is there more than one trusted administrator?
- Are personal accounts used for administration?
- Is privileged access reviewed periodically?

`Risk`:
If Project Owner access is granted too broadly, a compromised account could modify resources, change IAM permissions, disable logging, delete resources, access sensitive configuration, or create unexpected cost.

`Recommendation`:
Project Owner access should be limited to a small number of trusted administrator accounts. Day-to-day work should use more specific roles wherever possible.

### 9.2 Editor Role Review
The Editor role provides broad permissions across many GCP services. Review questions:
- Are any users assigned the Editor role?
- Are any service accounts assigned the Editor role?
- Is Editor access required?
- Can the access be replaced with narrower predefined roles?
- Can role assignments be limited to specific resources?

`Risk`:
The Editor role may allow users or service accounts to modify resources beyond their job responsibilities. This increases the risk of accidental changes, unauthorised activity, and privilege misuse.

`Recommendation`:
Avoid assigning Editor roles for normal users or service accounts. Replace Editor access with specific roles such as Cloud Run Developer, Storage Object Admin, Logging Viewer, Security Reviewer, or Secret Manager Secret Accessor only where needed.

### 9.3 Viewer and Read-Only Access
Viewer access allows users to view project resources and configuration. Review questions:
- Who has Viewer access?
- Is Viewer access appropriate for the user’s role?
- Does the user also need Logging Viewer or Security Reviewer?
- Is access granted to personal accounts or business-controlled accounts?

`Risk`:
Viewer access is lower risk than Owner or Editor, but it may still expose infrastructure details, project configuration, resource names, and security settings.

`Recommendation`:
Use read-only access for users who only need visibility. Review whether Viewer access should be combined with more targeted roles depending on job function.

### 9.4 Security Reviewer Access
Security Reviewer access is useful for reviewing security configuration without granting broad administrative permissions. Review questions:
- Is the security reviewer using a read-only security role?
- Does the reviewer also need Logging Viewer?
- Does the reviewer have unnecessary Owner or Editor access?
- Can security review be performed without administrative access?

`Risk`:
If a security reviewer has excessive access, the review account itself becomes a privileged risk.

`Recommendation`:
Security review activities should use read-only roles where possible, such as Security Reviewer, Viewer, and Logging Viewer. Administrative access should only be used when configuration changes are required.

### 9.5 Logging Viewer Access
Logging Viewer access allows users to review logs for investigation and monitoring. Review questions:
- Who can view logs?
- Are logs accessible to only authorised users?
- Do logs contain sensitive activity details?
- Can IAM changes and storage changes be found in Log Explorer?

`Risk`:
Logs may contain sensitive operational information, user activity, IP addresses, system events, and security-relevant details.

`Recommendation`:
Logging access should be granted to users with a valid security, operational, or audit purpose. Log access should not be given to users who do not need it.

### 9.6 External Contractor Access
External developers or contractors may support application deployment or cloud configuration. Review questions:
- Does any external user have access to the project?
- What roles are assigned to the external user?
- Is access time-limited?
- Is access reviewed after the work is completed?
- Is contractor access documented?
- Is privileged access avoided?

`Risk`:
External contractor access can create risk if permissions are excessive, not monitored, or not removed after engagement ends.

`Recommendation`:
Contractor access should be limited to specific work activities, approved by the business owner, reviewed regularly, and removed immediately when no longer required.

`Suggested contractor access model`:

| Contractor Task | Suggested Role |
| --- | --- |
| Review Cloud Run deployment | Cloud Run Viewer |
| Deploy demo Cloud Run service | Cloud Run Developer |
| View logs for troubleshooting | Logs Viewer |
| Access storage object for deployment | Storage Object Viewer or Storage Object Admin, only if required |
| Manage IAM | Not recommended unless specifically approved |

## 10. Service Account Review
Service accounts are used by applications and workloads to access GCP resources.

### 10.1 Service Accounts Identified

| Service Account | Intended Use | Expected Access |
| --- | --- | --- |
| shopsmart-cloudrun-sa | Optional Cloud Run demo app runtime identity. | Minimum access required by the app. |
| shopsmart-storage-review-sa | Storage access review scenario. | Limited storage-specific access. |
| shopsmart-logging-review-sa | Logging access review scenario. | Logging viewer or limited log-related access. |

### 10.2 Service Account Risk Areas

| Risk Area | Description |
| --- | --- |
| Overprivileged service account | Service account has broader access than required. |
| Unused service account | Old or unused service account remains active. |
| Service account key exposure | Downloaded key file could be leaked or reused. |
| Owner or Editor role assigned | Service account can perform broad administrative actions. |
| Unclear ownership | No one knows which workload uses the service account. |
| No review cycle | Permissions are not reviewed periodically. |

### 10.3 Service Account Key Review
Review questions:
- Do any service accounts have user-managed keys?
- Are keys required?
- When were keys created?
- Are old keys still active?
- Are keys stored securely?
- Can keys be replaced with workload identity or managed access?

`Risk`: Service account keys are high-risk because they can be copied, leaked, committed to code repositories, or used outside the GCP environment.

`Recommendation`: Avoid service account keys unless clearly required. If keys exist, they should be documented, rotated, protected, and deleted when no longer needed.

### 10.4 Service Account Role Review
Review questions:
- What roles are assigned to each service account?
- Does each role match the service account’s purpose?
- Does any service account have Owner or Editor?
- Can broad roles be replaced with narrower roles?
- Is the service account used by a specific resource?

`Recommendation`: Each service account should have a clear purpose, named owner, workload association, and least-privilege role assignment.
