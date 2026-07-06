# 06 - Server Inventory

---

# Objective

The purpose of the Server Inventory is to collect and document detailed information about every Exchange Server in the organization.

Maintaining an accurate inventory helps during troubleshooting, patching, migrations, upgrades, capacity planning, disaster recovery, and customer Knowledge Transfer (KT).

---

# Scope

This document covers:

- Exchange Server Details
- Windows Server Details
- Hardware Configuration
- Network Configuration
- Exchange Version
- CU / SU Level
- Storage Configuration
- Installed Roles
- Server Health

---

# Why Server Inventory is Important

A complete server inventory enables administrators to:

- Understand the Exchange infrastructure.
- Verify Exchange build versions.
- Plan upgrades.
- Troubleshoot server-specific issues.
- Maintain operational documentation.
- Prepare Disaster Recovery documentation.

---

# Inventory Workflow

```text
Identify Exchange Server
        │
        ▼
Collect Operating System Details
        │
        ▼
Collect Exchange Details
        │
        ▼
Collect Hardware Details
        │
        ▼
Collect Network Details
        │
        ▼
Collect Storage Details
        │
        ▼
Validate Health
        │
        ▼
Document Inventory
```

---

# Step 1 – Exchange Server Information

### PowerShell

```powershell
Get-ExchangeServer | Format-List Name,Edition,AdminDisplayVersion,Fqdn
```

### Verify

- Server Name
- Exchange Edition
- Exchange Version
- FQDN

---

# Step 2 – Windows Server Information

### PowerShell

```powershell
Get-ComputerInfo
```

### Verify

- Operating System
- Build Number
- Manufacturer
- Model
- Total Physical Memory
- Installed Date

---

# Step 3 – Hardware Information

### PowerShell

```powershell
Get-CimInstance Win32_Processor
```

```powershell
Get-CimInstance Win32_PhysicalMemory
```

### Verify

- CPU Model
- Number of Processors
- Number of Cores
- Installed RAM

---

# Step 4 – Disk Information

### PowerShell

```powershell
Get-Volume
```

### Verify

- Drive Letter
- File System
- Total Size
- Free Space
- Health Status

---

# Step 5 – Network Information

### PowerShell

```powershell
Get-NetIPAddress
```

### Verify

- IPv4 Address
- Subnet Mask
- Default Gateway
- DNS Servers

---

# Step 6 – Exchange Services

### PowerShell

```powershell
Get-Service *Exchange*
```

Verify that all critical Exchange services are running.

---

# Step 7 – Windows Services

### PowerShell

```powershell
Get-Service
```

Check for stopped services that may impact Exchange.

---

# Sample Inventory Table

| Item | Value |
|------|-------|
| Server Name | EXCH01 |
| Operating System | Windows Server 2022 |
| Exchange Version | Exchange Server 2019 |
| Exchange Build | CU15 |
| CPU | Intel Xeon |
| RAM | 64 GB |
| Storage | 2 TB |
| IP Address | 10.10.10.20 |
| DAG Member | Yes |

---

# Health Checklist

- Exchange Services Running
- Adequate Disk Space
- CPU Utilization Normal
- Memory Utilization Normal
- Network Connectivity Healthy
- Windows Event Logs Reviewed

---

# Best Practices

- Maintain an updated server inventory.
- Record Exchange CU and SU levels.
- Track hardware upgrades.
- Verify storage capacity regularly.
- Review inventory after every major change.

---

# Common Issues

- Outdated Exchange CU
- Low disk space
- High CPU usage
- Insufficient RAM
- Network configuration errors

---

# Interview Questions

1. Why is server inventory important?
2. Which PowerShell command retrieves Exchange server details?
3. How do you verify hardware information?
4. Why should Exchange build numbers be documented?
5. What server information should be reviewed before upgrading Exchange?

---

# Production Notes

Before performing maintenance or upgrades, always verify:

- Server health
- Exchange version
- Operating system version
- Available disk space
- Recent backups

---

# Microsoft Learn

Recommended reading:

- Exchange Server system requirements
- Exchange Server updates
- Exchange Server deployment planning

---

# Summary
A complete Server Inventory provides the baseline information required for successful administration, troubleshooting, and long-term maintenance of Exchange Server environments.
---

# Next Document

**07-Database-Inventory.md**
