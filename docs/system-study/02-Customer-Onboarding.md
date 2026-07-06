# 02 - Customer Onboarding

# Objective
The objective of Customer Onboarding is to understand the customer's IT environment before taking ownership of the Microsoft Exchange infrastructure.
A successful onboarding process ensures that the support team has all the technical, operational, and business information required to provide efficient support.

# Scope
This document covers:

- Customer information
- Business requirements
- Support contacts
- Exchange environment overview
- Active Directory overview
- Infrastructure information
- Backup solution
- Monitoring solution
- Documentation requirements
- Knowledge Transfer (KT) checklist

# Why is Customer Onboarding Important?
Before supporting any Exchange environment, engineers must understand the customer's infrastructure.

Without proper onboarding:

- Troubleshooting becomes difficult.
- Documentation is incomplete.
- Configuration mistakes are more likely.
- Knowledge is dependent on individuals.
- Support quality decreases.

A structured onboarding process minimizes these risks.

# Customer Information Checklist
Collect the following information during onboarding.

| Item | Details |
|------|---------|
| Customer Name | |
| Business Unit | |
| Primary Contact | |
| Secondary Contact | |
| Support Email | |
| Support Hours | |
| Time Zone | |
| Data Center Location | |
| Business Critical Applications | |

# Exchange Environment Information
Collect the following Exchange details.

| Item | Example |
|------|---------|
| Exchange Version | Exchange Server 2019 CU15 |
| Number of Exchange Servers | |
| Exchange Roles | Mailbox |
| Database Availability Group | Yes / No |
| Number of Mailbox Databases | |
| Number of Mailboxes | |
| Hybrid Deployment | Yes / No |
| Exchange Online | Yes / No |


# Active Directory Information
| Item | Details |
|------|---------|
| Forest Name | |
| Domain Name | |
| Number of Domain Controllers | |
| Active Directory Functional Level | |
| Sites and Services | |
| DNS Servers | |

# Server Inventory
Document every Exchange server.

| Server Name | Version | Operating System | Location | Status |
|-------------|----------|-----------------|----------|--------|
| | | | | |

---

# Database Inventory

Collect information about mailbox databases.

| Database | Mounted | Server | Size | Free Space |
|----------|----------|--------|------|-----------|
| | | | | |


# Certificate Inventory
Document all Exchange certificates.

| Certificate | Expiry Date | Services | Status |
|-------------|-------------|----------|--------|
| | | | |


# Mail Flow Information
Document how mail flows through the environment.

Information to collect:
- Send Connectors
- Receive Connectors
- SMTP Smart Hosts
- Mail Gateways
- Anti-Spam Solution
- Anti-Virus Solution

# Network Information
Document:
- Load Balancers
- Firewall Rules
- Reverse Proxy
- External URLs
- Internal URLs
- Autodiscover URL
- Outlook Anywhere
- OWA URL
- ECP URL
- MAPI URL
- EWS URL

# Backup Solution
Document:
- Backup Product
- Backup Schedule
- Backup Retention
- Recovery Testing
- Database Restore Procedure

# Monitoring Solution
Document:
- Monitoring Tool
- Alerting Method
- Email Notifications
- Dashboard
- Performance Monitoring

# Knowledge Transfer (KT) Checklist
During KT, ensure the following topics are covered.
- Exchange Architecture
- Mail Flow
- Database Layout
- DAG Configuration
- Certificates
- Exchange Services
- Backup Procedures
- Disaster Recovery
- Monitoring
- Known Issues
- Maintenance Tasks
- Escalation Process

# Questions to Ask During KT
Examples:
1. Are there any known issues?
2. What are the daily operational tasks?
3. How are backups verified?
4. How is Disaster Recovery performed?
5. Are there pending changes?
6. Are there unsupported configurations?
7. Are there recurring incidents?
8. Are there maintenance windows?
9. How is Exchange monitored?
10. Who owns DNS and Certificates?

# Deliverables
At the end of onboarding, the following documents should be available.
- Server Inventory
- Database Inventory
- Certificate Inventory
- Mail Flow Diagram
- Exchange Architecture Diagram
- Health Assessment
- KT Notes
- Support Contacts
- Escalation Matrix

# Best Practices
- Verify information instead of assuming.
- Keep documentation updated.
- Store documentation in a central repository.
- Review documentation periodically.
- Validate Exchange configuration using supported PowerShell cmdlets.

# Summary
Customer Onboarding is the first operational step before taking ownership of an Exchange environment.
A complete onboarding process improves support quality, reduces troubleshooting time, and ensures knowledge is shared across the support team.

# Next Document
Continue with:
**03-Environment-Discovery.md**
