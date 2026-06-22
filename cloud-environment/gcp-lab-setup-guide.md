# GCP Lab Setup Guide
## Project: GCP Cloud Security Review for a US eCommerce Business

### Organisation: ShopSmart Online LLC
### Document Owner: Cloud Security Analyst
### Version: 1.0
### Document Status: Portfolio Project – Fictional Business Scenario

## 1. Purpose
The purpose of this GCP Lab Setup Guide is to document how the Google Cloud Platform demo environment for ShopSmart Online LLC is created, configured, reviewed, and safely managed for this cloud security portfolio project.

This guide supports a practical cloud security review by creating a small, controlled GCP environment that can be assessed for identity and access management, service accounts, storage permissions, logging, monitoring, firewall exposure, secrets management, and basic cloud governance.

This lab environment is not a production environment and must not contain real customer data, real payment data, real credentials, or confidential business information.

## 2. Lab Scenario
ShopSmart Online LLC is a fictional US-based eCommerce business that uses Google Cloud Platform to support selected parts of its online business environment.

The lab simulates a small eCommerce cloud environment with:
- A dedicated GCP project.
- Cloud IAM users and roles.
- Service accounts.
- Cloud Storage buckets.
- Cloud Logging and Audit Logs.
- Secret Manager.
- Basic networking review.
- Optional Cloud Run demo application.
- Billing alerts and cost control.
- Security Command Center Standard visibility.

The goal is not to build a full eCommerce platform. The goal is to create enough cloud resources to perform a realistic security review.

## 3. Lab Safety Rules
The following rules must be followed throughout the project:

| Rule | Requirement |
| --- | --- |
| Use dummy data only | Do not upload real customer, payment, order, or business data. |
| Use a dedicated project | Do not use a personal, production, client, or work project. |
| Control cost | Avoid expensive services and configure billing alerts. |
| Limit resources | Create only the resources needed for screenshots and security review. |
| Avoid public exposure | Do not intentionally expose sensitive data publicly. |
| Remove resources after use | Delete unused resources after screenshots and review are completed. |
| Protect credentials | Do not publish real account emails, project IDs, keys, tokens, or secrets. |
| Sanitize screenshots | Blur personal email addresses, billing details, project IDs, and sensitive identifiers before publishing. |
