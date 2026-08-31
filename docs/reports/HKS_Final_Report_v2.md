# HkS Security, Governance & Compliance Framework — Assignment 1: ISO/IEC 27001 & SOC 2

**Prepared jointly by:** Ahmed Arebi · Abo Alqasem Elkorbow · Marwan Elamami
**HkS Internship Programme | Security & AI Lab | August 2026**

## 1. Scope, method and AI use

Each intern researched Assignment 1 independently and produced an individual report (Arebi, 58 pp.; Elkorbow, 12 pp.; Elamami, ~20 pp.). This document consolidates the three, removing repeated definitions while retaining the strongest material wherever it improves technical precision.

The discipline was the same in all three reports:

- Primary sources first. Clause numbers, control identifiers and criterion wording were read directly from the standards supplied in the programme resource pack — ISO/IEC 27001:2022, ISO/IEC 27002:2022, AICPA TSP section 100 (2017 Trust Services Criteria with Revised Points of Focus 2022), AICPA DC section 200, and the AICPA SOC 2 Guide (October 2022) — not recalled from blogs or model output.
- Secondary sources only where the standards are silent (threat statistics, certification mechanics, market timelines), attributed inline.
- AI tooling was used for acceleration: research triage, structuring, drafting. Every load-bearing claim was checked against source text, and claims that could not be traced to a primary or reputable secondary source are marked as such rather than silently kept.

One correction made during research shaped this report: the common framing "ISO 27001 is risk-based, SOC 2 is checklist-based" is wrong. SOC 2's CC3 series requires formal risk assessment on COSO principles, so both regimes are risk-based; they differ in what they demand evidence *of*.

## 2. What is ISO/IEC 27001?

ISO/IEC 27001:2022 — *Information security, cybersecurity and privacy protection — Information security management systems — Requirements* — specifies "the requirements for establishing, implementing, maintaining and continually improving an information security management system within the context of the organization," including requirements for assessing and treating information security risks. It is published jointly by ISO and IEC under JTC 1/SC 27 and is the standard in the 27000 family against which an organisation can be certified by an accredited third party.

### Requirements versus controls

Newcomers equate ISO 27001 with its control catalogue. Auditors test something else:

| Part | Status | Meaning |
|---|---|---|
| Clauses 0–3 | Informative | Scope, references, terms. Not auditable. |
| Clauses 4–10 | Mandatory | The "shall" requirements. This is the ISMS; no exclusions permitted. Certification runs against these. |
| Annex A | Normative reference set | 93 information-security controls. Exclusions permitted with documented justification in the Statement of Applicability. |

The logic runs: assess risk → determine necessary controls → cross-check against Annex A → record the result in the SoA. Controls are an output of the risk process, never an input to it.

### Structure of clauses 4–10

| Clause | Main purpose | Typical outputs or evidence |
|---|---|---|
| 4 — Context | Define internal/external issues, interested parties, ISMS scope | Scope statement, stakeholder and dependency analysis |
| 5 — Leadership | Management commitment, policy, roles | Approved policy, role assignments |
| 6 — Planning | Assess and treat risks, set objectives | Risk methodology, risk register, treatment plan, SoA |
| 7 — Support | Resources, competence, awareness, documented information | Training records, controlled policies |
| 8 — Operation | Execute risk assessments and treatment plan | Operational records, control activities |
| 9 — Performance evaluation | Monitor, measure, audit, review | Metrics, internal-audit reports, management-review minutes |
| 10 — Improvement | Address nonconformities, improve | Corrective-action records, root-cause analysis, effectiveness checks |

Clauses 9 and 10 deserve particular weight: an organisation can run technically strong safeguards yet operate an ineffective ISMS if it cannot measure performance, audit itself, hold management reviews, or close corrective actions.

### Annex A in the 2022 edition

Third edition, published October 2022. Amendment 1:2024 (February 2024) adds climate-action considerations to clauses 4.1 and 4.2 *(wording known from quotations of the amendment, not the amendment text itself)*. Certificates against the 2013 edition ceased to be valid after 31 October 2025, so all current audits run against the 2022 edition.

Annex A holds 93 controls across four themes: Organizational (A.5, 37 controls), People (A.6, 8), Physical (A.7, 14), Technological (A.8, 34). Counts were verified independently against the provided PDF by two of the three interns. Eleven controls are new in 2022: A.5.7 threat intelligence, A.5.23 cloud services security, A.5.30 ICT readiness for business continuity, A.7.4 physical monitoring, A.8.9 configuration management, A.8.10 information deletion, A.8.11 data masking, A.8.12 data leakage prevention, A.8.16 monitoring activities, A.8.23 web filtering, and A.8.28 secure coding — reflecting current cloud, detection and secure-development practice. Implementation guidance lives in ISO/IEC 27002:2022, which also tags every control with five attributes (control type; security properties; cybersecurity concepts; operational capabilities; security domains), a ready-made schema for a control library.

### The Statement of Applicability

Clause 6.1.3 requires determining which controls are needed to treat assessed risks, then — 6.1.3(c) — comparing them against Annex A to verify nothing necessary was omitted, and — 6.1.3(d) — producing a Statement of Applicability recording each control as applicable or excluded, with justification for exclusions and implementation status. Annex A's own note states the list is non-exhaustive, so additional controls outside it may be required by the risk assessment.

### Certification

An accredited certification body (accredited under ISO/IEC 17021-1 / 27006-1 by a national accreditation body such as UKAS) audits in two stages: Stage 1 reviews documentation and design readiness; Stage 2 samples records to confirm the ISMS operates in practice. Findings are observations, minor or major nonconformities; a major blocks certification until closed. The certificate is valid three years, typically with annual surveillance audits in years one and two and recertification at cycle end.

Two boundaries worth stating precisely:

