# Cybersecurity Templates & Documents – Descriptions, Key Points & Examples

## 1) Information Security

### 1.1 Data Breach Notification Log

**Purpose:** Track notifications sent to authorities, customers, and partners after a confirmed data breach.  
**Why it matters:** Many regulations (e.g., 72‑hour notification windows) require audit‑ready evidence.  
**Use when:** A breach is confirmed or likely and triggers legal/contractual notifications.

**Example snippet**

```markdown
# Data Breach Notification Log
- Incident ID: IR-2026-0041
- Discovery Date/Time: 2026‑02‑15 09:40 NPT
- Data Types: PII (email, phone), internal docs
- Jurisdictions: NP, EU
- Regulator Notification: NITC (2026‑02‑16 11:10), DPA (2026‑02‑16 12:05)
- Affected Individuals Notified: Email campaign #241 (2026‑02‑16 14:00)
- Evidence Links: SIEM-Event-48321, Ticket-12345
```

***

### 1.2 DLP Incident Log

**Purpose:** Record Data Loss Prevention (DLP) detections and actions.  
**Why:** Shows control effectiveness; supports tuning of detection rules.  
**Use when:** DLP tool flags exfiltration attempts or policy violations.

**Example snippet**

```markdown
# DLP Incident Log
|     ID   |    Date    |Channel|    Rule    | Severity |   Action    |  Owner  |
|----------|------------|-------|------------|----------|-------------|---------|
| DLP-2201 | 2026-02-10 | Email | PII-Export |   High   | Quarantined | dlp@sec |
```

***

### 1.3 Document Retention & Disposal Tracker

**Purpose:** Track how long records are retained and how/when they are securely destroyed.  
**Why:** Minimizes data exposure and meets legal retention requirements.

**Example snippet**

```markdown
# Document Retention & Disposal Tracker
| Record Type | Owner | Retention | Storage | Disposal Method | Next Review |
|-------------|-------|-----------|---------|-----------------|------------|
| Access Logs | SecOps | 1 year | SIEM | Secure wipe | 2026-12-31 |
```

***

### 1.4 Encryption Key Management Sheet

**Purpose:** Lifecycle tracking for encryption keys (creation, rotation, revocation).  
**Why:** Keys are crown jewels—mismanagement equals data exposure.

**Example snippet**

```markdown
# Encryption Key Management
| Key ID | Scope | Alg/Len | Custodian | Created | Rotation | State |
|--------|-------|---------|-----------|---------|----------|-------|
| kms-app-01 | DB-Prod | AES-256-GCM | SecOps | 2025-11-01 | 90 days | Active |
```

***

## 2) Network Security

### 2.1 DDoS Attack Mitigation Plan Tracker

**Purpose:** Plan, test, and track readiness for DDoS events.  
**Why:** Availability is a top risk; readiness reduces MTTR.

**Example snippet**

```markdown
# DDoS Mitigation Plan Tracker
- Provider: Upstream ISP + WAF/CDN
- Rate‑limit Profiles: /api v1 = 200 rps per IP
- Playbook: NOC‑DDOS‑01
- Test Date: 2026‑01‑20 (Passed) | Next: 2026‑04‑20
```

***

### 2.2 Network Security Risk Mitigation Report

**Purpose:** Summarize risks (e.g., exposed services, weak crypto) and mitigation status.  
**Why:** Communicates risk posture to leadership.

**Example snippet**

```markdown
# Network Risk Mitigation Report (Q1 2026)
- Risk: Legacy TLS on vpn.company.tld → **Mitigation:** Enforce TLS 1.2+, due 2026‑03‑01
- Risk: Flat VLAN for printers → **Mitigation:** Segmentation, due 2026‑02‑28
```

***

### 2.3 Patch Management Schedule for Network Devices

**Purpose:** Routine schedule for firmware/OS updates on routers, switches, firewalls.  
**Why:** Many breaches exploit unpatched network gear.

**Example snippet**

```markdown
# Network Patch Schedule
| Device | Version | Latest | Window | Rollback |
|--------|---------|--------|--------|----------|
| FW-01 | v12.3.1 | 12.4.0 | Sun 02:00–03:00 | Snapshot+Config backup |
```

