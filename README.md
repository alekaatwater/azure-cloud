# Azure Hybrid Cloud Migration

## Overview
A nationwide logistics company operating across four leased on premises data centers faced mounting pressure from rising infrastructure costs, service interruptions, and growing cybersecurity concerns. With a NIST SP 800-53 assessment on the horizon and active obligations under FISMA and PCI DSS, leadership made the decision to migrate to Microsoft Azure. This project documents the planning and implementation of a secure hybrid cloud environment designed to address critical security gaps and bring the organization into compliance.

## The Problem
Several critical security issues required immediate attention prior to and during the migration:

- Users could access data and assets belonging to other departments, indicating a breakdown in access control
- IT administrators were unable to verify file and system backups
- Vulnerability scanning boundaries had not been validated in over two years
- The cloud environment was potentially non compliant with federal regulations, putting government contracts at risk

## Compliance Frameworks
- FISMA (Federal Information Security Modernization Act)
- PCI DSS (Payment Card Industry Data Security Standard)
- NIST SP 800-53 Security and Privacy Controls

## Tools and Technologies
- Microsoft Azure (IaaS)
- Azure Role Based Access Control (RBAC)
- Microsoft Entra ID and Privileged Identity Management (PIM)
- Azure Key Vault
- Azure Backup and Recovery Vault
- Azure Policy
- Microsoft Defender for Cloud

## What Was Implemented

### Service Model
Recommended and justified an Infrastructure as a Service (IaaS) model, giving the organization control over virtual machines, storage, and network configurations while enabling regulatory compliance.

### Role Based Access Control (RBAC)
- Reorganized users into their correct departmental resource groups (Accounting, Marketing and IT)
- Assigned read only access to standard users to enforce least privilege
- Created security groups with time bound administrative privileges using PIM
- Configured Contributor roles for Marketing and Accounting admins with 90 day reactivation periods and LOD Contributor for IT admins with 30 day reactivation periods
- Applied resource tags across all departments for visibility and data governance
- Recommended dedicated storage accounts per department

### Encryption
- Relocated Key Vaults to their correct departmental resource groups
- Enabled Soft Delete and Purge Protection on all Key Vaults
- Disabled public access on all Key Vaults
- Created a dedicated IT Key Vault
- Recommended Customer Managed Keys (CMK) for data at rest encryption
- Recommended TLS certificate management through Azure Key Vault for data in transit encryption

### Backup Configuration
- Created a Recovery Vault and custom backup policy
- Configured a backup policy meeting a 1 day RPO and 36 hour RTO
- Set daily backups at 7:00 PM EST with 45 day retention
- Configured instant recovery snapshots with 3 day retention
- Aligned backup policy with FISMA controls CP-6 and CP-9 and PCI DSS Requirement 12.10

## Full Project Report
[View Full Report (PDF)](./GithubAzureProject.pdf)
