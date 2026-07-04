# Cloud Architecture Diagram

<img width="1112" height="757" alt="gcp-cloud-security-architecture" src="https://github.com/user-attachments/assets/f6ef72ac-dbea-4241-9e41-d168d2c4d850" />

This diagram shows the simplified GCP lab architecture used for the ShopSmart Online LLC cloud security review. The environment represents a fictional US eCommerce business using Google Cloud for a small, non-production security review lab.

The optional Cloud Run demo web app represents a simple customer-facing eCommerce service. It connects to supporting cloud services such as Cloud Storage for dummy product or order-related files, Secret Manager for a dummy API secret, and Cloud Logging for activity and audit visibility.

The diagram also highlights the key security review areas, including IAM, service accounts, Cloud Storage permissions, Secret Manager access, Cloud Logging, Security Command Center, and billing budget alerts. These areas were selected because they are common sources of cloud security risk for small businesses using GCP.

The purpose of the architecture is not to build a full production eCommerce platform. Instead, it provides a safe and realistic lab environment to review cloud security controls, identify risks, document findings, and produce business-focused recommendations.

No real customer data, payment data, credentials, or production workloads are included in this lab environment.
