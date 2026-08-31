# HkS Security, Governance & Compliance Framework

An engineering-led compliance framework unifying **ISO/IEC 27001:2022** and **SOC 2 Type 1 & Type 2** through automated evidence collection, deterministic assertions, and AI-assisted sufficiency reviews.

Developed within the **HkS Internship Programme | Security & AI Lab (August 2026)**.

---

## Current Status & Roadmap

| Phase | Description | Status |
|---|---|---|
| **Phase 1: Research & Unified Synthesis** | Comparative analysis of ISO 27001 vs. SOC 2, ISMS architecture, engineering 5 core security controls, and AI proposal. | Completed |
| **Phase 2: System Design & Architecture** | Canonical Control Schema, evidence connector interfaces, deterministic assertion engine, and AI Evidence Sufficiency Reviewer design. | Active |
| **Phase 3: Prototype & Verification** | End-to-end implementation of reference controls with mock evidence and automated sufficiency evaluation. | Planned |

---

## Core Engineering Principles

1. **One Control Library, Two Assurance Regimes**: Define controls once in a canonical schema, generating both the ISO Statement of Applicability (SoA) and the SOC 2 Section IV Matrix from the same data.
2. **Evidence by Automation**: Replace manual point-in-time screenshots with continuous, read-only telemetry collectors and tamper-evident manifests.
3. **Deterministic Checks Before AI Inference**: Validate dates, hashes, and population completeness using boolean assertions before model evaluation.
4. **Asymmetric AI Authority**: The AI Evidence Sufficiency Reviewer flags defects and enqueues human review tasks, but cannot unilaterally grant compliance.

---

## The 5 Canonical Security Controls

1. `HKS-AC-01`: Phishing-resistant identity & access lifecycle (FIDO2 MFA, SCIM, JIT)
2. `HKS-CM-02`: Secure change & CI/CD pipeline integrity (multi-party reviews, SLSA)
3. `HKS-VM-03`: Vulnerability & configuration management (EPSS/KEV triage, CSPM)
4. `HKS-LM-04`: Centralised logging, monitoring & incident response (WORM logs, SIEM/SOAR)
5. `HKS-BR-05`: Ransomware-resilient backup, recovery & data protection (isolated KMS, immutable storage)

---

## Repository Structure

```
hks_framework/
├── .github/
│   ├── CODEOWNERS                     # Global code ownership (@marwanelamami)
│   ├── PULL_REQUEST_TEMPLATE.md       # PR structure and compliance checklist
│   ├── workflows/pr-checks.yml        # CI lint, conflict marker, and secret scanner
│   └── ISSUE_TEMPLATE/                # Bug and proposal templates
│
├── docs/
│   ├── reports/
│   │   ├── HKS_Final_Report_v2.md     # Consolidated final research report
│   │   └── HKS_Unified_Report_Assignment1.md # Multi-intern unified report
│   │
│   ├── presentation/
│   │   ├── HKS_Assignment1_Presentation.pptx # Slide presentation deck
│   │   └── HKS_Assignment1_Presentation.pdf  # Slide presentation PDF
│   │
│   └── references/
│       ├── mentor_request.txt         # Mentor requirements and prompt
│       ├── citations_ledger.json      # Primary source quotation and citation ledger
│       └── standards/                 # Official standard texts (ISO 27001/2, SOC 2)
│
├── AGENTS.md                          # Global context and directives for AI agents
├── CLAUDE.md                          # Claude Code adapter pointing to AGENTS.md
├── CONTRIBUTING.md                    # Collaboration rules, branching, and PR workflow
├── SECURITY.md                        # Security policy and disclosure process
└── README.md                          # Project overview and roadmap
```

---

## Team & Workstreams (Phase 2)

- **Marwan Elamami** (AI & Automation Lead): AI Reviewer architecture, CI/CD orchestration, prompt guardrails, and synthetic evaluation benchmarks.
- **Ahmed Arebi** (Security Engineering & Infrastructure): Telemetry collector connectors, cryptography, KMS hierarchy, and WORM storage design.
- **Abo Alqasem Elkorbow** (GRC & Governance): Canonical Control Schema, ISO/SOC 2 crosswalks, Statement of Applicability compiler, and disaster recovery specs.

---

## AI Agent Integration

All AI assistants (Antigravity, Claude Code, Cursor, Copilot, etc.) must refer to [AGENTS.md](./AGENTS.md) for architectural invariants, grounding rules, and coding standards.
