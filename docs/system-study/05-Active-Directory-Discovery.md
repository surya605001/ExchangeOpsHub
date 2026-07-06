# 05 - Active Directory Discovery

---

# Objective

Microsoft Exchange Server depends heavily on Active Directory (AD). Before administering or troubleshooting Exchange, administrators must understand the Active Directory environment.

This document explains how to discover and document the Active Directory infrastructure that supports Exchange.

---

# Scope

This guide covers:

- Forest Discovery
- Domain Discovery
- Domain Controllers
- Global Catalog Servers
- FSMO Roles
- Active Directory Sites
- DNS Configuration
- Replication Health
- Exchange Dependencies

---

# Theory

Exchange Server stores most of its configuration information in Active Directory.

Examples include:

- Mailboxes
- Distribution Groups
- Accepted Domains
- Email Address Policies
- Transport Configuration
- RBAC
- Database Information

If Active Directory is unhealthy, Exchange will also experience operational issues.

---

# Discovery Workflow

```text
Identify Forest
        │
        ▼
Identify Domains
        │
        ▼
Locate Domain Controllers
        │
        ▼
Locate Global Catalog Servers
        │
        ▼
Verify FSMO Roles
        │
        ▼
Check DNS
        │
        ▼
Validate Replication
        │
        ▼
Document Findings
```

---

# Step 1 – Discover the Forest

### PowerShell

```powershell
Get-ADForest
```

### Verify

- Forest Name
- Forest Mode
- Root Domain
- Global Catalog Servers
- Domains

---

# Step 2 – Discover Domains

```powershell
Get-ADDomain
```

Verify:

- Domain Name
- Domain Mode
- RID Master
- PDC Emulator
- Infrastructure Master

---

# Step 3 – Domain Controllers

```powershell
Get-ADDomainController -Filter *
```

Verify:

- Host Name
- Site
- IPv4 Address
- Operating System
- Global Catalog

---

# Step 4 – FSMO Roles

```powershell
netdom query fsmo
```

Verify:

- Schema Master
- Domain Naming Master
- PDC Emulator
- RID Master
- Infrastructure Master

---

# Step 5 – Active Directory Sites

```powershell
Get-ADReplicationSite
```

Verify:

- Site Names
- Site Links
- Exchange Server Location

---

# Step 6 – DNS

Verify:

- Internal DNS Servers
- Forward Lookup Zones
- Reverse Lookup Zones
- Autodiscover Records
- Exchange Host Records

---

# Step 7 – Replication Health

```powershell
repadmin /replsummary
```

Healthy Output:

- No replication failures
- No lingering objects
- No large replication delays

---

# Step 8 – Time Synchronization

```powershell
w32tm /query /status
```

Verify:

- Time Source
- Synchronization Status

Time synchronization is critical for Kerberos authentication.

---

# Exchange Dependencies on AD

Exchange requires:

- Active Directory
- DNS
- Global Catalog
- LDAP
- Kerberos
- Replication

If any of these fail, Exchange functionality can be affected.

---

# Health Checklist

- Forest Healthy
- Domain Healthy
- Domain Controllers Reachable
- Global Catalog Available
- Replication Healthy
- DNS Healthy
- Time Synchronized

---

# Common Issues

- Replication failures
- DNS misconfiguration
- FSMO role issues
- Global Catalog unavailable
- Time synchronization problems

---

# Best Practices

- Maintain healthy replication.
- Monitor Domain Controllers.
- Verify DNS before troubleshooting Exchange.
- Document FSMO role holders.
- Keep Active Directory updated and healthy.

---

# Interview Questions

1. Why does Exchange depend on Active Directory?
2. What is a Global Catalog Server?
3. What are FSMO Roles?
4. Why is DNS important for Exchange?
5. How do you verify AD replication?

---

# Production Notes

Always validate Active Directory health before investigating Exchange issues.

Many Exchange incidents originate from underlying Active Directory or DNS problems.

---

# Microsoft Learn

Recommended reading:

- Active Directory Domain Services overview
- Exchange Server architecture
- Exchange prerequisites

---

# Summary

Active Directory is the foundation of Microsoft Exchange Server.

A healthy Active Directory environment is essential for reliable Exchange operation, authentication, mail flow, and administrative tasks.

---

# Next Document

**06-Server-Inventory.md**
