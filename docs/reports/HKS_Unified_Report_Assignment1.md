# HkS Security, Governance & Compliance Framework
## Assignment 1 — Unified Report: ISO 27001 & SOC 2

**Prepared jointly by:** Ahmed Arebi · Abo Alqasem Elkorbow · Marwan Elamami (AI & Automation Intern)
**HkS Internship Programme | Security & AI Lab | August 2026**

> **About this document.** Each intern researched Assignment 1 independently and produced an individual report (Arebi, 58 pp.; Elkorbow, 12 pp.; Elamami, ~20 pp.). This unified version merges the three. Sections covering established facts (definitions, standards structure, criteria) are stated once because all three reports verified them against the same primary sources: the official texts supplied in the programme workspace — ISO/IEC 27001:2022, ISO/IEC 27002:2022, AICPA TSP section 100 (2017 Trust Services Criteria with Revised Points of Focus 2022), and DC section 200. Where the individual reports differed — control selection, emphasis, claims resting on secondary sources — the difference is resolved explicitly and the reasoning given, per the programme's instruction that claims be verifiable and disagreements argued rather than assumed.

---

## 0. Method and AI-use statement

All three reports followed the same discipline independently:

- **Primary sources first.** Clause numbers, control identifiers and criterion wording were read from the standards texts provided in the resource pack, not recalled from blogs or model output.
- **Secondary sources only for what the standards don't cover** (threat statistics, certification mechanics, timelines), attributed inline.
- **AI tooling used for acceleration** — research triage, structuring, drafting. Every load-bearing claim was checked against source text. Claims that could not be traced to a primary or reputable secondary source are marked as such rather than silently kept.

One claim was challenged and corrected during research, and it shaped this report: the common framing "ISO 27001 is risk-based, SOC 2 is checklist-based" is wrong. SOC 2's CC3 series requires formal risk assessment (on COSO principles), so both regimes are risk-based. They differ in what they demand evidence *of*, not in whether risk drives them.

---

## 1. What is ISO/IEC 27001?

ISO/IEC 27001:2022 — *Information security, cybersecurity and privacy protection — Information security management systems — Requirements* — is an international standard that "specifies the requirements for establishing, implementing, maintaining and continually improving an information security management system within the context of the organization," including requirements for assessing and treating information security risks. It is published jointly by ISO and IEC under committee JTC 1/SC 27 and is the standard in the 27000 family against which an organisation can be certified by an accredited third party.

**Requirements versus controls — the critical structural point.** Newcomers equate ISO 27001 with its control catalogue; auditors test something else:

| Part | Status | Meaning |
|---|---|---|
| Clauses 0–3 | Informative | Scope, references, terms. Not auditable. |
| Clauses 4–10 | Mandatory | The "shall" requirements. This is the ISMS; no exclusions permitted. Certification is against these. |
| Annex A | Normative reference set | 93 information-security controls. Clause 6.1.3(c) requires comparing determined controls against Annex A to verify none necessary was omitted; Annex A's own note states the list is non-exhaustive. Exclusions are permitted with documented justification in the Statement of Applicability. |

The logic runs: assess risk → determine necessary controls → cross-check against Annex A → record the result in the Statement of Applicability. Controls are an output of the risk process, not an input to it.

**Current edition.** Third edition, published October 2022. Amendment 1:2024 (published February 2024) adds climate-action considerations to clauses 4.1 and 4.2 *(wording known from quotations of the amendment, not the amendment text itself)*. Certificates against the 2013 edition ceased to be valid after 31 October 2025, so all audits today run against the 2022 edition.

**Annex A in the 2022 edition.** 93 controls across four themes — Organizational (A.5, 37 controls), People (A.6, 8), Physical (A.7, 14), Technological (A.8, 34). Counts were verified independently against the provided PDF by two of the three interns. Eleven controls are new in 2022 (A.5.7 threat intelligence, A.5.23 cloud services security, A.5.30 ICT readiness for BC, A.7.4 physical monitoring, A.8.9 configuration management, A.8.10 information deletion, A.8.11 data masking, A.8.12 DLP, A.8.16 monitoring activities, A.8.23 web filtering, A.8.28 secure coding), reflecting current cloud, detection and secure-development practice. Implementation guidance for each lives in ISO/IEC 27002:2022, which also tags every control with five attributes (control type; security properties; cybersecurity concepts; operational capabilities; security domains) — a ready-made schema for building a control library.

**How certification works.** An accredited certification body (accredited under ISO/IEC 17021-1 / 27006-1 by a national accreditation body such as UKAS) audits in two stages: Stage 1 reviews documentation and design readiness; Stage 2 samples records to confirm the ISMS operates in practice. Findings are raised as observations, minor or major nonconformities; a major blocks certification until closed. The certificate is valid three years, typically with annual surveillance audits in years one and two and recertification at cycle end.

**Two boundaries worth stating precisely:**
1. Certification attests that a management system meeting the requirements exists and operates *within a declared scope*. It does not attest that the organisation has never been breached or that a specific technical control worked on a specific day. When assessing a supplier's certificate, read the scope statement and SoA exclusions first.
2. ISO 27001 does not certify products. A software company can be certified, but the certificate covers the management system within scope — not the software itself.

