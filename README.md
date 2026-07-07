# GCP Cloud Security Review for a US eCommerce Business

A practical cloud security portfolio project reviewing IAM, service accounts, Cloud Storage, Secret Manager, logging, monitoring, cloud risks, and security recommendations for a fictional US eCommerce business using Google Cloud Platform.

## Project Overview

This project presents a practical Google Cloud Platform security review for ShopSmart Online LLC, a fictional small-to-medium US eCommerce business.

The purpose of this project is to demonstrate how a cloud security analyst or GRC analyst can review a GCP environment, identify security risks, document findings, and communicate practical recommendations to business stakeholders.

This project focuses on realistic cloud security areas that matter to small businesses, including identity and access management, service account security, storage permissions, logging visibility, secrets management, cloud governance, cost control, and executive reporting.

## Business Scenario

ShopSmart Online LLC is a fictional US-based eCommerce business that sells consumer products online.

The company uses Google Cloud Platform to support selected parts of its cloud environment, including application hosting, storage, logging, security visibility, and access management.

The fictional business has approximately 35 employees across operations, customer support, marketing, finance, fulfilment coordination, and technology support.

ShopSmart does not have a large internal cyber security team. Cloud administration is handled by a small technical team with support from an external development contractor.

## Project Objectives

The objectives of this project are to:
1. Create a realistic GCP security review scenario for a small eCommerce business.
2. Assess IAM users, roles, privileged access, and service accounts.
3. Review Cloud Storage permissions and public access risk.
4. Review Secret Manager access and secrets handling.
5. Review Cloud Logging, Audit Logs, and monitoring visibility.
6. Identify cloud security risks and document them in a risk register.
7. Provide practical, prioritised security recommendations.
8. Produce executive-level reporting suitable for business leadership.
9. Create a portfolio-ready project for GitHub, Medium, and resume use.

## Key Review Areas

| Area |	What Was Reviewed |
| --- | --- |
| IAM |	Users, roles, privileged access, Owner and Editor permissions. |
| Service Accounts |	Service account purpose, permissions, keys, and least privilege. |
| Cloud Storage |	Bucket permissions, public access prevention, and sensitive data exposure risk. |
| Secret Manager |	Secret access control, dummy secrets, and screenshot handling. |
| Cloud Logging |	Admin activity, IAM changes, service account activity, and audit visibility. |
| Security Command Center |	Standard findings and cloud security posture observations. |
| VPC Firewall Rules |	Public exposure and unnecessary broad access. |
| Billing |	Budget alerts and cost governance. |
| Risk Management |	Cloud risks, likelihood, impact, residual risk, and treatment actions. |
| Executive Reporting |	Business-focused summary of risks, recommendations, and roadmap. |

## Main Deliverables

### Business Security Context

Defines the fictional company, business model, cloud environment, sensitive information, project scope, assumptions, and learning objectives.

### GCP Lab Setup Guide

Explains how to create a safe, low-cost GCP lab environment for portfolio purposes without using real customer data, payment data, or production workloads.

### Cloud Environment Overview

Documents the GCP services included in the lab, including IAM, service accounts, Cloud Storage, Secret Manager, Cloud Logging, Security Command Center, VPC firewall rules, billing alerts, and optional Cloud Run.

### GCP Security Review Checklist

An Excel-based checklist used to assess cloud security areas such as IAM, storage, logging, secrets, service accounts, networking, and governance.

### IAM and Access Review

Reviews users, roles, privileged access, service accounts, service account keys, contractor access, MFA considerations, and access review processes.

### Logging and Monitoring Review

Reviews Cloud Logging, Audit Logs, IAM activity, service account activity, storage changes, Secret Manager activity, Security Command Center findings, and alerting considerations.

### Cloud Risk Register

Records realistic GCP cloud security risks, likelihood, impact, inherent risk, residual risk, existing controls, treatment actions, owners, and status.

### Security Recommendations Report

Provides prioritised recommendations to reduce cloud security risk, including IAM hardening, service account review, storage protection, secrets control, logging review, contractor access governance, and cost alerts.

### Cloud Architecture Diagram

Shows the simplified GCP lab architecture used for the security review.

### Executive Cloud Security Summary

Summarises the key findings, highest-priority risks, maturity assessment, 90-day roadmap, security metrics, business benefits, and residual risk statement.

## Key Risks Identified

This project addresses realistic cloud security risks, including:
- Overprivileged IAM users.
- Excessive Owner or Editor role assignments.
- Overprivileged service accounts.
- Service account key exposure.
- Public Cloud Storage bucket exposure.
- Broad access to Secret Manager.
- Weak logging and monitoring review.
- Unreviewed contractor access.
- Poor resource ownership and labelling.
- Unexpected cloud costs.
- Limited executive visibility of cloud risks.

## Priority Recommendations

The highest-priority recommendations are:
1. Limit Project Owner access to trusted administrators only.
2. Remove or reduce Editor roles.
3. Review all service account permissions.
4. Avoid service account keys where possible.
5. Restrict Secret Manager access.
6. Review Cloud Storage bucket permissions.
7. Confirm public access prevention for sensitive buckets.
8. Review IAM and service account activity in Cloud Logging.
9. Configure billing budget alerts.
10. Maintain a cloud risk register and review it regularly.

## 90-Day Security Roadmap

| Timeframe |	Focus |
| --- | --- |
| Days 1–30 |	Review Owner and Editor access, service accounts, service account keys, Secret Manager access, Cloud Storage permissions, and billing alerts. |
| Days 31–60 |	Review Cloud Logging, Security Command Center findings, contractor access, log access, labels, and update the cloud risk register. |
| Days 61–90 |	Complete formal IAM review, service account review, storage classification, cloud security baseline, leadership reporting, and final portfolio documentation. |

## Skills Demonstrated

This project demonstrates practical skills in:
- GCP cloud security review.
- IAM and privileged access review.
- Service account security.
- Cloud Storage security.
- Secret Manager access control.
- Cloud Logging and Audit Logs review.
- Security Command Center review.
- Cloud risk assessment.
- Security recommendations writing.
- Executive reporting.
- Cloud governance.
- GRC documentation.
- Business-focused cyber security communication.
- Portfolio project presentation.

## Important Notes

This is a fictional portfolio project.

ShopSmart Online LLC is not a real company. The cloud environment, risks, findings, screenshots, and recommendations are created for learning and portfolio purposes only.

No real customer data, payment data, credentials, API keys, or production workloads are included in this project.

This project is not a penetration test, legal assessment, compliance certification, PCI DSS audit, or full production cloud security assessment.

## Licence

Copyright (c) 2026 `TENGKU MUHAMMAD ZULFADLI`. All Rights Reserved.

This repository is provided for portfolio evaluation and professional review purposes only. No part of this repository may be copied, reproduced, modified, redistributed, or reused without prior written permission from the copyright owner.
