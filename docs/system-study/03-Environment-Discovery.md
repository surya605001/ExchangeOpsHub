# 03 - Environment Discovery

# Objective
The purpose of Environment Discovery is to identify and document the complete Microsoft Exchange environment before performing administration, troubleshooting, migrations, upgrades, or health assessments.
Environment Discovery provides a baseline of the existing infrastructure and ensures engineers understand the production environment before making changes.

# Scope
This document covers:
- Exchange Organization
- Exchange Servers
- Active Directory
- Mailbox Databases
- Database Availability Groups (DAG)
- Client Access Services
- Mail Flow
- Certificates
- Exchange Services

# Why Environment Discovery?
Before making any production change, always answer these questions:
- What servers exist?
- Which Exchange version is installed?
- Which CU is installed?
- How many mailbox databases exist?
- Is DAG configured?
- Which certificates are used?
- How does mail flow?
- What virtual directories exist?

Without this information, troubleshooting becomes inefficient and risky.

# Environment Discovery Workflow
Start
↓
Collect Exchange Information
↓
Collect Active Directory Information
↓
Collect Database Information
↓
Collect DAG Information
↓
Collect Mail Flow Information
↓
Collect Certificate Information
↓
Validate Exchange Health
↓
Document Findings
↓
End

# Step 1 – Discover Exchange Servers:
         Get-ExchangeServer | Format-Table Name,Edition,AdminDisplayVersion,ServerRole

Name      Edition     AdminDisplayVersion                 ServerRole
-----------------------------------------------------------------------
EXCH01    Enterprise  Version 15.2 (Build 1544.4)         Mailbox
EXCH02    Enterprise  Version 15.2 (Build 1544.4)         Mailbox


### Explanation
| Field | Description |
|-------|-------------|
| Name | Exchange Server Name |
| Edition | Standard or Enterprise |
| AdminDisplayVersion | Exchange Version and CU |
| ServerRole | Installed Exchange Role |

# Step 2 – Discover Mailbox Databases:
         Get-MailboxDatabase | Format-Table Name,Server,Mounted

Name          Server      Mounted
---------------------------------
DB01          EXCH01      True
DB02          EXCH02      True

### Explanation
Mounted = True means the database is online.
Mounted = False means the database is dismounted.

# Step 3 – Discover Database Availability Groups  
         Get-DatabaseAvailabilityGroup
Name
-----
DAG01

### Purpose
Shows whether Exchange High Availability is configured.

# Step 4 – Discover Client Access Services
         Get-ClientAccessService

Name
----
EXCH01
EXCH02


# Step 5 – Discover Send Connectors
         Get-SendConnector

Name
Internet Send Connector

Purpose:Shows outbound mail routing.

# Step 6 – Discover Receive Connectors
         Get-ReceiveConnector
Purpose:Shows inbound SMTP connectors.

# Step 7 – Discover Exchange Certificates
        Get-ExchangeCertificate

Purpose:Lists all Exchange certificates.

Verify:
- Expiry Date
- Services
- Thumbprint
- Subject

# Step 8 – Discover Exchange Services
         Get-Service *Exchange*
Purpose:Displays all Exchange Windows services.
Ensure critical services are running.

# Environment Discovery Checklist
- Exchange Servers
- Exchange Version
- CU Level
- Mailbox Databases
- DAG
- Certificates
- Send Connectors
- Receive Connectors
- Exchange Services
- Mail Flow
- Client Access Services

# Best Practices
- Perform discovery before making changes.
- Save command outputs for future reference.
- Compare discovery results after major changes.
- Document unsupported configurations.
- Keep inventory updated.

# Summary
Environment Discovery is the foundation of Exchange administration.
A complete discovery process helps engineers understand the environment, reduce operational risks, and troubleshoot efficiently.

# Next Document
**04-Exchange-Discovery.md**
