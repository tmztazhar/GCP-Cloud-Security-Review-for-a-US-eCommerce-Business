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
