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

## 5. Sensitive Information Handled
ShopSmart may handle or process the following types of information:

| Information Type | Example | Security Concern |
| --- | --- | --- |
| Customer information | Name, email, phone number, shipping address | Privacy, phishing, customer trust impact |
| Order information | Order ID, product details, delivery status | Business confidentiality, customer service impact |
| Payment-related information | Payment provider reference, transaction status | Fraud risk, financial process risk |
| Product data | Product catalogue, images, descriptions | Integrity and availability |
| Business data | Sales reports, operational files | Commercial confidentiality |
| Application secrets | API keys, database credentials, tokens | High risk if exposed |
| Logs | Access logs, admin activity, audit records | Sensitive operational and security information |
| Admin accounts | IAM users and service accounts | Privileged access risk |

This project does not use real customer data, real payment card data, real credentials, or real production systems.

## 6. Key Cloud Security Concerns
The main cloud security concerns for ShopSmart are:

| Risk Area | Example Scenario |
| --- | --- |
| Overprivileged IAM roles | Users or service accounts have broader permissions than required. |
| Weak account security | MFA is not consistently used for administrative accounts. |
| Public Cloud Storage exposure | A storage bucket is accidentally made public. |
| Poor service account management | Unused or overprivileged service accounts remain active. |
| Inadequate logging | Important admin or data access activity is not logged or reviewed. |
| Weak network controls | Firewall rules allow unnecessary public access. |
| Secret exposure | API keys or credentials are stored insecurely. |
| Contractor access risk | External developer access is not time-limited or reviewed. |
| Poor environment separation | Development and production-like resources are not clearly separated. |
| Lack of governance | No clear ownership, review cycle, or cloud security baseline. |

## 7. Applicable Frameworks and References
This project uses practical cloud security and governance concepts aligned to:

| Framework / Reference | How It Is Used |
| --- | --- |
| Google Cloud security best practices | Used to review IAM, logging, service accounts, storage, and cloud configuration. |
| CIS Google Cloud Platform Foundations Benchmark | Used as a reference point for cloud configuration review areas. |
| NIST Cybersecurity Framework | Used conceptually for identify, protect, detect, respond, and recover thinking. |
| ISO/IEC 27001-style control thinking | Used for governance, access control, logging, supplier access, and risk treatment. |
| Least privilege principle | Used to assess IAM roles and service account permissions. |
| Shared responsibility model | Used to distinguish responsibilities between Google Cloud and the customer. |

This is not a formal compliance audit. It is a portfolio security review based on practical cloud security assessment methods.

## 8. Project Scope
This project includes a security review of the following areas:

| In Scope |
| --- |
| GCP project structure |
| IAM users and roles |
| Privileged access |
| MFA and account security observations |
| Service accounts |
| Cloud Storage bucket permissions |
| Cloud Logging and Cloud Audit Logs |
| Security Command Center Standard observations |
| VPC firewall rules |
| Secret Manager usage |
| Cloud Run or App Engine application exposure |
| Billing alerts and basic governance |
| Cloud security risk register |
| Security recommendations |
| Executive cloud security summary |
| Architecture diagram |
| Screenshots from the GCP lab environment |

## 9. Out of Scope
The following items are outside the scope of this portfolio project:

| Out of Scope | Reason |
| --- | --- |
| Real production customer data | This is a fictional portfolio lab. |
| Payment card processing review | No real payment card data is used. |
| PCI DSS audit | This project is not a formal PCI assessment. |
| Penetration testing | The focus is cloud security review and governance. |
| Red team activity | Not required for this project. |
| Enterprise SIEM deployment | Not realistic for this SME lab scenario. |
| GKE cluster security | Avoided to reduce cost and complexity. |
| Large Cloud SQL deployment | Not required for the core project. |
| Paid Security Command Center Premium features | Standard/free visibility is sufficient for this portfolio project. |
| Full legal or compliance advice | This project is educational and portfolio-based. |

## 10. GCP Lab Environment Assumptions
This project assumes:

| Assumption |
| --- |
| A dedicated GCP project is created only for this portfolio lab. |
| No real customer information is uploaded. |
| No real payment card data is processed. |
| Dummy sample data is used where data is needed. |
| The lab is created with cost control in mind. |
| Billing alerts are configured to reduce unexpected charges. |
| Expensive resources such as GKE, GPUs, and large databases are avoided. |
| Screenshots are taken from the user’s own GCP console. |
| Resources are deleted after screenshots and review activities are completed. |
| The project demonstrates cloud security review skills, not production deployment. |

## 11. Suggested Demo Architecture

The lab environment may use this simple architecture:

`Internet User` --> `Cloud Run / App Engine Demo Web App` = Cloud Storage Bucket + Secret Manager + Cloud Logging / Audit Logs + IAM Users and Service Accounts

## 12. Main Review Questions
This cloud security review will answer the following questions:
1. Are IAM roles assigned using least privilege?
2. Are any users or service accounts overprivileged?
3. Are service accounts managed securely?
4. Are unused accounts or excessive permissions present?
5. Are Cloud Storage buckets publicly exposed?
6. Are audit logs enabled and useful for investigation?
7. Are administrative actions visible in Cloud Logging?
8. Are firewall rules too broad?
9. Are secrets stored securely?
10. Are external contractors given appropriate access?
11. Are billing alerts and basic governance controls configured?
12. What are the highest-priority security improvements?
13. How should risks be communicated to business leadership?

## 13. Expected Deliverables
The completed project will include:

| Deliverable | Purpose |
| --- | --- |
| Business Security Context | Defines the business scenario, scope, assumptions, and review purpose. |
| GCP Lab Setup Guide | Explains how the demo environment was created safely. |
| Cloud Architecture Diagram | Shows the demo GCP environment and security review scope. |
| GCP Security Review Checklist | Documents the review areas and findings. |
| IAM and Access Review | Reviews users, roles, service accounts, and privileged access. |
| Logging and Monitoring Review | Reviews Cloud Logging, audit logs, alerts, and visibility. |
| Cloud Risk Register | Records risks, likelihood, impact, existing controls, and treatment actions. |
| Security Recommendations Report | Provides prioritised technical and business recommendations. |
| Executive Cloud Security Summary | Summarises key findings for business leadership. |

## 14. Security Review Method
The review will follow this practical process:
1. Define business scenario and scope
2. Create safe GCP demo project
3. Configure basic lab resources
4. Review IAM and access controls
5. Review service accounts
6. Review storage permissions
7. Review logging and audit visibility
8. Review firewall and exposure settings
9. Review secrets handling
10. Record findings
11. Score risks
12. Write recommendations
13. Produce executive summary

## 15. Learning Objectives
This project demonstrates the ability to:

| Skill Demonstrated | Evidence |
| --- | --- |
| Cloud security review | GCP security checklist and findings. |
| IAM analysis | IAM and access review documentation. |
| Service account review | Service account risk assessment. |
| Storage security | Cloud Storage bucket permission review. |
| Logging review | Cloud Logging and audit log assessment. |
| Risk assessment | Cloud risk register and treatment plan. |
| GRC communication | Executive summary and security recommendations. |
| Business understanding | eCommerce-focused risk framing. |
| Cloud governance | Ownership, review process, access control, and improvement roadmap. |

## 16. Portfolio Note
This project is a fictional cloud security portfolio project. ShopSmart Online LLC is not a real company.

The GCP environment used for this project is a demo lab environment created for learning and portfolio purposes only. It must not contain real customer data, real payment data, real credentials, or production workloads.

This project is not a legal assessment, compliance audit, penetration test, or full production security review.
