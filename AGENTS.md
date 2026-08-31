# AGENTS.md — Global Context & Directives for AI Agents

Welcome to the **HkS Security, Governance & Compliance Framework** repository. This document serves as the single source of truth for all autonomous AI coding assistants, planners, and pair-programming agents (Antigravity, Claude Code, Cursor, Windsurf, Copilot, Codex, etc.).

---

## 1. Project Context & Mission

- **Organization**: HkS Internship Programme | Security & AI Lab (August 2026).
- **Core Objective**: Build a modern, automated, and reusable **Security, Governance & Compliance Framework** that unifies:
  1. **ISO/IEC 27001:2022** (ISMS certification against Clauses 4–10 & Annex A).
  2. **SOC 2 Type 1 & Type 2** (AICPA Trust Services Criteria attestation).
- **Guiding Architecture**: *"One control library, two assurance regimes, evidence by automation."*
- **Current Phase**: **Phase 2 — System Design & Architecture**.

---

## 2. Core Architectural Principles & Invariants

All agents generating code, schemas, or documentation must uphold these invariant principles:

1. **Collect-Once, Present-Many-Times**: Controls and evidence are defined once in a canonical schema, then mapped outward to multiple frameworks (ISO SoA, SOC 2 Section IV Matrix).
2. **Deterministic Checks Before AI Inference**:
   - Dates, hashes, period coverage, record counts, and population reconciliation must be evaluated by deterministic comparison code before calling any LLM.
   - *Rule*: Never spend model inference tokens on questions a deterministic boolean operator can answer.
3. **Asymmetric AI Authority (Core Safety Guardrail)**:
   - The AI *Evidence Sufficiency Reviewer* may flag gaps, identify anomalies, and enqueue tasks for human review (`INSUFFICIENT` / `UNCERTAIN`).
   - The AI **cannot** automatically approve evidence or grant compliance certification (`SUFFICIENT` verdicts only pass to human review queue without taking unilateral action).
4. **Evidence as Untrusted Input**: Logs, commit messages, and ticket bodies are treated as untrusted data; prompt injection defenses (delimiters, schema-constrained JSON outputs) are mandatory.
5. **Read-Only Collector Connectors**: Evidence collectors must strictly operate with read-only IAM/API permissions. The compliance pipeline must never become an unauthorized write path into production environments.

---

## 3. High-Accuracy Grounding & Verification Directives

- **Primary Sources First**: All clause numbers, control IDs, and criteria citations must be verified against official source documents in `docs/references/standards/`:
  - `ISO_IEC_27001-2022_redline.pdf` / `ISO_IEC_27002-2022_full.pdf`
  - `AICPA_SOC2_Description_Criteria_DC200.pdf` / `AICPA_TSC_2017_with_Revised_PoFs_2022_CLEAN.pdf` / `AICPA_SOC2_Guide_Oct2022_LATEST.pdf`
- **Zero Hallucination Rule**: If a standard requirement or technical mapping cannot be traced to primary sources or `docs/references/citations_ledger.json`, explicitly mark it as an assumption or pending verification rather than inventing facts.
- **The 5 Canonical Security Controls**:
  1. `HKS-AC-01`: Phishing-resistant identity & access lifecycle
  2. `HKS-CM-02`: Secure change & CI/CD pipeline integrity
  3. `HKS-VM-03`: Vulnerability & configuration management
  4. `HKS-LM-04`: Centralised logging, monitoring & incident response
  5. `HKS-BR-05`: Ransomware-resilient backup, recovery & data protection

---

## 4. Repository Map & Path Standards

```
hks_framework/
├── .github/
│   ├── CODEOWNERS                     # Code ownership (@marwanelamami)
│   ├── PULL_REQUEST_TEMPLATE.md       # PR structure & checklist
│   ├── workflows/pr-checks.yml        # CI lint, conflict, and secret checks
│   └── ISSUE_TEMPLATE/                # Feature and bug reporting templates
│
├── docs/
│   ├── reports/
│   │   ├── HKS_Final_Report_v2.md     # Consolidated final research report
│   │   └── HKS_Unified_Report_Assignment1.md # Unified multi-intern report
│   ├── presentation/
│   │   ├── HKS_Assignment1_Presentation.pptx # Presentation deck
│   │   └── HKS_Assignment1_Presentation.pdf  # Presentation PDF
│   └── references/
│       ├── mentor_request.txt         # Mentor requirements
│       ├── citations_ledger.json      # Quotations and primary source ledger
│       └── standards/                 # Official standards PDFs and extracted text
│
├── AGENTS.md                          # Universal AI agent instructions (this file)
├── CLAUDE.md                          # Claude Code adapter pointing to AGENTS.md
├── CONTRIBUTING.md                    # Contributor workflow & branch governance
├── SECURITY.md                        # Security & vulnerability reporting policy
└── README.md                          # Public project overview & status
```

---

## 5. Team Roles & Domain Ownership

When assisting with specific tasks, align changes with the appropriate domain workstream:

- **Marwan Elamami** *(Lead, AI & Automation)*:
  - AI Evidence Sufficiency Reviewer (prompts, retrieval grounding, evaluation sets, JSON schemas).
  - CI/CD orchestrators, automation pipelines, and core system interfaces.
- **Ahmed Arebi** *(Security & Infrastructure Engineering)*:
  - Telemetry connectors (CloudTrail, IdP/SCIM, GitHub API, SIEM).
  - Cryptography, KMS architectures, and tamper-evident storage (S3 Object Lock / WORM).
- **Abo Alqasem Elkorbow** *(GRC & Governance)*:
  - Control Schema definitions, Statement of Applicability (SoA) generation, and SOC 2 Crosswalk logic.
  - Risk assessment models and disaster recovery / backup verification procedures.

---

## 6. Code & Engineering Standards

- **Language & Runtime**: Python 3.11+ for automation scripts, YAML/JSON for schemas and configurations.
- **Data Models**: Use `pydantic` or strict dataclasses for all schemas and data validation.
- **Type Safety**: Full type annotations (`typing`) on all Python functions and classes.
- **Error Handling**: Defensive programming; log structured errors; do not silently swallow exceptions.
- **Secret Zero**: Never hardcode API keys, tokens, or credentials. Use environment variables or short-lived federated credentials (OIDC).

---

## 7. Git & Collaboration Protocol

- **Direct Push Prohibited**: Never commit directly to `main`. Always create a descriptive branch:
  - `feat/<feature-name>`
  - `docs/<doc-name>`
  - `fix/<fix-name>`
- **Pull Request Review**: All PRs must target `main` and require code owner review from `@marwanelamami`.
- **Commit Messages**: Follow conventional commit formats (e.g. `feat: ...`, `docs: ...`, `fix: ...`, `refactor: ...`).
- **Formatting**: Preserve clean Markdown formatting with no extraneous emojis in technical documentation.

---

## 8. Quick Verification Commands

- Check Git status: `git status`
- Test CI conflict marker check:
  ```bash
  grep -rnE '^[<]{7} |^[=]{7}$|^[>]{7} ' . --exclude-dir=".git" --exclude-dir=".github"
  ```
- Scan for credential leaks:
  ```bash
  grep -rnE 'BEGIN (RSA|EC|DSA|OPENSSH) PRIVATE KEY|AKIA[0-9A-Z]{16}' . --exclude-dir=".git" --exclude-dir=".github"
  ```