1. Certification attests that a conforming management system exists and operates *within a declared scope*. It does not attest that the organisation has never been breached or that a specific technical control worked on a given day. When assessing a supplier's certificate, read the scope statement and SoA exclusions first.
2. ISO 27001 does not certify products. A software company can be certified, but the certificate covers the management system within scope, not the software.

## 3. What is SOC 2?

SOC 2 works differently at the root: it is an **attestation engagement**, not a standard you certify against. A licensed CPA firm examines controls at a service organisation against the AICPA's Trust Services Criteria under attestation standards AT-C 105 and 205, and issues an opinion.

Three consequences follow:

1. There is no such thing as "SOC 2 certified." No certificate, no certifying body, no pass/fail. There is a dated opinion letter on defined controls over a defined period. The useful questions about any report are: what scope, what period, what exceptions, what opinion type.
2. The controls are yours. The AICPA supplies criteria — outcomes to be achieved — not controls. Management designs and describes the controls; the auditor tests them. Two organisations facing identical criteria can have entirely different control sets.
3. The report is scoped to a described system, per the Description Criteria (DC200). It is not a universal statement that every system in the organisation is effective.

### The five Trust Services Criteria

Definitions quoted verbatim from the TSC text:

| Category | Definition (TSP 100) |
|---|---|
| Security | "Information and systems are protected against unauthorized access, unauthorized disclosure of information, and damage to systems that could compromise the availability, integrity, confidentiality, and privacy of information or systems and affect the entity's ability to achieve its objectives." |
| Availability | "Information and systems are available for operation and use to meet the entity's objectives." |
| Processing integrity | "System processing is complete, valid, accurate, timely, and authorized to meet the entity's objectives." |
| Confidentiality | "Information designated as confidential is protected to meet the entity's objectives." |
| Privacy | Personal information collected, used, retained, disclosed and disposed of consistently with the entity's privacy commitments and applicable principles. |

Security is included in essentially every engagement and is sufficient on its own through the common criteria; the others are selected based on the service and customer commitments. The 2022 revision updated points of focus only, not the criteria themselves.

### Common criteria CC1–CC9

The criteria align to the 17 COSO Internal Control principles. CC1–CC5 map to COSO components; CC6–CC9 elaborate COSO Principle 12, and these are what engineers recognise:

