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