***

### 2.4 Security Event Correlation Tracker

**Purpose:** Track SIEM correlation rules, alerts, and tuning actions.  
**Why:** Reduces noise, improves detection quality.

**Example snippet**

```markdown
# Correlation Tracker
| Rule | Objective | FNs/Fps | Tuning | Owner |
|------|-----------|---------|--------|-------|
| BruteForce-AD | Detect password spray | FPs: 3/week | Threshold + geo filter | SOC |
```

***

## 3) Cloud Security

### 3.1 Cloud Access Control Matrix

**Purpose:** Map roles to permissions across cloud services.  
**Why:** Prevents privilege sprawl and supports least‑privilege reviews.

**Example snippet**

```markdown
# Cloud Access Control Matrix (Azure)
| Role | Scope | Permissions | Notes |
|------|-------|-------------|-------|
| AppOps | Sub:Prod | VM Read, Start/Stop | No Delete |
```

***

### 3.2 Cloud Backup & Recovery Testing Tracker

**Purpose:** Track backups and verify that restores actually work.  
**Why:** Backups are only useful if tested.

**Example snippet**

```markdown
# Cloud Backup & Recovery Testing
| Asset | Backup Policy | Last Restore Test | RTO | RPO | Result |
|------|----------------|-------------------|-----|-----|--------|
| SQL-Prod | Daily full, 15-min logs | 2026-02-01 | 60m | 15m | Pass |
```

***

### 3.3 Cloud Incident Response Log

**Purpose:** Record full timeline and evidence for cloud incidents.  
**Why:** Traceability for forensics and audits.

**Example snippet**

```markdown
# Cloud IR Log
- Provider: AWS
- Impacted: S3 bucket (logs-prod)
- Detection: GuardDuty finding #GD-8821
- Containment: Blocked public ACLs, SCP update
- Evidence: CloudTrail export s3://forensics/IR-2026-09
```

***

### 3.4 Cloud Security Configuration Baseline

**Purpose:** Baseline controls (e.g., MFA, logging, encryption) per account/subscription.  
**Why:** Ensures minimum standards for all cloud environments.

**Example snippet**

```markdown
# Cloud Config Baseline (GCP)
- Org Policies: Restrict VM external IPs ✅
- Logging: Admin Activity logs retained 2 years ✅
- Encryption: CMEK for BigQuery required ✅
```

***

## 4) Application Security

### 4.1 Application Data Encryption Checklist

**Purpose:** Verify encryption in transit/at rest and key handling in apps.  
**Why:** Prevents data exposure and compliance violations.

**Example snippet**

```markdown
# App Data Encryption Checklist
- TLS 1.2+ enforced ✅
- HSTS preloaded ⬜
- Secrets via KMS/Vault (no env plaintext) ✅
- PII fields encrypted at rest ✅
```

***

### 4.2 Patch & Update Tracker

**Purpose:** Track app/library dependencies and patch SLAs.  
**Why:** Third‑party vulnerabilities are a common entry point.

**Example snippet**

```markdown
# Patch & Update Tracker
| Service | Dependency | Current | Latest | Risk | ETA |
|---------|------------|--------|--------|------|-----|
| web-api | OpenSSL | 1.1.1u | 3.0.13 | High | 2026‑02‑25 |
```

***

### 4.3 Secure Mobile App Testing Tracker

**Purpose:** Plan and record mobile security testing (OWASP MASVS/L2).  
**Why:** Mobile leaves unique footprints (storage, inter‑app comms).

**Example snippet**

```markdown
# Mobile App Testing Tracker
- Platform: Android
- Tests: Root detection, TLS pinning, Secure storage (Keystore)
- Findings: MASVS-STORAGE-1 (cached tokens) → Fixed in 2.4.1
```

***

### 4.4 Static Code Analysis Log

**Purpose:** Capture SAST runs, findings, trends, and remediation.  
**Why:** Shift‑left security & measurable MTTR.

**Example snippet**

```markdown
# SAST Log
| Repo | Tool | Run | Findings (H/M/L) | MTTR | Notes |
|------|------|-----|------------------|------|-------|
| svc-auth | Semgrep | 2026‑02‑12 | 2/4/9 | 6d | Added JWT rulepack |
```