## 2. What is SOC 2?

SOC 2 (System and Organization Controls 2) works fundamentally differently: it is not a standard you certify against, it is an **attestation engagement**. A licensed CPA firm examines controls at a service organisation against the AICPA's Trust Services Criteria, under attestation standards AT-C sections 105 and 205, and issues an opinion.

Three consequences follow, and getting them right immediately distinguishes understanding from familiarity:

1. **There is no such thing as "SOC 2 certified".** No certificate, no certifying body, no pass/fail. There is a dated opinion letter on defined controls over a defined period. The useful questions about any report are: what scope, what period, what exceptions, what opinion type.
2. **The controls are yours.** The AICPA supplies criteria — outcomes to be achieved — not controls. Management designs and describes the controls; the auditor tests them. Two organisations with identical criteria can have entirely different control sets.
3. **It is scoped to a described system**, per the Description Criteria (DC200). It is not a universal statement that every system in the organisation is effective.

### 2.1 The Trust Services Criteria

Five categories (definitions quoted verbatim from the TSC text):

- **Security** — "Information and systems are protected against unauthorized access, unauthorized disclosure of information, and damage to systems that could compromise the availability, integrity, confidentiality, and privacy of information or systems and affect the entity's ability to achieve its objectives." Included in essentially every engagement; sufficient on its own through the common criteria.
- **Availability** — "Information and systems are available for operation and use to meet the entity's objectives."
- **Processing integrity** — "System processing is complete, valid, accurate, timely, and authorized to meet the entity's objectives."
- **Confidentiality** — "Information designated as confidential is protected to meet the entity's objectives."
- **Privacy** — personal information collected, used, retained, disclosed and disposed of consistently with the entity's privacy commitments and applicable principles.

Security is mandatory; the others are selected based on the service and customer commitments. The 2022 revision updated points of focus only — it did not alter the criteria themselves — and no successor version has been published as of August 2026 *(negative claim; weakest class of claim in this report — recheck AICPA publications before relying on it in client work)*.

### 2.2 How the common criteria are organised

The criteria align to the 17 COSO Internal Control principles. CC1–CC5 correspond to COSO components; CC6–CC9 are supplemental criteria elaborating COSO Principle 12, and these are what engineers recognise:

| Series | Area |
|---|---|
| CC1 | Control environment |
| CC2 | Information and communication |
| CC3 | Risk assessment |
| CC4 | Monitoring of controls (SOC 2's analogue of ISO's internal-audit clause) |
| CC5 | Control activities |
| CC6 | Logical and physical access (CC6.1 architecture; CC6.2 registration/removal; CC6.3 role-based access; CC6.6 external threats; CC6.7 transmission/removal; CC6.8 unauthorised software) |
| CC7 | System operations (CC7.1 vulnerability detection; CC7.2 anomaly monitoring; CC7.3 event evaluation; CC7.4 incident response; CC7.5 recovery) |
| CC8 | Change management (CC8.1 authorise→design→develop→configure→document→test→approve→implement) |
| CC9 | Risk mitigation (CC9.1 business disruption; CC9.2 vendor/partner risk) |

Points of focus beneath each criterion are interpretive guidance, explicitly *not individually required* by TSP 100. Building a control for every point of focus is a common and expensive first-timer mistake.

### 2.3 Type 1 versus Type 2

Per the AICPA guide: "Generally, in a type 1 examination, the time frame is as of a point in time; in a type 2 examination, it is for a specified period of time," and "in a type 1 examination, the service auditor does not express an opinion about whether the controls operated effectively."

| | Type 1 | Type 2 |
|---|---|---|
| Question answered | Were controls suitably designed and implemented? | Designed AND did they operate effectively? |
| Time dimension | As of a single date | Throughout a period |
| Auditor procedures | Inspection, inquiry, observation of design | All of that plus sampling tests of operating effectiveness across the period |
| Market value | Acceptable first signal | What enterprise procurement actually asks for |