| Series | Area |
|---|---|
| CC1 | Control environment |
| CC2 | Information and communication |
| CC3 | Risk assessment |
| CC4 | Monitoring of controls (SOC 2's analogue of ISO clause 9) |
| CC5 | Control activities |
| CC6 | Logical and physical access (CC6.1 architecture; CC6.2 registration/removal; CC6.3 role-based access; CC6.6 external threats; CC6.7 transmission/removal; CC6.8 unauthorised software) |
| CC7 | System operations (CC7.1 vulnerability detection; CC7.2 anomaly monitoring; CC7.3 event evaluation; CC7.4 incident response; CC7.5 recovery) |
| CC8 | Change management (CC8.1 authorise→design→develop→configure→document→test→approve→implement) |
| CC9 | Risk mitigation (CC9.1 business disruption; CC9.2 vendor/partner risk) |

Points of focus beneath each criterion are interpretive guidance, explicitly not individually required by TSP 100. Building a control for every point of focus is a common and expensive first-timer mistake.

### Type I versus Type II

Per the AICPA guide: "Generally, in a type 1 examination, the time frame is as of a point in time; in a type 2 examination, it is for a specified period of time," and "in a type 1 examination, the service auditor does not express an opinion about whether the controls operated effectively."

| Dimension | Type 1 | Type 2 |
|---|---|---|
| Question answered | Were controls suitably designed and implemented? | Designed, and did they operate effectively? |
| Time dimension | As of a single date | Throughout a period |
| Auditor procedures | Inspection, inquiry, observation of design | All of that plus sampling tests of operating effectiveness across the period |
| Market value | Acceptable first signal | What enterprise procurement actually asks for |

On period length the individual reports initially diverged; vendor-blog sources variously claimed fixed norms. The formulation that survives review: the period is agreed between management and the CPA firm. Practitioner examples commonly run 3, 6 or 12 months, with roughly six months a pragmatic floor buyers tend to accept on a first report and twelve months the mature recurring cadence. No universal rule fixes the length. A common path is Type 1 → short-period Type 2 → annual 12-month Type 2, with bridge letters covering gaps between periods — bridge letters are management representations, not auditor opinions.

A SOC 2 report contains five parts: the service auditor's report (read the opinion paragraph first), management's assertion, the description of the system (per DC200), the criteria-and-testing section with every exception, and unaudited other information. Opinions come in four types: unqualified, qualified, adverse, and disclaimer of opinion. A qualified opinion is not automatically disqualifying; which criterion was qualified matters more.

SOC 2 sits inside a family: SOC 1 covers controls relevant to customers' financial reporting, SOC 2 covers security/availability/processing-integrity/confidentiality/privacy, and SOC 3 is a general-use summary of a SOC 2 examination without detailed testing results.

## 4. Main differences between ISO/IEC 27001 and SOC 2

| Dimension | ISO/IEC 27001:2022 | SOC 2 |
|---|---|---|
| Nature | Certifiable management-system standard | Attestation engagement producing a professional opinion |
| Publisher | ISO/IEC (JTC 1/SC 27) | AICPA (Assurance Services Executive Committee) |
| Assessed by | CB accredited to ISO/IEC 17021-1 / 27006-1 | Licensed CPA firm under AT-C 105/205 |
| Output | Certificate, 3-year validity, named scope | Restricted-use report with opinion; no certificate; market expects one annually |
| Who chooses controls | Organisation, driven by risk; Annex A is a completeness cross-check; justified exclusions allowed | Organisation designs controls but must collectively satisfy in-scope criteria; criteria cannot be dropped from an in-scope category |
| Governance machinery | Explicit and extensive: risk method, SoA, objectives, internal audit (9.2), management review (9.3), corrective action (10.2) | Implied rather than prescribed: CC3 and CC4 cover risk and monitoring, but no mandated SoA or audit function |
| Operating-effectiveness burden | Sampled during Stage 2/surveillance; focus on system conformity | Central question of a Type 2: complete populations sampled across the whole period — a materially higher evidentiary bar per control |
| Public visibility | Certificate public and verifiable; SoA and audit report private | Report restricted-use (NDA); SOC 3 is the public summary variant |
| Failure vocabulary | Observation / minor / major nonconformity | Exceptions, published in the report itself; may drive qualified/adverse opinion |
| Market | Global; frequent hard gate in EU/UK/Gulf/public-sector tenders | Dominant in North-American B2B SaaS procurement, increasingly global |

Three points deserve more attention than blog comparisons give them:

1. Both regimes are risk-based. SOC 2's CC3 explicitly requires risk assessment on COSO principles, so the lazy contrast fails.
2. Prescriptiveness differs; rigour doesn't. ISO hands you a numbered catalogue with justified exclusions; SOC 2 gives outcomes and expects designed controls. A well-scoped SOC 2 can be harder to fake than a copy-pasted SoA.
3. Overlap claims deserve scepticism. Vendors advertise "80% overlap" between the two. We decline to put a number on it: the technical control activities overlap heavily, but the work does not, because the two regimes demand different artefacts about the same controls. A mature ISO ISMS gets you most of the way to SOC 2 control design and roughly nowhere on SOC 2 evidence volume — which is where the cost sits.

Which first, if choosing? Commercially: do the one your buyers ask for. North-American enterprise SaaS → SOC 2 Type 2. Europe/Gulf/public sector → ISO 27001. If both are coming, build the ISO ISMS first and run SOC 2 on top of it; the ISMS provides the risk methodology, ownership and review cadence that make SOC 2 evidence generation a by-product rather than a project. Either way: one control library, mapped outward. Never maintain two.

## 5. What is an ISMS?

An ISMS is the part of an organisation's overall management system — policies, processes, roles, resources, records — that applies a risk-based approach to establishing, implementing, operating, monitoring, reviewing, maintaining and improving information security. ISO 27001 states its purpose directly: it "preserves the confidentiality, integrity and availability of information by applying a risk management process and gives confidence to interested parties that risks are adequately managed."

The mental model all three reports converged on: **controls are the product; the ISMS is the factory.** Anyone can install MFA. The ISMS determines that MFA was the right thing to install, assigns an owner, sets a target, measures whether it still works months later, audits that measurement independently, escalates failure to management, and closes the loop with corrective action whose effectiveness is itself verified. Without the factory, controls get installed in a burst before an audit and decay immediately afterwards.

As a loop, the classic Plan-Do-Check-Act pattern expressed through clauses 4–10:

| Stage | Practical question | Clauses / activity |
|---|---|---|
| Plan | What matters, what can harm it, what risk level is acceptable? | Context and scope (4), leadership (5), planning: risk assessment, treatment, SoA (6) |
| Do | How will we reduce the identified risks? | Support and operation (7–8): implement policies, people, technical controls |
| Check | How do we know the system is working? | Performance evaluation (9): metrics, internal audit, management review |
| Act | What changes when weaknesses or the environment change? | Improvement (10): corrective action, root causes, updated treatment |

Findings, metrics and incidents feed back into context and risk assessment. That return path is the part organisations skip and auditors examine hardest: most major nonconformities are raised against clauses 9 and 10 rather than Annex A. A technically strong safeguard portfolio with no measurement loop is still an ineffective ISMS.

A mature ISMS maintains, at minimum: a coherent scope statement, information-security policy, risk-assessment method, risk register, risk-treatment plan, Statement of Applicability, control library, security objectives, competence records, operational records, monitoring metrics, internal-audit results, management-review records, and a corrective-action register.

One proposal from the individual reports worth carrying forward: keep the ISMS artefacts themselves in a Git repository — risks.yaml, controls.yaml, generated SoA — with CI failing the build when a control lacks an owner or an Annex A control is neither mapped nor excluded. That turns clause 6.1.3(c) compliance and clause 7.5 document control into automatic by-products.

## 6. What is a security control?

ISO/IEC 27002 defines it in one line: "a measure that modifies or maintains risk." Note the deliberate modesty — *modifies*, not eliminates. COSO approaches from the other side: policies establishing what is expected, procedures putting them into action.

Our operational definition merges both: a control is a repeatable, owned mechanism that changes the likelihood or impact of a risk, and produces a record proving it operated. That final clause is not academic. A mechanism with no record is not auditable, not measurable, and in practice not maintained.

MFA by itself is not a control. *"All privileged access requires a phishing-resistant second factor, enforced by IdP policy X, reviewed monthly by owner Y, evidenced by configuration export Z"* is a control. The first is a purchase; the second is a testable claim. Weak statements are unfalsifiable ("access is reviewed periodically"). Strong ones name the owner, action, population, frequency, mechanism, record and failure threshold.

Classification axes used throughout this report:

| Axis | Values |
|---|---|
| Function | Preventive · Detective · Corrective (practice adds deterrent, directive, compensating) |
| Nature | Administrative · Technical/logical · Physical |
| Execution | Manual · Semi-automated · Automated |
| Importance | Key vs non-key |

Controls sit among related governance artefacts:

| Term | Meaning |
|---|---|
| Policy | Management's approved statement of intent and mandatory direction |
| Standard | Specific, measurable requirements implementing the policy |
| Procedure | Detailed steps describing how an activity is performed |
| Guideline | Recommended practice, not necessarily mandatory |
| Control | The repeatable operating mechanism, together with evidence that it operated |

Design versus operating effectiveness is the spine of SOC 2 and the single most useful early concept: a control can be designed correctly and still fail operationally (skipped while its owner was on leave). Automated controls shift the risk from "did a human forget?" to "was the automation changed, disabled or bypassed?" — which is why change management and logging become the load-bearing controls that let every other automated control be tested cheaply.

## What is compliance evidence and why does it matter?

Compliance evidence is the set of records allowing an independent party to conclude — without taking anyone's word — that a control existed, was appropriately designed, and operated as described throughout a stated period. An auditor never asks "do you do X?" The question is always: here is the population of everything that should have gone through control X in the period; I've selected twenty-five items; show me for each that X happened, when, and who did it.

Four kinds:

| Kind | Answers | Typical artefacts |
|---|---|---|
| Design | Is the control capable of achieving the objective? | Policies, architecture diagrams, control descriptions |
| Implementation | Does it exist in the live environment? | Configuration exports, Terraform state, branch-protection settings |
| Operating | Did it run, every time, across the period? | Logs, tickets, approvals, review sign-offs, pipeline histories |
| Population | Is the list of controlled things complete and accurate? | Authoritative inventories: HRIS extract, asset inventory, deployment list — usually the weakest link |

Audit-grade evidence is attributable, timestamped and in-period, pulled from the system of record, demonstrably complete, reproducible, tamper-evident (hash at collection, immutable storage), and retained. A screenshot pasted into a document has none of these properties beyond maybe a timestamp; system-generated exports with recorded query parameters have all seven.

Five reasons it matters:

1. It is the audit. In a Type 2 the opinion is formed on evidence. Excellent security with poor records earns a worse report than mediocre security with immaculate records — uncomfortable, but that is how assurance works.
2. It is the defence after an incident. GDPR Article 5(2) makes "able to demonstrate compliance" a legal documentation requirement.
3. It is the sales cycle. A well-organised evidence library turns a two-week questionnaire into a two-hour exercise.
4. It is an operating signal. If you cannot produce evidence a control ran last Tuesday, you do not know it ran. Evidence gaps and control failures are the same phenomenon observed at different times.
5. It is the input to improvement. Clauses 9.1 and 10.2 consume evidence; without it, management review becomes opinion-sharing.

The failure mode nobody warns you about is population completeness, formalised in attestation standards as Information Produced by the Entity (IPE). Hand over "the list of all production changes in Q2" and the auditor must next test whether that list is complete. If a change could reach production without appearing on the list, the control fails — not because the control is bad but because its population can't be trusted. The strongest test designs therefore reconcile two independent sources: deployments observed in CloudTrail versus merged pull requests; IdP accounts versus HR employees; scanner coverage versus asset inventory. A reconciliation proves completeness in a way no single system's own report can.

Evidence goes stale continuously. Re-collection dominates GRC labour cost, which is why automation changes the economics rather than just saving clicks.

## 7. Five security controls, engineered end-to-end

### 7.1 Selection — agreed jointly, resolved on data

All three individual reports independently selected identity/access management, vulnerability management, and logging/monitoring. Two of three selected secure change and pipeline integrity. For the fifth slot the reports diverged: encryption & key management (Arebi), backup & recovery (Elkorbow), awareness & training (Elamami).

We resolved the conflict on attack data rather than preference. Reported figures from published analyses of the Verizon 2026 DBIR put ransomware at 48% of breaches, vulnerability exploitation at 31% as the leading initial-access vector, and credential abuse present in 39%. One caveat belongs next to those numbers: they are secondary-source-derived figures about a report we did not read in full, so we rely on them directionally rather than precisely. Against that threat profile, tested recovery capability is the control that still limits damage when every preceding control has failed. Encryption constrains post-failure disclosure but does not restore operations, so it is folded into control 5 as its data-protection elements (encrypted backups, key administration separated from key use) rather than given its own slot. Awareness & training stays in considered-not-selected below with its case stated.

Mnemonic for the spine: **Lock it** (identity) · **Change it safely** (pipeline) · **Patch & protect it** (vulnerability) · **Watch it** (logging) · **Recover anyway** (backup).

| # | Internal ID | Control | Primary Annex A | Primary TSC |
|---|---|---|---|---|
| 1 | HKS-AC-01 | Phishing-resistant identity & access lifecycle | A.5.15–5.18, A.8.2, A.8.5 | CC6.1–CC6.3, CC6.6 |
| 2 | HKS-CM-02 | Secure change & CI/CD pipeline integrity | A.8.25, A.8.28–8.32 | CC8.1, CC6.8 |
| 3 | HKS-VM-03 | Vulnerability & configuration management | A.8.8, A.8.9, A.8.19, A.5.7 | CC7.1, CC8.1 |
| 4 | HKS-LM-04 | Centralised logging, monitoring & incident response | A.8.15–8.17, A.5.24–5.26 | CC7.2–CC7.5 |
| 5 | HKS-BR-06 | Ransomware-resilient backup, recovery & data protection | A.8.13, A.8.24, A.5.29–5.30 | A1.2, A1.3, CC9.1 |

Considered and not selected:

- **Encryption & key management.** A strong preventive control mapping to A.8.24/CC6.1/C-series. It lost slot five because it limits disclosure while recovery limits existence; it survives intact inside HKS-BR-06 as encryption-at-rest, secure transport, and separation of key administration from key use.
- **Awareness & training.** Genuinely reduces the phishing surface the DBIR quantifies, and we recommend adopting it alongside the five. Its evidence is completion data and simulation statistics rather than system-of-record proof, which makes it the hardest of the three candidates to automate or test with negative cases.

Each control follows the required chain of six stages. Implementations reference AWS/GitHub services as concrete anchors; these are patterns, not endorsements, and map to Azure/GitLab equivalents.

### 7.2 HKS-AC-01 — Phishing-resistant identity & access lifecycle

**Risk.** Credential abuse appears in 39% of breaches and precedes roughly half of ransomware events per the DBIR analyses. Phishing captures passwords, ex-employees retain access, privilege creep accumulates silently, and over-permissioned automation keys become standing credentials. Identity is the highest-blast-radius control: when it fails, every other control is bypassable.

**Control.** Verify user and device context before granting access; apply least privilege; make privileged access time-bound and reviewable; revoke promptly on HR events. Annex A: A.5.15–A.5.18, A.8.2, A.8.5. TSC: CC6.1 (access architecture), CC6.2 (registration before issue, removal when no longer authorised), CC6.3 (role-based modification/removal), CC6.6 (external-threat protection).

**Implementation.** Centralise identity in one authoritative IdP behind conditional-access policy. Enforce phishing-resistant MFA (FIDO2/WebAuthn keys or passkeys) for all users with hardware-key step-up for administrators; FIDO's own claim is carefully worded, "phishing-resistant when correctly implemented," because public-key cryptography binds to the legitimate origin and transmits no reusable secret. Machine and pipeline identities use short-lived federated credentials via OIDC, never stored long-lived secrets. Joiner-mover-leaver processes must *replace* obsolete role membership rather than continuously adding permissions, or privilege creep is built into the process itself. Quarterly access reviews where non-response means revocation; de-provisioning within 24 hours of HR termination signals; break-glass accounts separately inventoried, monitored and reviewed after each use.

**Evidence.** Design: access policy, RBAC matrix, conditional-access export. Operating: review sign-offs with reviewer/date/decision, JML records with timestamps, MFA coverage reports, privileged-session logs, exception register. The strongest single artefact is a daily HRIS↔IdP↔cloud reconciliation: no enabled account without an active HR record, no leaver still enabled.

**Testing.** Negative tests run continuously: password-only authentication must hard-fail; expired access must fail; unauthorised access-key creation must be denied and logged. An auditor samples leavers from HRIS and traces deactivation latency, samples 25 JML events checking approval preceded provisioning, and reviews privileged-group membership against the approved list. Measures: phishing-resistant coverage %, revocation latency, stale-access exceptions, approval latency.

**Automation.** The most automatable control family here. Nightly jobs diff IdP users against HR headcount and auto-ticket orphans; AWS Config rules check MFA enforcement and key rotation; OIDC trust-policy audits reject wildcard `sub` conditions; policy-as-code flags over-broad grants at deploy time. Automation can prepare and execute revocation, but business owners retain the decision on whether access is still required.

*The quarterly review should demonstrate oversight, not discover stale access.*

### 7.3 HKS-CM-02 — Secure change & CI/CD pipeline integrity

**Risk.** Unreviewed change is self-inflicted breach: one misconfigured bucket exposes data instantly, compromised build tooling turns the pipeline itself into the attack vector, leaked secrets grant standing access. The CI/CD pipeline is now the shortest path to production, and the only place a preventive gate touches every change at near-zero marginal cost.

**Control.** Changes to software, infrastructure and procedures follow a controlled lifecycle of authorisation, independent review, automated testing, approval, segregation of duties and rollback capability, with verifiable provenance over build inputs and outputs. Annex A: A.8.25, A.8.28, A.8.29, A.8.31, A.8.32. TSC: CC8.1, CC6.8.

**Implementation.** Git-centric flow: protected main branches, mandatory peer review, CODEOWNERS review required on security-sensitive paths, stale approvals dismissed so a re-run after changes cannot ride an old sign-off, status checks required, bypass permissions restricted. Short-lived federated pipeline credentials via OIDC rather than stored production keys. CI gates: secret scanning, SAST, SCA, dependency review, IaC scanning. Dependency pinning, SBOM generation, artifact signing verified at deploy admission. Environment separation with restricted production write; emergency changes get documented retro-review within 48 hours. NIST's SSDF frames this correctly: high-level practices integrated into whatever SDLC model exists, with the toolset chosen by risk and environment, not an SBOM-as-proof-of-safety claim.

**Evidence.** Branch-protection and ruleset configuration, merge requests with reviewer identities, CI history including failed gates, SBOMs linked to release identifiers, provenance attestations, deployment approvals, emergency-change tickets. The strongest artefact is again a reconciliation: deployments observed in CloudTrail versus merged approved PRs, where unmatched deployments become investigated exceptions.

**Testing.** Auditor samples deployments from the release log and traces each back through review, green pipeline and approval. Negative tests in a non-production pipeline: plant a deliberately leaked secret, vulnerable dependency, insecure IaC rule, self-approved change or unsigned artifact and confirm the expected gate blocks it. Attempt direct production push in a test repo to confirm branch protection. Review the emergency-change rate for abuse.

**Automation.** The pipeline generates its own evidence: every commit yields immutable proof of review, tests and approval. Policy-as-code evaluates rules like "no security group open to 0.0.0.0/0 on port 22" at deploy admission, blocking noncompliant infrastructure before it exists. Automated reconciliation flags out-of-band changes. Auto-generated remediation PRs go to human review; material production changes are never changed silently.

*A gate that samples only pull requests that already passed tests compliance, not completeness. Reconcile deployments against approvals.*

### 7.4 HKS-VM-03 — Vulnerability & configuration management

**Risk.** Exploitation of known vulnerabilities is now the top initial-access vector at 31% of breaches per the DBIR analyses. Insecure defaults, exposed services, vulnerable dependencies and silent configuration drift compound exposure. A programme can also create false assurance by measuring remediation performance without measuring whether the asset population is fully covered.

**Control.** Maintain an asset inventory and configuration baselines; identify vulnerabilities and deviations; prioritise by exploitability and business exposure; remediate within documented risk-based SLAs; prevent unmanaged change from becoming permanent. Annex A: A.8.8, A.8.9, A.8.19, A.5.7. TSC: CC7.1 (detection of configuration-introduced vulnerabilities), supporting CC8.1.

**Implementation.** Inventory is the precondition (A.5.9): cloud workloads, OSes, containers, serverless functions, applications, third-party components. Authenticated weekly scans of all hosts and daily for internet-facing surface. SLAs tier by exploitability, actively-exploited (KEV) fastest then critical/high/medium, enriched with EPSS scores rather than CVSS severity alone; exact day-counts are set by the organisation's own risk acceptance, not copied from any template. Exceptions carry a named owner, rationale, compensating control where appropriate, and an expiry date that fires automatically. Infrastructure lives as version-controlled IaC, scanned before deployment; runtime drift is detected and either reverted or formally accepted.

**Evidence.** Scan findings with first-observed/resolved timestamps, remediation tickets linking finding→fix→verification rescan, SLA attainment metrics, signed exception register with expiries, SBOMs per release, drift-detection results, and an inventory-completeness reconciliation: scanner coverage versus the asset inventory, where a coverage gap is itself a control gap.

**Testing.** Reconcile authoritative assets against scanner coverage. Deploy a deliberately vulnerable test image and confirm detection, ticketing and escalation. Verify a remediation closes a finding only after a follow-up scan. Introduce an out-of-band configuration change in staging and confirm it is detected, attributed, ticketed, and either reverted or formally accepted.

**Automation.** Scanners automate detection; the assurance layer automates everything around them: API-sync findings into ticketing with SLA clocks started at first detection, auto-close on verified rescan, auto-expiring exceptions, blocking of high-risk IaC at plan time. Automated remediation is limited to pre-approved low-risk change models; anything material keeps human approval.

*Coverage is a first-class metric. A high percentage remediated within SLA means nothing if part of the estate is invisible.*

### 7.5 HKS-LM-04 — Centralised logging, monitoring & incident response

**Risk.** Breaches dwell undetected for weeks when nobody watches telemetry, multiplying impact through lateral movement, exfiltration and late-notification penalties. Beyond detection, logs are the substrate for every other control's evidence: without trustworthy logs nothing else in this section can be proved to have operated. Attackers who can delete local logs erase their own trail.

**Control.** Collect security-relevant events from in-scope systems with reliable timestamps and integrity protection; detect meaningful deviations; evaluate, respond to and recover from incidents. Annex A: A.8.15–A.8.17, A.5.24–A.5.26. TSC: CC7.2–CC7.5.

**Implementation.** Define a logging standard covering identity, privileged activity, endpoint, cloud control plane, application, network and backup events. Centralise in a SIEM (Wazuh/ELK at smaller scale); synchronise clocks; separate collection from analysis privileges; store critical logs in a separate access-controlled account with integrity protection such as WORM storage (S3 Object Lock as one cloud example, presented honestly: it prevents alteration of locked object versions but does not prove all logs were collected, nor replace access controls). Retention follows legal, contractual and forensic needs. Detections target privileged-access changes, disabled logging, public exposure, suspicious authentication and unusual transfer. Documented IR plan with roles, severity matrix, escalation paths and comms templates; tabletop exercises twice yearly; the 72-hour GDPR notification clock built into the workflow.

**Evidence.** Log-source coverage matrix, ingestion-health dashboard, integrity-validation results, alert-to-triage-to-case trails with response times, IR plan version history, tabletop records with lessons learned, postmortems, retention exports, detection-rule change history.

**Testing.** Detection canaries, benign decoy actions, verify the full chain from event generation to alert, page, acknowledgement and case creation, run monthly so a silently broken alerting pipeline is caught within weeks rather than at audit. Purple-team exercises using atomic red-team techniques confirm specific alerts fire and pages land. Negative test: attempt to delete or modify protected logs in a test environment and capture the denial. Reconcile high-severity alerts against incident records and log-source coverage against the asset inventory. Targets are organisation-set; no universal MTTD number is claimed.

**Automation.** SOAR playbooks for containment speed (auto-isolate endpoint, revoke sessions) gated behind strong authorisation, rollback paths and human escalation. Collection-health checks, anomaly detection, alert routing, case creation and evidence packaging run continuously, turning the annual evidence pull into a query. A failing health check is an alert, never a silent artefact.

*Logging is the load-bearing wall: the evidence for every other control depends on it.*

### 7.6 HKS-BR-06 — Ransomware-resilient backup, recovery & data protection

**Risk.** Ransomware reached 48% of breaches per the DBIR analyses. Destructive deletion, compromised backup credentials, accidental loss and prolonged outage can all make trustworthy restoration impossible. Unprotected copies create their own exposure: stolen backups leak what production protects. Backups that exist but have never been restored are a hope, not a control.

**Control.** Maintain recoverable, protected copies of critical information and services, including at least one logically or physically separated from the production attack path, supporting approved RTO/RPO objectives and verified through scheduled restoration tests. Confidential data is encrypted in transit and at rest with key administration separated from ordinary data use. Annex A: A.8.13, A.8.24, A.5.29/A.5.30. TSC: Availability criteria A1.2/A1.3, CC9.1, plus C-series confidentiality criteria where selected.

**Implementation.** This is the merged control: Elkorbow's recovery spine with Arebi's cryptography folded in. Encrypted backups using customer-managed keys where risk or contract requires, key rotation enabled, key activity monitored, and administration of keys separated from use of keys through service conditions. Backup administration runs under separate identities with their own MFA, never reachable through production roles. Immutable or retention-protected storage (Object Lock as one layer), complemented by account/region separation and offline copies where justified. Clean recovery procedures and representative test data maintained in advance. Backup jobs monitored for success and for changes to retention configuration. CISA's #StopRansomware guidance points the same direction: offline, encrypted, regularly tested copies.

**Evidence.** Backup policy, job-success and failure history, backup-coverage inventory, immutability and encryption/key-rotation configuration, key-policy reviews, restore runbooks, recovery-test results with measured RTO/RPO, hash checks on restores, access reviews for backup administration, corrective actions raised by failed exercises and their closure.

**Testing.** Scheduled restores using representative systems and data, measuring actual recovery time and data loss against objectives. Clean-room recovery exercises. Negative tests: attempt to modify or delete protected copies during retention as an ordinary production administrator and confirm it fails; attempt backup operations with production credentials to confirm isolation; test encryption enforcement and key-administration separation directly. Record failures and track them to closure.

**Automation.** Schedule backups and restore verification, alert on failed jobs, retention changes or missing sources, monitor encryption and coverage status, generate recovery-evidence packages automatically, and gate incident closure on evidence of successful restoration rather than a green backup job alone. Policy-as-code blocks unencrypted storage creation where the platform supports it.

*Backup existence is not equivalent to recoverability. The assurance question is whether trustworthy services can be restored within approved objectives from copies an attacker cannot easily destroy.*

---

## 8. One control library, one evidence pipeline

The five controls are defined once, in an internal library, and mapped outward to ISO 27001 Annex A, SOC 2 criteria, internal policies, owners and evidence definitions. The same control supports both frameworks; it is never copied into separate documents that drift apart.

The crosswalk is data, not a spreadsheet. Store mappings in machine-readable form (`crosswalk.yaml`) and three deliverables become generated artefacts: the Statement of Applicability produced per clause 6.1.3(c), where every Annex A control either maps to an implemented control or carries a documented exclusion; the SOC 2 Section IV criteria-and-controls matrix; and the gap report when a new framework arrives, computed as a set difference rather than debated in a workshop.

A useful control record carries a fixed schema:

| Field | Purpose |
|---|---|
| Control ID and title | Stable identifier for governance and evidence linkage |
| Risk statement | Connects the control to a defined threat and business impact |
| Control objective and statement | Testable description of the expected risk treatment |
| Owner and status | Accountability and implementation state |
| Framework mappings | Links to Annex A, SOC 2 criteria, internal requirements |
| Evidence definitions | Source, cadence, period, population, retention, assertion |
| Test procedures | Configuration, effectiveness, and population-completeness tests |
| Exceptions | Rationale, compensating controls, owner, approval, expiry |
| Metrics | Management review and continual improvement |

Evidence follows a collect-once-present-many-times model:

1. Approved read-only connectors pull from systems of record: IdP, cloud APIs, repositories, CI/CD, ticketing, HRIS, monitoring.
2. Collectors normalise timestamps and identifiers, record query parameters and record counts, preserve original artefacts, and compute cryptographic hashes.
3. Evidence lands in access-controlled retention storage with a manifest recording collector version, source, period, population definition, collection identity and integrity metadata.
4. Deterministic assertions identify failures immediately instead of filing an artefact silently for later discovery.
5. The same store serves ISO internal audits, SOC 2 sample requests, management review, customer questionnaires and continuous monitoring.

This is what GRC-as-Code means here: not merely scanning infrastructure, but preventing the control library, risk register, SoA and operational reality from drifting apart. Two rules keep it honest. Collectors are read-only, so the evidence system can never become a shadow production path. And a failing assertion is an alert, not a quietly filed artefact awaiting discovery at audit.

---

## 9. AI proposal: the Evidence Sufficiency Reviewer

All three individual reports proposed an AI system for evidence work, and their convergence is itself a finding: working independently they identified the same bottleneck and the same safety shape.

**The bottleneck.** The expensive part of both regimes is not implementing controls, it is proving them continuously. Analysts reviewing hundreds of artefacts ask whether each demonstrates the control operated, for the stated period, over the complete population. The failure modes are mundane and consistent: out-of-period artefacts, policies filed against operating-effectiveness tests, undisclosed filters, screenshots of screenshots, record counts contradicting stated populations, artefacts attached to the wrong control. None require hard judgement; all are numerous and performed under deadline pressure, exactly where humans err consistently and a well-scoped model performs well.

**Deterministic checks come first.** Dates, hashes, control identifiers, record counts and population metadata are checked by comparison operators before any model call. Roughly half of real defects fall here at zero inference cost. Never ask a model what a comparison operator can answer.

**Then LLM triage, grounded and constrained.** Artefacts passing pre-checks are evaluated by a tenant-isolated model reasoning only over supplied control text: the control narrative, the mapped TSC criterion, the mapped Annex A wording, retrieved rather than recalled. Output is constrained JSON: verdict SUFFICIENT / INSUFFICIENT / UNCERTAIN, coded reasons, and exact quotations from the artefact supporting the verdict.

**Asymmetric authority is the core safety design.** The model may flag, never approve. Only INSUFFICIENT and UNCERTAIN act, by adding items to a human review queue; a SUFFICIENT verdict changes nothing automatically. The system can create work but cannot remove it, so a hallucinated approval has no path to becoming accepted compliance, and a successful prompt injection produces a no-op. Mapped briefly onto the OWASP Top 10 for LLM Applications: prompt injection addressed structurally (untrusted-content delimiters, schema-constrained output), excessive agency removed entirely, sensitive-information disclosure limited by tenant isolation, overreliance countered by mandatory human decision.

**Evidence is untrusted input.** Logs, commit messages, ticket bodies and policy text may contain injected instructions; the reviewer treats artefact content accordingly and reasons only over retrieved control text plus the artefact under evaluation.

**The AI system must itself be auditable.** Model ID, prompt version, retrieved-context hashes, raw outputs, human dispositions and exceptions are logged end to end. An unevidenced control sitting inside a framework built on evidence would be an embarrassing way to fail. The agent is registered in the AI system inventory with purpose, owner, data flow and retirement position, aligned to the NIST AI RMF (the evaluation set below is its Measure function) and mappable onto ISO/IEC 42001 clauses.

**Evaluation before prompting.** Build a labelled set of ~200 artefacts, half deliberately defective with defects drawn from real audit findings, before writing the prompt, so tuning cannot contaminate the test. Primary metric: recall on defective artefacts ≥0.95, because missing a bad artefact costs a Section IV exception. Secondary: precision ≥0.70, a human-factors floor rather than a statistical nicety, since below roughly 0.5 the queue becomes noise and analysts rubber-stamp it into worthlessness. An adversarial suite injects payloads through log lines, commit messages and ticket bodies, with a zero-behaviour-change requirement. Time saved is explicitly not a metric: judging the tool on shrinking human review runs the incentive gradient straight through the asymmetry guardrail.

**Phased pilot.** One cloud account, one identity source, one CI platform, a few controls. Phase 1 build (weeks 1–3): evaluation set live, deterministic pre-checks running. Phase 2 shadow (weeks 4–7): verdicts logged but hidden, scored against independent analyst decisions. Phase 3 assist (weeks 8–12): flags surfaced in the queue, success measured as defects found before the auditor finds them. Phase 4 decide (week 13): keep, tune or stop on evidence, with a kill criterion if recall or injection-resistance targets are missed. First release classifies evidence and opens review tasks; it never modifies production.

---

## 10. Points we disagreed on, and how we resolved them

Recorded because the brief grades reasoning, not just conclusions:

1. **Fifth control.** Encryption vs backup/recovery vs awareness. Resolved on DBIR attack data toward backup & recovery, with encryption folded into HKS-BR-06 and awareness kept alongside; full reasoning in section 7.1.
2. **"80% overlap" between frameworks.** Rejected as a claim to repeat. It is unfalsifiable as usually stated and measures the wrong thing: control activities overlap heavily, the evidence workload does not.
3. **Type II period norms.** Vendor sources imply fixed rules ("six months minimum", "always twelve"). Resolved to Elkorbow's formulation: the period is agreed between management and the CPA firm; ranges are practitioner convention, not rule.
4. **Asset inventory: "control zero" or a control?** Held open deliberately. Our position treats inventory as a precondition with completeness enforced inside each control's testing through reconciliations, rather than standing it up as a standalone sixth control. Counter-arguments welcome in review.
5. **Immutable evidence stores vs erasure rights.** Compliance-mode Object Lock means nobody deletes before expiry, including in response to a legitimate erasure request touching evidence containing personal data. Genuine tension between evidential integrity and data-protection law; unresolved, flagged for discussion.
6. **Fixed SLA numbers** (72-hour patching, 24-hour revocation). Presented throughout as design examples; each organisation sets its own risk-based values. A number quoted as a standard requirement is a hallmark of copy-paste compliance.
7. **No cost figures retained.** Earlier drafts carried audit-day rates and Type II price ranges from vendor sources. They vary widely by scope and market and were dropped rather than laundered into false precision; obtain quotes from actual firms.

---

## 11. Limitations

Stated plainly, jointly:

- This is a design and research deliverable, not proof of deployment. No live HKS systems, audit samples, risk registers or production configurations were examined; the most valuable next step is building controls 1 and 3 in a sandbox account to see what survives contact with reality.
- AWS/GitHub implementation examples are illustrative patterns; managed-rule catalogues, API behaviour and service names change and must be re-checked against current catalogues at implementation time.
- The DBIR figures derive from published secondary-source analyses of the Verizon 2026 report, relied on directionally rather than precisely.
- Amendment 1:2024 wording is known from quotations of the amendment, not the amendment text itself.
- Framework mappings are illustrative pending real ISMS scope, selected SOC 2 criteria, system description and auditor interpretation.
- Nothing here is legal advice; notification deadlines, privacy obligations and retention requirements must be confirmed per jurisdiction and organisation.
- The claim that no successor TSC revision exists is the weakest class of claim in this document and should be rechecked against AICPA publications before client use.

---

## Sources

**Primary standards pack** (read directly from the programme resource pack):

1. ISO/IEC 27001:2022 (third edition) — Requirements
2. ISO/IEC 27002:2022 — Information security controls
3. AICPA TSP section 100 — 2017 Trust Services Criteria with Revised Points of Focus (2022)
4. AICPA DC section 200 — Description Criteria for a SOC 2 Report
5. AICPA SOC 2 Guide (October 2022)

**Public sources** (verified August 2026):

- ISO — ISO/IEC 27001:2022/Amd 1:2024 catalogue entry (iso.org/standard/88435.html); iso.org/standard/27001
- Verizon — 2026 Data Breach Investigations Report and published analyses thereof (Help Net Security, May 2026; Push Security review)
- NIST — SSDF (SP 800-218); Cybersecurity Framework 2.0; AI Risk Management Framework
- CISA — Known Exploited Vulnerabilities catalogue; #StopRansomware Guide
- FIDO Alliance — passkey/WebAuthn phishing-resistance material
- AWS — Audit Manager SOC 2 framework docs; Config conformance packs; S3 Object Lock documentation
- OWASP — Top 10 for LLM Applications
- LRQA — ISO 27001 Stage 1/Stage 2 FAQ
- IT Governance / GRCSolutions — ISO 27001 certification cost and cycle guidance

*Built from the individual reports of Ahmed Arebi, Abo Alqasem Elkorbow and Marwan Elamami. Control identifiers prefixed HKS- are illustrative and defined only within this document.*

---

## Conclusion

ISO/IEC 27001 and SOC 2 are complementary assurance approaches, not interchangeable ones. The strategy that holds up under both is one accountable, risk-based internal control library, mapped outward to each framework and operated through normal engineering and governance processes, with evidence collected continuously from systems of record.

The five controls here give that library a practical foundation. Their value, though, sits entirely in execution: ownership that is real, testing that includes failure, evidence pulled from systems of record rather than screenshotted, populations complete enough to trust, and improvement that closes the loop. Compliance is demonstrated operation, not document production.
