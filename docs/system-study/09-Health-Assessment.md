# 09 - Exchange Health Assessment

---

# Objective

The purpose of an Exchange Health Assessment is to determine the operational health of the Microsoft Exchange environment before maintenance, migrations, upgrades, troubleshooting, or production changes.

A Health Assessment provides a baseline of the Exchange organization and identifies configuration issues, operational risks, performance concerns, and recommended corrective actions.

---

# Scope

This document covers:

- Exchange Server Health
- Windows Server Health
- Exchange Services
- Mailbox Database Health
- Database Availability Group (DAG) Health
- Mail Flow Health
- Queue Health
- Certificate Health
- Disk Health
- Event Logs
- Performance
- Backup Validation

---

# Why Perform a Health Assessment?

A Health Assessment should always be performed:

- Before applying a Cumulative Update (CU)
- Before Security Updates (SU)
- Before Exchange migrations
- During customer onboarding
- During Knowledge Transfer (KT)
- During quarterly maintenance
- Before Disaster Recovery testing
- After resolving major incidents

---

# Health Assessment Workflow

```text
Exchange Server
        │
        ▼
Windows Health
        │
        ▼
Exchange Services
        │
        ▼
Database Health
        │
        ▼
DAG Health
        │
        ▼
Mail Flow
        │
        ▼
Certificates
        │
        ▼
Disk Space
        │
        ▼
Backup Verification
        │
        ▼
Final Report
```

---

# Step 1 – Verify Exchange Servers

### PowerShell

```powershell
Get-ExchangeServer
```

Verify:

- Server Name
- Exchange Version
- CU Level
- Build Number

---

# Step 2 – Exchange Services

```powershell
Get-Service *Exchange*
```

Healthy State:

All required Exchange services are running.

---

# Step 3 – Mailbox Databases

```powershell
Get-MailboxDatabase -Status
```

Verify:

- Mounted
- Database Size
- White Space
- Backup Status

---

# Step 4 – Database Copies

```powershell
Get-MailboxDatabaseCopyStatus *
```

Healthy State:

- Mounted
- Healthy
- Content Index Healthy

---

# Step 5 – Queue Health

```powershell
Get-Queue
```

Healthy State:

Queues should remain low during normal operations.

Large queue growth may indicate:

- SMTP issues
- DNS problems
- Remote server unavailable

---

# Step 6 – Mail Flow

```powershell
Test-Mailflow
```

Healthy State:

Test succeeds without delay.

---

# Step 7 – Certificate Health

```powershell
Get-ExchangeCertificate
```

Verify:

- Valid
- Not Expired
- Correct Services Assigned

---

# Step 8 – Disk Health

```powershell
Get-Volume
```

Verify:

- Free Space
- Health Status
- Drive Capacity

---

# Step 9 – Event Logs

Review:

- Application Log
- System Log

Focus on:

- MSExchangeIS
- MSExchangeTransport
- Active Directory
- IIS
- Failover Clustering

---

# Step 10 – Performance

Review:

- CPU Usage
- Memory Usage
- Disk Latency
- Network Utilization

---

# Health Checklist

| Component | Status |
|-----------|--------|
| Exchange Servers | ☐ |
| Exchange Services | ☐ |
| Mailbox Databases | ☐ |
| DAG | ☐ |
| Mail Flow | ☐ |
| Queues | ☐ |
| Certificates | ☐ |
| Disk Space | ☐ |
| Event Logs | ☐ |
| Backup | ☐ |

---

# Common Issues

- Stopped Exchange Services
- Database Dismounted
- Failed Database Copy
- Large Mail Queues
- Expired Certificates
- Low Disk Space
- Event Log Errors
- Failed Backups

---

# Recommended Actions

If issues are identified:

1. Record the finding.
2. Assess the business impact.
3. Determine the root cause.
4. Plan corrective action.
5. Validate after implementation.
6. Update documentation.

---

# Production Best Practices

- Perform health checks regularly.
- Review monitoring alerts daily.
- Test mail flow after maintenance.
- Monitor certificate expiry.
- Verify backups.
- Keep Exchange updated with supported CUs and SUs.

---

# Interview Questions

1. What checks are included in an Exchange Health Assessment?
2. How do you verify mail flow?
3. Which command checks Exchange queues?
4. Why is database health important?
5. How do you verify Exchange services?

---

# Production Notes

A Health Assessment should be documented and retained as a baseline. Comparing current results with previous assessments helps identify trends, capacity issues, and configuration drift.

---

# Summary

An Exchange Health Assessment provides a structured view of the operational state of the environment. Regular assessments reduce operational risk and support proactive maintenance.

---

# Next Document

**10-System-Study-Report.md**