***

## 5) Security Management

### 5.1 Information Transfer Policy

**Purpose:** Govern secure transfer of information inside/outside the company.  
**Why:** Reduces leakage via email, chat, removable media.

**Example snippet**

```markdown
# Information Transfer Policy (Excerpt)
- Use company‑approved channels (M365, SFTP).
- Prohibit personal email for business data.
- Encrypt external transfers with org‑approved tools.
```

***

### 5.2 Information Classification Policy

**Purpose:** Define data classes (Public, Internal, Confidential, Restricted) and handling rules.  
**Why:** Right controls for the right sensitivity.

**Example snippet**

```markdown
# Data Classification (Summary)
- Restricted: PII/PHI/PCI → Encrypt at rest & transit; least privilege; DLP mandatory.
- Internal: Business docs → Approved sharing domains only.
```

***

### 5.3 Disposal and Destruction Policy

**Purpose:** Secure data destruction methods and evidence capture.  
**Why:** Prevents recovery of retired media.

**Example snippet**

```markdown
# Disposal/Destruction
- Media: SSDs – Cryptographic erase + shred certificate
- Paper: Cross‑cut shredding + vendor CoD stored 7 years
```

***

### 5.4 Backup and Recovery

**Purpose:** Define backups, retention, offsite/immutability, and restore drills.  
**Why:** Core to resilience and ransomware readiness.

**Example snippet**

```markdown
# Backup & Recovery
- 3‑2‑1 rule (3 copies, 2 media, 1 offsite/immutable)
- Quarterly restore tests; target RTO=60m, RPO=15m
```

***

## 6) Incident Management

### 6.1 Major Incident Report Template

**Purpose:** Standardized post‑incident report (PIR) for critical events.  
**Why:** Drives accountability and learning.

**Example snippet**

```markdown
# Major Incident Report
- Severity: SEV‑1 | Duration: 48m | Impact: Payment failures (15% users)
- Root Cause: Misconfigured WAF rule
- Corrective Actions: Rule tests in staging + canary; runbook update
```

***

### 6.2 Internal Incident Report

**Purpose:** Record lower‑severity internal incidents (near misses, access issues).  
**Why:** Early signals prevent bigger events.

**Example snippet**

```markdown
# Internal Incident Report
- Summary: Unauthorized shared link created externally
- Containment: Link revoked; owner coached; DLP rule adjusted
```

***

### 6.3 Structure Damage Incident Report

**Purpose:** Capture physical facility damage impacting security/operations.  
**Why:** Physical issues often trigger cyber‑impacts (power, links, DR).

**Example snippet**

```markdown
# Structure Damage Report
- Event: Water leak in server room 2F
- Impact: Two ToR switches offline
- Recovery: Failover to DC‑B within 12 minutes
```

***

### 6.4 Incident Management Process

**Purpose:** End‑to‑end workflow from detection to lessons learned.  
**Why:** Consistency, speed, auditability.

**Example snippet**

```markdown
# Incident Management Process (High-level)
1. Detect → 2. Triage → 3. Contain → 4. Eradicate → 5. Recover → 6. Review
- RACI: SOC (Lead), IT (Containment), AppOps (Fix), Comms (Stakeholders)
- SLAs: SEV‑1 engage ≤ 15m; status updates every 30m
```

***

## Repo Enhancements (Optional but Recommended)

*   **Labels & Issue Templates**:  
    Create `.github/ISSUE_TEMPLATE/incident.yml` to standardize incident logging.
*   **PR Template**:  
    `.github/pull_request_template.md` to capture security impact and test notes.
*   **Compliance Tags**:  
    At the top of each file, add `Compliance:` lines (e.g., `ISO 27001 A.12.3`, `NIST CSF PR.IP-4`).
*   **CHANGELOG.md**:  
    Summarize security template updates per release.

**Example PR template**

```markdown
## Summary
What changed and why?

## Security Impact
- [ ] No impact
- [ ] Policy/Control tightened
- [ ] Process change (details below)

## Testing / Validation
- Links to runs, screenshots, or checklists

## Checklist
- [ ] Updated README/Docs
- [ ] Mapped compliance tags
```

***
