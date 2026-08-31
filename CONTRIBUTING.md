# Contributing Guidelines

Thank you for collaborating on the **HkS Security, Governance & Compliance Framework**.

To ensure quality, compliance integrity, and consistency, all contributors must adhere to the workflow rules defined below.

---

## 1. Branching & Merge Governance

- **Main Branch Lock**: Direct commits and direct pushes to `main` are strictly prohibited.
- **Merge Authority**: Merging into `main` is restricted exclusively to `@marwanelamami`.
- **Branch Naming**:
  - `docs/brief-description`: For report, reference, or presentation updates.
  - `feat/brief-description`: For new controls, scripts, or framework sections.
  - `fix/brief-description`: For correcting citations, formatting, or broken links.

---

## 2. Contribution Workflow

1. **Pull Latest Changes**:
   ```bash
   git checkout main
   git pull origin main
   ```
2. **Create a Dedicated Branch**:
   ```bash
   git checkout -b docs/update-section-7
   ```
3. **Commit with Clear Messages**:
   ```bash
   git commit -m "docs: Refine control implementation details for HKS-CM-02"
   ```
4. **Push Branch & Open a Pull Request**:
   ```bash
   git push -u origin docs/update-section-7
   ```
5. **Request Review**:
   - Open a Pull Request targeting `main`.
   - Complete the Pull Request template checklist.
   - Tag `@marwanelamami` for review and approval.

---

## 3. Review Criteria

Before merging, all contributions will be verified for:
1. **Source Verifiability**: All claims, control IDs, and standard clauses must reference authoritative standards (ISO/IEC 27001:2022, SOC 2 TSC).
2. **Confidentiality & Privacy**: No credentials, private tokens, internal keys, or unauthorized personal data.
3. **Automated Status Checks**: All CI verification jobs in `.github/workflows/` must pass cleanly.
