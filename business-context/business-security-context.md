# Business Security Context
## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Project Overview
This project presents a practical Google Cloud Platform security review for ShopSmart Online LLC, a fictional small-to-medium US eCommerce business.

The purpose of this project is to assess the security posture of a realistic GCP environment and provide business-focused security recommendations. The review focuses on identity and access management, multi-factor authentication, service accounts, storage permissions, logging, monitoring, network exposure, cloud governance, and security improvement planning.

This project is designed for a cyber security portfolio and demonstrates practical cloud security, GRC, and risk assessment skills using a realistic SME cloud environment rather than enterprise-only tooling.

## 2. Business Scenario
ShopSmart Online LLC is a fictional US-based eCommerce business that sells consumer products through an online store.

The business uses Google Cloud Platform to support selected parts of its cloud environment, including application hosting, storage, logging, and administrative access management.

The company has approximately 35 employees across operations, customer support, marketing, finance, fulfilment coordination, and technology support.

ShopSmart does not have a large internal security team. Cloud administration is handled by a small internal IT team with support from an external development contractor.

## 3. Business Objectives
The security review supports the following business objectives:

| Business Objective | Security Relevance |
| --- | --- |
| Protect customer trust | Reduce risk of unauthorised access to customer and order-related information. |
| Maintain eCommerce availability | Reduce risk of downtime affecting online sales and customer access. |
| Improve cloud governance | Ensure cloud resources, IAM roles, and service accounts are managed properly. |
| Reduce account compromise risk | Review MFA, IAM, privileged access, and service account exposure. |
| Improve detection capability | Review logging, audit logs, and monitoring coverage. |
| Support secure growth | Provide practical recommendations as the business expands cloud usage. |
| Reduce supplier and contractor risk | Review access granted to external developers and third-party users. |

## 4. Technology Environment
ShopSmart uses a small GCP environment designed for a realistic portfolio lab. The environment may include the following services:

| Area | Example GCP Service |
| --- | --- |
| Project management | Google Cloud Project |
| Identity and access | IAM, service accounts |
| Application hosting | Cloud Run or App Engine |
| Object storage | Cloud Storage |
| Database | Cloud SQL |
| Secrets | Secret Manager |
| Logging | Cloud Logging |
| Audit logging | Cloud Audit Logs |
| Monitoring | Cloud Monitoring |
| Security visibility | Security Command Center Standard |
| Networking | VPC firewall rules |
| Billing governance | Budgets and alerts |

This project does not require a full production eCommerce platform. It uses a controlled lab environment to simulate realistic cloud security review activities.
