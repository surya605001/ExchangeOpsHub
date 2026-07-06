# 04 - Exchange Discovery
# Objective
Exchange Discovery is the process of collecting detailed information about the Microsoft Exchange organization. It provides administrators with a complete understanding of the Exchange configuration before performing maintenance, troubleshooting, migrations, or upgrades.

The objective is to establish a reliable baseline of the Exchange environment.
# Scope
This document covers:

- Exchange Organization
- Exchange Servers
- Exchange Version
- Mailbox Databases
- Client Access Services
- Virtual Directories
- Send Connectors
- Receive Connectors
- Certificates
- Exchange Services

# Discovery Workflow

Start
↓
Identify Exchange Organization
↓
Identify Exchange Servers
↓
Verify Exchange Version
↓
Discover Databases
↓
Verify Client Access Services
↓
Review Mail Flow Configuration
↓
Review Certificates
↓
Verify Exchange Services
↓
Document Findings
↓
End

# Step 1 – Exchange Organization
```powershell
Get-OrganizationConfig
```

### Purpose
Displays the configuration of the Exchange organization.

### Verify
- Organization Name
- Hybrid Configuration
- MailTips
- Address Book Policies
- Distribution Groups


# Step 2 – Exchange Servers

```powershell
Get-ExchangeServer | Format-Table Name,Edition,AdminDisplayVersion,Fqdn
```

```text
Name     Edition      AdminDisplayVersion         FQDN
------------------------------------------------------------
EXCH01   Enterprise   Version 15.2 (Build 1544.4) exch01.contoso.com
EXCH02   Enterprise   Version 15.2 (Build 1544.4) exch02.contoso.com


# Step 3 – Exchange Build Information

```powershell
Get-ExchangeServer | Select Name,AdminDisplayVersion
```
### Why?
Always verify the installed Cumulative Update (CU).
Running unsupported Exchange builds can introduce security and support risks.

---

# Step 4 – Mailbox Databases
##
```
Get-MailboxDatabase -Status
```
### Verify
- Database Status
- Mounted State
- Database Size
- Available Space
- Log Path
- EDB Path

---

# Step 5 – Client Access Services

## 
```powershell
Get-ClientAccessService
```

### Purpose
Displays Client Access Service configuration for Exchange servers.

---

# Step 6 – Virtual Directories

Useful discovery commands:

```powershell
Get-OwaVirtualDirectory
```
```powershell
Get-EcpVirtualDirectory
```
```powershell
Get-WebServicesVirtualDirectory
```
```powershell
Get-MapiVirtualDirectory
```
```powershell
Get-ActiveSyncVirtualDirectory
```
```powershell
Get-AutodiscoverVirtualDirectory
```
---

# Step 7 – Send Connectors

```powershell
Get-SendConnector
```
Verify:
- Address Spaces
- Smart Hosts
- Source Transport Servers

---

# Step 8 – Receive Connectors

```powershell
Get-ReceiveConnector
```

Verify:
- Bindings
- Remote IP Ranges
- Authentication
- Permission Groups

---
# Step 9 – Exchange Certificates

```powershell
Get-ExchangeCertificate
```

Verify:

- Thumbprint
- Subject
- Services
- Expiry Date
- Certificate Status

---

# Step 10 – Exchange Services

```powershell
Get-Service *Exchange*
```
Ensure all critical Exchange services are running.

---

# Discovery Checklist
Complete the following:
- Exchange Organization
- Exchange Version
- Exchange Servers
- Mailbox Databases
- Client Access Services
- Virtual Directories
- Send Connectors
- Receive Connectors
- Certificates
- Exchange Services

---
# Best Practices
- Perform Exchange Discovery before every major project.
- Export command output for documentation.
- Record Exchange build numbers.
- Verify certificate expiry dates.
- Document every configuration change.

---

# Summary
Exchange Discovery is the core of understanding an Exchange environment.
Without a complete Exchange Discovery, troubleshooting and change management become significantly more difficult.
A well-documented Exchange organization enables faster issue resolution and reduces operational risk.

---

# Next Document

**05-Active-Directory-Discovery.md**
