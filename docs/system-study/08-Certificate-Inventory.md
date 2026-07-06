# 08 - Certificate Inventory

---

# Objective

The purpose of Certificate Inventory is to identify, document, and validate all SSL/TLS certificates used by Microsoft Exchange Server.

Certificates are critical for securing client communications, mail flow, and Exchange services such as Outlook on the Web (OWA), Exchange Admin Center (EAC), Outlook Anywhere, Autodiscover, Exchange Web Services (EWS), MAPI over HTTP, ActiveSync, SMTP TLS, POP3, and IMAP.

A well-maintained certificate inventory helps prevent service interruptions caused by expired, invalid, or misconfigured certificates.

---

# Scope

This guide covers:

- Exchange Certificates
- Certificate Services
- Certificate Thumbprints
- Subject and SAN Entries
- Expiry Dates
- Certificate Assignment
- Certificate Health
- Renewal Planning

---

# Theory

Exchange Server uses X.509 certificates to encrypt communication between clients and Exchange services.

Certificates may be:

- Self-Signed
- Public CA Signed
- Internal Enterprise CA Signed

The certificate assigned to Exchange services should match the DNS names used by clients.

---

# Certificate Discovery Workflow

```text
Identify Certificates
        │
        ▼
Review Subject Names
        │
        ▼
Verify SAN Entries
        │
        ▼
Check Expiry Dates
        │
        ▼
Review Assigned Services
        │
        ▼
Verify Certificate Status
        │
        ▼
Document Findings
```

---

# Step 1 – List Exchange Certificates

### PowerShell

```powershell
Get-ExchangeCertificate
```

### Purpose

Displays all certificates installed on the Exchange server.

---

# Step 2 – View Certificate Details

### PowerShell

```powershell
Get-ExchangeCertificate | Format-List
```

### Verify

- Thumbprint
- Subject
- Issuer
- NotBefore
- NotAfter
- Services
- Status

---

# Step 3 – View Certificate Services

### PowerShell

```powershell
Get-ExchangeCertificate | Select Thumbprint,Services,Subject,NotAfter
```

### Sample Output

```text
Thumbprint   : ABC123456789...
Services     : IIS, SMTP
Subject      : CN=mail.contoso.com
NotAfter     : 15-Nov-2027
```

---

# Explanation

| Field | Description |
|-------|-------------|
| Thumbprint | Unique certificate identifier |
| Services | Exchange services using the certificate |
| Subject | Common Name (CN) |
| NotAfter | Expiration date |

---

# Exchange Services That Use Certificates

Certificates may be assigned to:

- IIS
- SMTP
- POP
- IMAP

Verify that required services are correctly assigned.

---

# Step 4 – Verify Certificate Assignment

### PowerShell

```powershell
Get-ExchangeCertificate | Select FriendlyName,Services
```

Ensure production certificates are assigned to the required Exchange services.

---

# Step 5 – Review Certificate Expiry

### PowerShell

```powershell
Get-ExchangeCertificate | Sort NotAfter
```

Review certificates approaching expiration.

---

# Sample Inventory Table

| Item | Value |
|------|-------|
| Friendly Name | Exchange Production Certificate |
| Subject | mail.contoso.com |
| Issuer | DigiCert |
| Expiry Date | 15-Nov-2027 |
| Services | IIS, SMTP |
| Status | Valid |

---

# Health Checklist

- Certificate Valid
- Correct Subject Name
- SAN Entries Correct
- Correct Services Assigned
- Expiry Date Monitored
- Trusted Certificate Chain

---

# Common Issues

- Expired Certificate
- Incorrect Subject Name
- Missing SAN Entry
- Certificate Not Assigned to IIS
- SMTP TLS Certificate Issues
- Untrusted Certificate

---

# Troubleshooting

Symptoms of certificate issues may include:

- Outlook security warnings
- OWA certificate errors
- EAC inaccessible
- Autodiscover failures
- SMTP TLS failures
- Hybrid connectivity issues

Always verify certificate assignment before replacing or renewing certificates.

---

# Best Practices

- Monitor certificate expiry regularly.
- Renew certificates before expiration.
- Document all certificate details.
- Verify SAN entries match client URLs.
- Test services after certificate replacement.

---

# Interview Questions

1. Which Exchange services use certificates?
2. What is the difference between a Subject Name and a SAN?
3. How do you view Exchange certificates?
4. How do you assign a certificate to IIS?
5. What happens if an Exchange certificate expires?

---

# Production Notes

Before renewing a certificate:

- Export the existing certificate (including the private key if appropriate).
- Record the thumbprint.
- Verify all Exchange URLs.
- Plan a maintenance window if required.
- Validate client connectivity after renewal.

---

# Microsoft Learn

Recommended reading:

- Exchange certificates
- Configure certificates in Exchange Server
- Certificate requirements for Exchange

---

# Summary

Certificate Inventory ensures that Exchange services remain secure and accessible.

Maintaining accurate certificate documentation reduces operational risk and helps prevent outages caused by expired or incorrectly configured certificates.

---

# Next Document

**09-Health-Assessment.md**
