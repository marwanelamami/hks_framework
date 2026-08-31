# CLAUDE.md — Claude Code Instructions

> **Global Reference**: This repository uses [`AGENTS.md`](./AGENTS.md) as the unified single source of truth for all AI agent directives, architectural invariants, and high-accuracy standards. **Read and follow `AGENTS.md` before performing any tasks.**

---

## Quick Reference

### Project Summary
- **Project**: HkS Security, Governance & Compliance Framework (ISO 27001 & SOC 2).
- **Core Strategy**: "One control library, two assurance regimes, evidence by automation."
- **Current Milestone**: Phase 2 (Systems Design & Architecture).

### Key Rules
1. **Zero Hallucinations**: Ground all standard mappings in official texts in `docs/references/standards/`.
2. **Branching**: Do not push directly to `main`. Create feature branches (`feat/`, `docs/`, `fix/`) and target `main` via PR.
3. **Approvals**: Merges require code owner review from `@marwanelamami`.
4. **Clean Docs**: Maintain clean GitHub-flavored markdown without unnecessary emojis in technical documentation.

---

### Verification Commands
```bash
# Verify no Git conflict markers exist
grep -rnE '^[<]{7} |^[=]{7}$|^[>]{7} ' . --exclude-dir=".git" --exclude-dir=".github"

# Verify no exposed credentials or private keys
grep -rnE 'BEGIN (RSA|EC|DSA|OPENSSH) PRIVATE KEY|AKIA[0-9A-Z]{16}' . --exclude-dir=".git" --exclude-dir=".github"
```