On period length the individual reports initially diverged — vendor-blog sources variously claimed fixed norms. The careful formulation (Elkorbow's) survives review: the period is agreed between management and the CPA firm; practitioner examples commonly run 3, 6 or 12 months, with roughly six months a pragmatic floor buyers tend to accept on a first report and 12 months the mature recurring cadence. There is no universal rule fixing the length. A common path is Type 1 → 3-month Type 2 → annual 12-month Type 2, with bridge letters (management representations, not auditor opinions) covering gaps between periods.

A SOC 2 report contains five parts: the service auditor's report (read the opinion paragraph first), management's assertion, the description of the system (per DC200), the criteria-and-testing section with every exception, and unaudited other information. Opinions are unqualified, qualified, adverse, or disclaimer — a qualified opinion is not automatically disqualifying; which criterion was qualified matters more.

## 3. The main differences between them

| Dimension | ISO/IEC 27001:2022 | SOC 2 |
|---|---|---|
| Nature | Certifiable management-system standard (requirements for a process) | Attestation engagement producing a professional opinion on controls |
| Publisher | ISO/IEC (JTC 1/SC 27) | AICPA (Assurance Services Executive Committee) |
| Assessed by | CB accredited to ISO/IEC 17021-1 / 27006-1 | Licensed CPA firm under AT-C 105/205 |
| Output | Certificate (3-year validity) naming a defined scope | Report with opinion; no certificate; market expects one annually |
| Who chooses controls | Organisation, driven by risk assessment; Annex A is a completeness cross-check; justified exclusions allowed | Organisation designs controls but must collectively satisfy the in-scope criteria; criteria cannot be excluded from an in-scope category |
| Governance machinery | Extensive and explicit: documented risk method, SoA, objectives, internal audit (9.2), management review (9.3), corrective action (10.2) | Implied rather than prescribed: CC3 covers risk assessment, CC4 monitoring — but no mandated SoA or audit function |
| Operating-effectiveness burden | Sampled during Stage 2/surveillance; focus on system conformity | Central question of a Type 2: complete populations sampled across the whole period — a materially higher evidentiary bar per control |
| Public visibility | Certificate public and verifiable; SoA and audit report private | Report restricted-use (NDA); SOC 3 is the public summary variant |
| Failure vocabulary | Observation / minor / major nonconformity | Exceptions, published in the report itself; may drive qualified/adverse opinion |
| Market | Global; frequent hard gate in EU/UK/Gulf/public-sector tenders | Dominant in North-American B2B SaaS procurement, increasingly global |

Three points deserve more attention than blog comparisons give them:

1. **Both are risk-based.** CC3 explicitly requires risk assessment on COSO principles. The lazy contrast fails.
2. **Prescriptiveness differs; rigour doesn't.** ISO hands you a numbered catalogue with justified exclusions; SOC 2 gives outcomes and expects designed controls. A well-scoped SOC 2 can be harder to fake than a copy-pasted SoA.
3. **Overlap claims deserve scepticism.** Vendors advertise "80% overlap between ISO 27001 and SOC 2." We decline to put a number on it: the technical control activities overlap heavily, but the *work* does not, because the two regimes demand different artefacts about the same controls. A mature ISO ISMS gets you most of the way to SOC 2 control design and roughly nowhere on SOC 2 evidence volume — which is where the cost sits.

**Which first, if choosing?** Commercially: do the one your buyers ask for. North-American enterprise SaaS → SOC 2 Type 2. Europe/Gulf/public sector → ISO 27001. If both are coming, build the ISO ISMS first and run SOC 2 on top of it — the ISMS provides the risk methodology, ownership and review cadence that make SOC 2 evidence generation a by-product rather than a project. Either way: one control library, mapped outward; never maintain two.

## 4. What is an Information Security Management System (ISMS)?

An ISMS is the part of an organisation's overall management system — policies, processes, roles, resources, records — that applies a risk-based approach to establishing, implementing, operating, monitoring, reviewing, maintaining and improving information security. ISO 27001 states its purpose directly: it "preserves the confidentiality, integrity and availability of information by applying a risk management process and gives confidence to interested parties that risks are adequately managed."

The mental model the three reports converged on from different directions: **controls are the product; the ISMS is the factory.** Anyone can install MFA. The ISMS determines that MFA was the right thing to install, assigns an owner, sets a target, measures whether it still works months later, audits that measurement independently, escalates failure to management, and closes the loop with corrective action whose effectiveness is itself verified. Without the factory, controls are installed in a burst before an audit and decay immediately afterwards.

As a loop (the classic Plan-Do-Check-Act pattern expressed through clauses 4–10):

Context & scope (cl. 4) → Leadership & policy (cl. 5) → Planning: risk assessment, treatment, SoA (cl. 6) → Support & Operation (cl. 7–8) → Performance evaluation: metrics, internal audit, management review (cl. 9) → Improvement: corrective action (cl. 10) — with findings, metrics and incidents feeding back into context and risk assessment. The dashed return path is the part organisations skip and auditors examine hardest; most major nonconformities are raised against clauses 9 and 10 rather than Annex A.

An engineering gloss that made the concept click for us: the ISMS answers five questions — what information and services matter; what can harm them; which safeguards reduce the risk; how do we know the safeguards operate; what changes when the environment changes.

*(One proposal from the individual reports worth carrying forward: keeping the ISMS artefacts themselves in a Git repository — risks.yaml, controls.yaml, generated SoA — with CI failing the build when a control lacks an owner, an Annex A control is neither mapped nor excluded, or someone hand-edits the generated SoA. This converts clause 6.1.3(c) compliance and clause 7.5 document control into automatic by-products.)*

## 5. What is a security control?

ISO/IEC 27002 defines it in one line: "a measure that modifies or maintains risk." Note the deliberate modesty — *modifies*, not eliminates. COSO approaches from the other side: policies establishing what is expected, procedures putting them into action.

Our operational definition merges both: **a control is a repeatable, owned mechanism that changes the likelihood or impact of a risk, and produces a record proving it operated.** That final clause is not academic — a mechanism with no record is not auditable, not measurable, and in practice not maintained.

The distinction we would defend in review: MFA by itself is not a control. *"All privileged access requires a phishing-resistant second factor, enforced by IdP policy X, reviewed monthly by owner Y, evidenced by configuration export Z"* is a control. The first is a purchase; the second is a testable claim. Weak control statements are unfalsifiable ("access is reviewed periodically"); strong ones name the owner, action, population, frequency, mechanism, record and failure threshold.

Classification axes (used consistently in section 8):

| Axis | Values |
|---|---|
| Function | Preventive · Detective · Corrective (practice adds deterrent, directive, compensating) |
| Nature | Administrative · Technical/logical · Physical |
| Execution | Manual · Semi-automated · Automated |
| Importance | Key vs non-key |

Design effectiveness versus operating effectiveness is the spine of SOC 2 and the single most useful early concept: a control can be designed correctly and still fail operationally (skipped while the owner was on leave). Automated controls shift the risk from "did a human forget?" to "was the automation changed, disabled or bypassed?" — which is why change management and logging become the load-bearing controls that let every other automated control be tested cheaply.

## 6. What is compliance evidence and why does it matter?

Compliance evidence is the set of records allowing an independent party to conclude — without taking anyone's word — that a control existed, was appropriately designed, and operated as described throughout a stated period.

The framing that makes it concrete: an auditor never asks "do you do X?" The question is always "here is the population of everything that should have gone through control X in the period; I've selected twenty-five items; show me for each that X happened, when, and who did it."

**Four kinds of evidence:**

| Kind | Answers | Typical artefacts |
|---|---|---|
| Design | Is the control capable of achieving the objective? | Policies, architecture diagrams, control descriptions |
| Implementation | Does it exist in the live environment? | Configuration exports, Terraform state, branch-protection settings |
| Operating | Did it run, every time, across the period? | Logs, tickets, approvals, review sign-offs, pipeline histories |
| Population | Is the list of controlled things complete and accurate? | Authoritative inventories: HRIS extract, asset inventory, deployment list — usually the weakest link |

Audit-grade evidence is attributable, timestamped and in-period, pulled from the system of record, demonstrably complete, reproducible, tamper-evident (hash at collection, immutable storage), and retained. A screenshot pasted into a document has none of these properties beyond maybe a timestamp; system-generated exports with recorded query parameters have all seven.

**Why it matters — five distinct reasons:**

1. **It is the audit.** In a Type 2 the opinion is formed on evidence. Excellent security with poor records earns a worse report than mediocre security with immaculate records — uncomfortable, but that is how assurance works.
2. **It is the defence after an incident.** GDPR Article 5(2) makes "able to demonstrate compliance" a legal documentation requirement.
3. **It is the sales cycle.** A well-organised evidence library turns a two-week questionnaire into a two-hour exercise.
4. **It is an operating signal.** If you cannot produce evidence a control ran last Tuesday, you do not know it ran. Evidence gaps and control failures are the same phenomenon observed at different times.
5. **It is the input to improvement.** Clauses 9.1 and 10.2 consume evidence; without it, management review becomes opinion-sharing.

**The failure mode nobody warns you about — population completeness (IPE).** Information Produced by the Entity: when you hand over "the list of all production changes in Q2", the auditor must next test whether that list is complete. If a change could reach production without appearing on the list, the control fails — not because the control is bad but because its population can't be trusted. This is why the strongest test designs reconcile two independent sources: deployments observed in CloudTrail versus merged pull requests; IdP accounts versus HR employees; scanner coverage versus asset inventory. A reconciliation proves completeness in a way no single system's own report can.

Evidence goes stale continuously, which is why re-collection dominates GRC labour cost — and why the automation layer in section 8 changes the economics rather than just saving clicks.

## 7. Five controls, engineered end-to-end

### 7.1 Selection — agreed jointly, resolved on evidence

All three individual reports independently selected identity/access management, vulnerability management, and logging/monitoring — a strong consensus signal. Two of three selected secure change/pipeline integrity. For the final slot the reports diverged: encryption & key management (Arebi), backup & recovery (Elkorbow), awareness & training (Elamami).

**Resolution, on attack data rather than preference.** The Verizon 2026 DBIR figures (verified against published analyses; see sources) put ransomware at 48% of breaches, vulnerability exploitation at 31% as the leading initial-access vector, and credential abuse somewhere in 39%. Against that profile, tested recovery capability is the control that still limits damage when every preceding control has failed — and it is the centrepiece of CISA's ransomware guidance precisely because backups that exist but have never been restore-tested do not count. Encryption limits post-failure disclosure but does not restore operations; awareness remains important but has the weakest measurement and automation story of the three candidates. **Backup & recovery verification takes the fifth slot.** The two unselected candidates are documented below with reasons, not silently dropped.

Mnemonic for the spine: **Lock it (identity), Change it safely (pipeline), Patch & protect it (vulnerability), Watch it (logging), Recover anyway (backup).**

| # | Internal ID | Control | Primary Annex A | Primary TSC |
|---|---|---|---|---|
| 1 | HKS-AC-01 | Phishing-resistant identity & access lifecycle | A.5.15–5.18, A.8.2, A.8.5 | CC6.1–CC6.3, CC6.6 |
| 2 | HKS-CM-02 | Secure change & CI/CD pipeline integrity | A.8.25, A.8.28–8.32 | CC8.1, CC6.8 |
| 3 | HKS-VM-03 | Vulnerability & configuration management | A.8.8, A.8.9, A.8.19, A.5.7 | CC7.1, CC8.1 |
| 4 | HKS-LM-04 | Centralised logging, monitoring & incident response | A.8.15–8.17, A.5.24–5.26 | CC7.2–CC7.5 |
| 5 | HKS-BR-05 | Ransomware-resilient backup & recovery verification | A.8.13, A.5.29–5.30 | A1.2, A1.3, CC9.1 |

Considered and not selected: **encryption & key management** (strong preventive control, maps to A.8.24/CC6.1/C-series — recommended as the sixth implementation priority; it lost slot five because it constrains disclosure while recovery constrains existence); **awareness & training** (A.6.3/CC1.4 — genuinely reduces the phishing surface the DBIR quantifies, but its evidence is completion data and simulation statistics rather than system-of-record proof, making it the hardest of the candidates to automate; recommended for immediate adoption alongside, not instead of, the five).

Each control follows the required chain. Implementations reference AWS/GitHub as concrete anchors — patterns, not product endorsements; the same designs map to Azure/GitLab equivalents.

### 7.2 HKS-AC-01 — Phishing-resistant identity & access lifecycle

**Risk.** Credential abuse appears in 39% of breaches and precedes half of ransomware events (DBIR 2026). Phishing captures passwords; ex-employees retain access; privilege creep accumulates silently; over-permissioned automation keys become standing credentials. Identity is the highest-blast-radius control: if it fails, every other control is bypassable.

**Control.** Verify user and device context before granting access; apply least privilege; make privileged access time-bound and reviewable; revoke promptly on HR events. Annex A: A.5.15 access control, A.5.16 identity management, A.5.17 authentication information, A.5.18 access rights, A.8.2 privileged access rights, A.8.5 secure authentication. TSC: CC6.1 (access architecture), CC6.2 (registration before issue, removal when no longer authorised), CC6.3 (role-based modification/removal), CC6.6 (external-threat protection).

**Implementation.** Centralise identity in an IdP with conditional-access policy. Enforce phishing-resistant MFA — FIDO2/WebAuthn keys or passkeys — for all users, hardware-key step-up for administrators (FIDO's precise claim is "phishing-resistant when correctly implemented": public-key cryptography bound to the legitimate origin, no reusable secret transmitted). Machine and pipeline identities use short-lived federated credentials only (OIDC federation, no stored long-lived secrets). RBAC owned by data owners; quarterly access reviews where non-response means revocation; de-provisioning within 24 hours of HR termination signals; break-glass accounts separately inventoried, monitored and tested.

**Evidence.** Design: access-control policy and standard, RBAC matrix, conditional-access export. Operating: access-review sign-offs with reviewer/date/decisions, joiner-mover-leaver records with timestamps, MFA-enrolment coverage report, privileged-session logs, exception register. The strongest single artefact is a daily **HRIS↔IdP↔cloud reconciliation**: no enabled account without an active HR record, no leaver still enabled.

**Testing.** Continuous synthetic attempts: password-only authentication must hard-fail; expired access must fail. Periodic: auditor samples leavers from HRIS and traces deactivation latency; samples 25 JML events checking approval preceded provisioning; reviews privileged-group membership against the approved list. Measures: MFA and phishing-resistant coverage %, revocation latency, stale-access exceptions, approval latency.

**Automation.** The most automatable control family. Nightly job diffs IdP users against HR headcount and auto-tickets orphan accounts; AWS Config rules check MFA and key rotation; OIDC trust-policy audits reject wildcard `sub` conditions; policy-as-code flags over-broad grants at deploy time. Compliance platforms demonstrate the same integration pattern commercially.

### 7.3 HKS-CM-02 — Secure change & CI/CD pipeline integrity

**Risk.** Unreviewed change is self-inflicted breach: one misconfigured bucket or firewall rule exposes data instantly; compromised build tooling or malicious dependencies turn the pipeline itself into the attack vector; leaked secrets grant standing access. The CI/CD pipeline is now the shortest path to production — and the only place a preventive gate touches every change at near-zero marginal cost. Change failure is also a leading cause of availability loss.

**Control.** Changes to software, infrastructure and procedures follow a controlled lifecycle — authorisation, peer review, automated testing, approval, segregation of duties — and build inputs/outputs have verifiable provenance. Annex A: A.8.25 secure development life cycle ("Rules for the secure development of software and systems should be established and applied"), A.8.28 secure coding, A.8.29 security testing, A.8.31 separation of environments, A.8.32 change management. TSC: CC8.1 (authorise→…→implement changes), CC6.8 (unauthorised software prevention).

**Implementation.** Git-centric flow: branches, mandatory peer review, protected main, CI gates (tests, SAST, SCA, secret scanning), dependency pinning, SBOM generation, artifact signing with deploy-time verification, environment separation dev/staging/prod with restricted prod write access, rollback plans for migrations, emergency-change retro-reviews within 48h. Supply-chain guardrails (SBOMs, signing, provenance) are an implementation design derived from risk — informed by NIST SSDF practices — not a claim that an SBOM proves software safe.

**Evidence.** Merge requests with reviewer identities, CI pipeline logs showing gates executed, deployment approvals, SBOMs linked to release identifiers, signing/verification records, dependency-exception approvals, environment-separation matrix. The strongest artefact is again a reconciliation: deployments observed in CloudTrail versus merged approved PRs.

**Testing.** Auditor samples deployments from the release log and traces each back through review, green pipeline and approval. Negative tests in a non-production pipeline: introduce a deliberately vulnerable dependency, unsigned artifact or leaked secret and verify the expected gate blocks it. Attempted direct prod push (in test) confirms branch protection. Emergency-change rate reviewed for abuse.

**Automation.** The pipeline generates its own evidence: every commit yields immutable proof of review, tests and approval. Policy-as-code enforces at deploy time — "no security group open to 0.0.0.0/0 on port 22" becomes a machine-evaluated allow/deny blocking noncompliant infrastructure before it exists. Auto-generated remediation PRs go to human review rather than silently changing production.

### 7.4 HKS-VM-03 — Vulnerability & configuration management

**Risk.** Exploitation of known vulnerabilities is now the top initial-access vector at 31% of breaches (DBIR 2026). Median time to full remediation is 43 days and only 26% of CISA KEV entries were fully remediated — the gap is operational, not technical. Insecure defaults and silent config drift compound exposure.

**Control.** Maintain asset inventory and configuration baselines; identify vulnerabilities and deviations; prioritise by exploitability and business exposure; remediate within risk-based SLAs; prevent unmanaged change from becoming permanent. Annex A: A.8.8 technical vulnerabilities, A.8.9 configuration management, A.8.19 software installation, A.5.7 threat intelligence. TSC: CC7.1 (detection of configuration-introduced vulnerabilities and newly discovered susceptibilities), supporting CC8.1.

**Implementation.** Inventory as precondition (A.5.9). Authenticated weekly scans of all hosts; daily for internet-facing surface. SLAs tiered by exploitability — actively-exploited (KEV) fastest, then critical, high, medium — with exact day-counts set by the organisation's own risk acceptance, not copied from any template. Patch windows with an emergency path; exceptions require named-owner risk acceptance with expiry dates. Infrastructure managed as version-controlled IaC; IaC scanned before deployment; runtime drift detected and either reverted or formally accepted.

**Evidence.** Scan findings with timestamps, remediation tickets linking finding→fix→verification rescan, SLA attainment metrics, signed exception register, inventory-completeness reconciliation (scanner coverage vs asset inventory — a coverage gap is a control gap), SBOMs per release, drift-detection results.

**Testing.** Auditor picks findings from mid-period scans and traces each through ticket→patch→rescan; measures SLA attainment; validates coverage. Independent pentests confirm scanner blind spots. Controlled drift test: make a configuration change outside the pipeline in a staging environment and verify detection, ticketing and reversion.

**Automation.** Scanners automate detection; the GRC layer automates assurance: API-sync findings into ticketing with SLA clocks, auto-close on verified rescan, auto-expiring exceptions. Checkov/OPA in CI catches vulnerable container/Terraform configs pre-deployment. Prioritisation enriched by KEV membership and EPSS scores rather than CVSS severity alone.

### 7.5 HKS-LM-04 — Centralised logging, monitoring & incident response

**Risk.** Breaches dwell undetected for weeks when nobody watches telemetry; late detection multiplies impact through lateral movement, exfiltration and late-notification penalties. Beyond detection, logs are the substrate for every other control's evidence — without trustworthy logs, nothing else in this section can be proved to have operated. Attackers who can delete local logs erase their own trail.

**Control.** Collect security-relevant events from in-scope systems with time accuracy and integrity protection; detect meaningful deviations; evaluate, respond to, and recover from incidents. Annex A: A.8.15 logging, A.8.16 monitoring activities, A.8.17 clock synchronisation, A.5.24–5.26 incident management planning/assessment/response. TSC: CC7.2 (anomaly monitoring), CC7.3 (event evaluation), CC7.4 (incident response), CC7.5 (recovery).

**Implementation.** Define a logging standard covering identity, privileged activity, endpoint, cloud control plane, application, network and backup events. Centralise in a SIEM (Wazuh/ELK at smaller scale); synchronise clocks; separate collection from analysis privileges; retention aligned to legal and forensic needs. Integrity protection where evidence risk warrants — WORM storage such as S3 Object Lock is one cloud example, presented honestly: it prevents alteration/deletion of locked object versions but does not by itself prove all logs were collected, nor replace access controls. Documented IR plan with roles, severity matrix, comms templates; tabletop exercises twice yearly; regulator/customer notification workflow (72-hour GDPR clock).

**Evidence.** Log-source coverage matrix, ingestion-health dashboard, alert-to-triage ticket trails with response times, IR plan version history, tabletop records with lessons learned, postmortems, retention configuration exports, detection-rule change history.

**Testing.** Detection canaries (benign decoy actions) verify the pipeline end-to-end; purple-team injections using atomic red-team techniques verify specific alerts fire and pages land; auditor walks 2–3 real incidents detection→triage→containment→postmortem. Measures: critical-source coverage %, mean time to detect/contain, alert precision, % high-severity alerts with documented closure. Targets are organisation-set; no universal MTTD number is claimed.

**Automation.** SOAR playbooks for containment speed (auto-isolate endpoint, revoke sessions) — high-impact actions gated behind strong authorisation, rollback paths and human escalation. SIEM exports coverage and MTTD/MTTR metrics continuously, turning the annual evidence pull into a query. A failing health check is an alert, not a silent artefact.

### 7.6 HKS-BR-05 — Ransomware-resilient backup & recovery verification

**Risk.** Ransomware reached 48% of breaches (DBIR 2026). Encryption of data, destructive deletion, compromise of backup credentials themselves, prolonged outage, inability to restore trustworthy services. Backups that exist but have never been restored are a hope, not a control.

**Control.** Maintain recoverable, protected copies of critical data — including at least one logically or physically separated from the production attack path — and demonstrate through exercises that critical services restore within approved RTO/RPO objectives. Annex A: A.8.13 information backup, A.5.29/A.5.30 continuity. TSC: Availability criteria A1.2/A1.3, CC9.1.

**Implementation.** Encrypted backups; administration separated from production identities with its own MFA; retention protection or immutable storage (Object Lock as one layer, complemented by account/region separation, offline copies where justified, clean recovery environments); backup jobs monitored for success *and* for retention-configuration changes.

**Evidence.** Backup policy, job-success history, immutability configuration exports, restore runbooks, recovery-test results with measured RTO/RPO, integrity/hash checks on restores, access-review records for backup administration, issues raised during exercises and their closure.

**Testing.** Scheduled restore tests using representative data and systems; measure actual recovery time and data loss against objectives; clean-room recovery exercises; attempt backup modification during retention to confirm immutability holds. The business outcome is demonstrated recoverability, not green backup dashboards.

**Automation.** Schedule backups and restore verifications; alert on failed jobs, retention changes or missing sources; automatically generate recovery-evidence packages; gate incident closure on evidence of successful restore rather than a successful backup job alone.

### 7.7 One control set, many frameworks

Store mappings as data (`crosswalk.yaml`), not spreadsheet rows. Three outputs then become generated rather than hand-maintained: the Statement of Applicability (every Annex A control either maps to an implemented control or carries a documented exclusion — clause 6.1.3(c) executed automatically), the SOC 2 Section IV control matrix, and the gap report when a new framework arrives (NIST CSF 2.0, CIS v8, DORA, ISO/IEC 42001) — a set difference, not a workshop.

---

## 8. AI proposal: the Evidence Assurance Agent

The three individual reports each proposed an AI system — Arebi's *Evidence Sufficiency Reviewer*, Elkorbow's *GRC-Sentinel*, Elamami's *Evidence Concierge*. Their convergence is itself a finding: working independently, all three identified the same bottleneck and the same safety shape. This section merges them into one proposal.

**The bottleneck.** The expensive part of both ISO 27001 and SOC 2 is not implementing controls; it is proving them, continuously. Before an audit, analysts review hundreds of artefacts asking: does this actually demonstrate this control operated, for this period, over the complete population? The failure modes are mundane and consistent — out-of-period artefacts, policies filed against operating-effectiveness tests, undisclosed filters, screenshots of screenshots, record counts contradicting stated populations, artefacts filed against the wrong control. None are hard judgements; all are numerous, tedious, and performed under deadline pressure — exactly the profile where humans err consistently and a well-scoped model performs well.

**The proposal — three cooperating functions:**

1. **Continuous collection (deterministic).** Allow-listed read-only connectors stream control-relevant state from IdP, cloud APIs, ticketing, repos and HRIS into a versioned evidence store. Every artefact is hashed at collection, stored immutably, and described by a manifest recording source, query, record count and collector version. Roughly half of real evidence defects are caught here by comparison operators alone — timestamps out of period, hash mismatches, zero counts — at zero inference cost. Never ask a model a question a comparison operator can answer.
2. **LLM sufficiency triage (retrieval-grounded).** For artefacts passing pre-checks, a tenant-isolated LLM evaluates the artefact *against retrieved control text* — the control narrative, the mapped TSC criterion, the mapped Annex A wording — never from memory. Output is constrained JSON only: verdict (SUFFICIENT / INSUFFICIENT / UNCERTAIN), confidence, coded reasons, and exact quotations from the artefact supporting the verdict.
3. **Audit-prep mapping.** The same agent maps collected evidence against the auditor's likely test plan per criterion, flags gaps before fieldwork, and drafts the human-reviewable evidence index.

**The design decision that makes it safe — asymmetric authority.** The model is permitted to lower confidence in evidence but never to raise it. A SUFFICIENT verdict changes nothing; only INSUFFICIENT and UNCERTAIN act, by adding items to a human review queue. The system can create work, never remove it. A hallucinated approval has no path to becoming an accepted control; a successful prompt-injection attack produces a no-op. Framed against the OWASP Top 10 for LLM Applications: prompt injection addressed structurally (untrusted-content delimiters, schema-constrained output), excessive agency removed entirely, overreliance countered by mandatory human decision.

**Governance, because this internship includes AI governance.** The agent is an entry in the AI system inventory with a documented purpose, data flow, owner and retirement position — aligned to NIST's AI RMF (Govern/Map/Measure/Manage; the evaluation set below is the Measure function) and mappable onto ISO/IEC 42001 clauses. Full decision logging: model ID, prompt version, retrieved-context hash, raw output, human disposition — the AI system's own operation must itself be auditable, or it becomes an unevidenced control inside a framework built on evidence.

**Proving it works.** Build a labelled evaluation set first — ~200 artefacts, half deliberately defective with defects drawn from real audit findings — before writing the prompt, so the prompt isn't tuned to the test. Primary metric: recall on defective artefacts ≥0.95 (missing a bad artefact costs a Section IV exception). Secondary: precision ≥0.70 (below ~0.5 the queue becomes noise and analysts rubber-stamp, destroying the value — a human-factors threshold). Adversarial suite: injection payloads in log lines, commit messages, ticket bodies; required result zero behaviour change. Explicitly *not* measured: "time saved" — judging the tool on reducing human review runs the incentive gradient straight through the asymmetry guardrail.

**Pilot shape.** One cloud account, one identity source, one CI platform, limited controls. Phase 1 (build, weeks 1–3): evaluation set + deterministic pre-checks live. Phase 2 (shadow, weeks 4–7): verdicts logged, not shown; compared against independent analyst decisions. Phase 3 (assist, weeks 8–12): flags surfaced in the queue; success measured as defects found before the auditor finds them. Phase 4 (decision, week 13): keep, tune or stop — on evidence. First release classifies evidence and opens review tasks; it never modifies production.

---

## 9. Points we disagreed on, and how we resolved them

Recorded because the programme brief grades reasoning, not just conclusions:

1. **Fifth control.** Encryption (Arebi) vs backup/recovery (Elkorbow) vs awareness (Elamami). Resolved on DBIR attack data toward backup & recovery (section 7.1); the losers stay documented with their cases.
2. **"80% overlap" between the frameworks.** Rejected as a claim to repeat: unfalsifiable as usually stated, and it measures the wrong thing — control activities overlap, evidence volume doesn't.
3. **Type II period norms.** Vendor sources imply fixed rules ("6 months minimum", "always 12"). Resolved to Elkorbow's formulation: period is agreed with the CPA firm; ranges are practitioner convention, not rule.
4. **Asset inventory: "control zero" or a control?** Open question, held loosely. Position taken: precondition, with completeness built into each control's testing (reconciliations) rather than stood up as a standalone sixth control. Counter-arguments welcome in review.
5. **Immutable evidence stores vs privacy rights.** Compliance-mode Object Lock means nobody can delete before expiry — including in response to a legitimate erasure request touching evidence containing personal data. Genuine tension between evidential integrity and data-protection law; unresolved, flagged for discussion.
6. **Fixed SLA numbers** (72-hour patching, 24-hour revocation). Presented as design examples; each organisation must set its own risk-based values. An arbitrary number quoted as a standard requirement is a hallmark of copy-paste compliance.

## 10. Limitations

Stated plainly, jointly:

- Individual implementations referencing AWS/GitHub services are illustrative patterns; managed-rule catalogues change and should be re-checked at implementation time. None of it has been deployed in a live environment yet — the most valuable next step is building controls 1 and 3 in a sandbox account to learn what survives contact with reality.
- The DBIR figures derive from published analyses of the 2026 report rather than our own reading of the full dataset.
- Amendment 1:2024 wording is known from quotations, not the amendment text.
- Cost figures circulating in earlier drafts (audit-day rates, $50k–$120k Type II estimates) come from vendor sources, vary widely, and were deliberately left out of the unified report rather than laundered into false precision.
- The negative claim that no new TSC version exists is the weakest class of claim in this document and should be rechecked against AICPA publications before client use.

## Sources

**Primary standards (read directly from the programme resource pack):**
1. ISO/IEC 27001:2022 (third edition) — Requirements
2. ISO/IEC 27002:2022 — Information security controls (incl. attribute model)
3. AICPA TSP section 100 — 2017 Trust Services Criteria with Revised Points of Focus (2022)
4. AICPA DC section 200 — Description Criteria for a SOC 2 Report
5. AICPA SOC 2 Guide (October 2022)

**Public sources (verified August 2026):**
- ISO — ISO/IEC 27001:2022/Amd 1:2024 catalogue entry (iso.org/standard/88435.html); iso.org/standard/27001
- Verizon — 2026 Data Breach Investigations Report, and published analyses thereof (Help Net Security, May 2026; Push Security review)
- NIST — SSDF (SP 800-218); Cybersecurity Framework 2.0; AI Risk Management Framework
- CISA — Known Exploited Vulnerabilities catalogue; ransomware and vulnerability-management guidance
- FIDO Alliance — passkey/WebAuthn phishing-resistance explanations
- AWS — Audit Manager SOC 2 framework docs; Config conformance packs; S3 Object Lock documentation; AICPA SOC 2 on AWS whitepaper
- IT Governance/GRCSolutions — ISO 27001 certification cost & cycle guidance
- LRQA — ISO 27001 Stage 1/Stage 2 FAQ
- GRC Engineering Club — compliance-as-code / policy-as-code practice
- OWASP — Top 10 for LLM Applications

*Individual reports: Arebi, A. "ISO 27001 & SOC 2" (58 pp., v1.0, 24 Aug 2026) · Elkorbow, A.A. "Security, Governance & Compliance Framework" (12 pp., 17 Aug 2026) · Elamami, M. "ISO 27001 vs SOC 2" (~20 pp., Aug 2026). Control identifiers prefixed HKS- are illustrative and defined within this document only.*
