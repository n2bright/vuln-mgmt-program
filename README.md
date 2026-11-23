# Vulnerability management program

> A working vulnerability management program built on Tenable in a live, internet-exposed Azure environment, run the way a FedRAMP or SOC 2 auditor would expect to see it.

**Status:** 🚧 In progress

## What it does
Takes a vulnerability management program from policy to evidence:

1. **Policy.** A vulnerability management policy with scope, roles, scan frequency and remediation SLAs by severity.
2. **Scan.** Authenticated and unauthenticated Tenable scans of Windows and Linux VMs, giving a baseline.
3. **Remediate.** Scripted remediation (PowerShell / Bash) for the top findings, then a rescan to prove the fix.
4. **Track.** Open findings go into a POA&M with owner, severity, due date and status.
5. **Report.** Before/after metrics and a short summary written for a non-technical stakeholder.

## Frameworks and controls

| Control | What it covers | Evidence in this repo |
|---|---|---|
| NIST 800-53 RA-5 | Vulnerability monitoring and scanning | Scan configuration, baseline and rescan exports |
| NIST 800-53 SI-2 | Flaw remediation | Remediation scripts, before/after comparison |
| NIST 800-53 CM-6 | Configuration settings | Hardening changes applied by the scripts |
| NIST 800-53 CA-5 | Plan of action and milestones | `poam/` export |
| FedRAMP ConMon | Monthly scanning and remediation timelines | SLA table in the policy |

## Stack
Tenable Vulnerability Management, Microsoft Azure, PowerShell, Bash, Python (POA&M generation)

## Repository layout (planned)
```
policy/        vulnerability management policy and SLA table
scans/         sanitized scan exports (baseline and rescan)
remediation/   remediation scripts with notes on each finding
poam/          POA&M generator and output
report/        stakeholder summary and metrics
```

## Design decisions
See [DECISIONS.md](DECISIONS.md).

## What I'd change in production
_Coming soon._

---
Scans run against my own lab VMs in a training environment. Exports are sanitized; nothing here comes from any employer or client environment.
