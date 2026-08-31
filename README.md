# HkS Security, Governance & Compliance Framework (Assignment 1)

This repository contains the research, compliance framework design, and presentation deliverables for **Assignment 1 of the HkS Internship Programme (Security & AI Lab | August 2026)**.

---

## 📁 Repository Structure

```
hks_project/
├── reports/
│   ├── HKS_Final_Report_v2.md             # Consolidated final report (ISO 27001, SOC 2, 5 Controls, AI proposal)
│   └── HKS_Unified_Report_Assignment1.md  # Multi-intern unified research report
│
├── presentation/
│   ├── HKS_Assignment1_Presentation.pptx  # 26-slide presentation deck
│   └── HKS_Assignment1_Presentation.pdf   # Exported presentation PDF
│
└── references/
    ├── mentor_request.txt                 # Original assignment requirements and prompts
    ├── citations_ledger.json              # Primary source quotes and citation index
    └── standards/                         # Official ISO & AICPA standard texts and corpora
        ├── AICPA_SOC2_Description_Criteria_DC200.pdf
        ├── AICPA_SOC2_Guide_Oct2022_LATEST.pdf
        ├── AICPA_TSC_2017_with_Revised_PoFs_2022_CLEAN.pdf
        ├── ISO_IEC_27001-2022_redline.pdf
        ├── ISO_IEC_27002-2022_full.pdf
        └── text/                          # Plain-text extracts of standards
```

---

## 🎯 Key Content Summary

1. **Framework Comparison**: Detailed analysis of ISO/IEC 27001:2022 (ISMS clauses 4–10 & Annex A) vs. AICPA SOC 2 (Trust Services Criteria / Common Criteria CC1–CC9, Type 1 vs. Type 2).
2. **5 Engineered Security Controls**:
   - `HKS-AC-01`: Phishing-resistant identity & access lifecycle (FIDO2 MFA, SCIM, JIT)
   - `HKS-VM-03`: Vulnerability & configuration management (EPSS/KEV triage, CSPM)
   - `HKS-LM-04`: Centralized logging, monitoring & incident response (WORM logs, SIEM/SOAR)
   - `HKS-CM-02`: Secure change & CI/CD pipeline integrity (multi-party reviews, SLSA)
   - `HKS-BR-06`: Ransomware-resilient backup, recovery & data protection (isolated KMS, immutable storage)
3. **AI & Automation**: Proposed *Evidence Sufficiency Reviewer* for continuous compliance validation.
