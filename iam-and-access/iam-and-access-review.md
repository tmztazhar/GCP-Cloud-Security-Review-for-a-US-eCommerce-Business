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
