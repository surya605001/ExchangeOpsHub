# 07 - Database Inventory

---

# Objective

The objective of a Database Inventory is to collect complete information about all Exchange Mailbox Databases within the organization.

A properly maintained database inventory helps administrators understand database layout, storage utilization, high availability, backup requirements, and operational health.

---

# Scope

This guide covers:

- Mailbox Databases
- Database Status
- Database Size
- EDB File Location
- Log File Location
- Circular Logging
- Mount Status
- DAG Copies
- White Space
- Backup Status

---

# Theory

In Microsoft Exchange Server, mailbox data is stored in **Mailbox Databases**.

Each database consists of:

- EDB file
- Transaction log files
- Checkpoint files
- Database copies (if DAG is configured)

Proper documentation of these components is essential for disaster recovery and operational support.

---

# Database Discovery Workflow

```text
Identify Databases
        │
        ▼
Verify Mounted Status
        │
        ▼
Collect Database Size
        │
        ▼
Verify EDB Path
        │
        ▼
Verify Log Path
        │
        ▼
Check Circular Logging
        │
        ▼
Review Database Copies
        │
        ▼
Document Findings
```

---

# Step 1 – List Mailbox Databases

### PowerShell

```powershell
Get-MailboxDatabase
```

### Purpose

Lists all mailbox databases in the Exchange organization.

---

# Step 2 – Database Status

### PowerShell

```powershell
Get-MailboxDatabase -Status
```

### Verify

- Mounted
- Database Size
- Available New Mailbox Space
- Last Full Backup
- Last Incremental Backup

---

# Step 3 – Database File Paths

### PowerShell

```powershell
Get-MailboxDatabase | Format-List Name,EdbFilePath,LogFolderPath
```

### Sample Output

```text
Name          : DB01
EdbFilePath   : E:\Mailbox Database\DB01\DB01.edb
LogFolderPath : E:\Mailbox Logs\DB01
```

### Explanation

| Field | Description |
|-------|-------------|
| Name | Mailbox Database Name |
| EdbFilePath | Location of the .EDB database file |
| LogFolderPath | Transaction log location |

---

# Step 4 – Database Copies (DAG)

### PowerShell

```powershell
Get-MailboxDatabaseCopyStatus *
```

### Verify

- Copy Status
- Copy Queue Length
- Replay Queue Length
- Content Index State

---

# Step 5 – Circular Logging

### PowerShell

```powershell
Get-MailboxDatabase | Select Name,CircularLoggingEnabled
```

### Verify

Determine whether circular logging is enabled.

---

# Step 6 – Database White Space

### PowerShell

```powershell
Get-MailboxDatabase -Status | Select Name,DatabaseSize,AvailableNewMailboxSpace
```

### Purpose

Review database growth and available white space.

---

# Sample Inventory Table

| Item | Value |
|------|-------|
| Database Name | DB01 |
| Mounted | Yes |
| Database Size | 850 GB |
| White Space | 120 GB |
| EDB Path | E:\Mailbox Database\DB01\DB01.edb |
| Log Path | E:\Mailbox Logs\DB01 |
| Circular Logging | Disabled |
| DAG Copies | 2 |

---

# Health Checklist

- Database Mounted
- Backup Successful
- Adequate Free Space
- Healthy DAG Copies
- Low Copy Queue Length
- Low Replay Queue Length
- Healthy Content Index

---

# Common Issues

- Database Dismounted
- Low Disk Space
- Failed Database Copy
- Large Copy Queue
- Large Replay Queue
- Failed Content Index
- Missing Backups

---

# Best Practices

- Keep databases mounted unless maintenance is required.
- Monitor database growth.
- Review white space regularly.
- Separate database and log files onto different volumes when appropriate.
- Verify successful backups.

---

# Interview Questions

1. What files make up an Exchange mailbox database?
2. What is white space?
3. Why are transaction logs important?
4. What is circular logging?
5. Which command checks database copy health?

---

# Production Notes

Before performing maintenance:

- Verify all database copies are healthy.
- Ensure recent backups are available.
- Confirm adequate free disk space.
- Check for database corruption alerts.

---

# Microsoft Learn

Recommended reading:

- Mailbox databases
- Database Availability Groups
- Exchange backup and recovery

---

# Summary

Database Inventory provides the operational information required to manage Exchange mailbox databases safely and efficiently.

Maintaining an accurate inventory improves troubleshooting, disaster recovery, capacity planning, and long-term administration.

---

# Next Document
**08-Certificate-Inventory.md**
