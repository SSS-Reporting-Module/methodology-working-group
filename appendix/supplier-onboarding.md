# Outline of Instructions for Collecting Supplier Data in the Granular Registry SSS Reporting Platform

This outline delineates a phased approach to supplier data collection, meticulously designed for integration into a software wizard. The structure draws from cross-verified best practices in GHG Protocol Scope 2 Guidance (e.g., supplier-specific emission factors, data hierarchies, and quality criteria for contractual instruments like RECs), EPA market-based accounting protocols (emphasizing REC retirement verification and utility reporting checklists), CRS methodologies for standard delivery renewable energy accounting (focusing on supplier allocation and data requirements), and industry insights on onboarding challenges (e.g., data quality gaps, traceability issues, supplier reluctance, regulatory variations, double-counting risks, cost burdens, and privacy concerns). It also incorporates software wizard design principles from energy compliance platforms (e.g., phased user flows in EnergyCAP and VelocityEHS for automated tracking, monitoring, and reporting) and ESG/AI-driven tools (e.g., IBM Envizi for Scope 1-3 automation, reducing reporting time by up to 73% via AI-population).

The wizard architecture assumes a modular, user-guided interface with progress tracking (e.g., "1/5 Completed"), conditional branching (e.g., based on supplier type: monopoly utility vs. competitive supplier), real-time validation (e.g., API checks against registries like PJM-GATS), and fallback options for incomplete data (e.g., proxies from public sources like EEI or Ember). To address uncertainties: (1) Regulatory flux (e.g., post-2025 GHG Protocol updates may refine SSS criteria, potentially invalidating current hierarchies—mitigated by annual wizard updates); (2) Supplier variability (e.g., small utilities lack API access—handled via manual uploads with AI-assisted parsing); (3) Double-counting pitfalls (e.g., REC arbitrage decouples attributes—countered by chain-of-custody attestations); (4) Privacy risks (e.g., GDPR compliance—ensured via anonymized data handling and consent modules). Alternative viewpoints scrutinized: Purely automated wizards may overlook nuanced policy interactions (e.g., subsidies in SSS exclusions), so human review gates are embedded; conversely, over-reliance on manual steps could inflate costs (estimated 20-30% burden per supplier, per CRS challenges), balanced by AI efficiencies.

Phases are sequenced to minimize drop-off (e.g., early eligibility checks), with built-in education (tooltips/videos on SSS concepts) and scalability (e.g., batch uploads for large suppliers). Triple-verification embedded: Each phase requires multi-source corroboration (e.g., supplier input + registry API + public data); mathematical validations (e.g., pro-rata share calculations via formulas like Claimable_REC_MWh = (SSS_REC_MWh / Retail_Sales_MWh) × Customer_Load); and external cross-checks (e.g., against EPA eGRID or AIB residuals). Potential oversights: Hourly data feasibility (only ~50% registries support timestamps—flagged with confidence scores); global inconsistencies (e.g., EU GOs vs. US RECs—addressed via jurisdiction-specific branches). Reconsidered from scratch: If wizard prioritizes compliance over usability, adoption falls; thus, emphasize value (e.g., "Unlock SSS claims for your customers").

## Phase 1: Registration and Eligibility Screening
**Objective:** Establish supplier identity, confirm SSS relevance, and gather baseline info to filter ineligible participants (e.g., non-utility entities). This phase mitigates early reluctance by simplifying entry while verifying foundational compliance (e.g., against GHG Protocol market boundaries).

**Wizard Flow:** Guided form with auto-population from public registries (e.g., EEI database lookup); conditional questions based on responses (e.g., if "competitive market," branch to RPS details).

**Checklist:**
- [ ] Provide basic entity details: Legal name, jurisdiction (e.g., US state/ISO, EU Member State), supplier type (monopoly, competitive, government-owned), and contact info (verified via email/SMS OTP).
- [ ] Upload proof of operations: Utility license, FERC Form 1 (US), or ENTSO-E disclosure (EU); cross-check against public sources (e.g., EPA eGRID for US utilities).
- [ ] Confirm SSS applicability: Select categories (regulated cost recovery, non-bypassable charges, customer funding) with examples (e.g., RPS compliance, ZEC programs); validate against decision trees (e.g., "Is resource part of default service?").
- [ ] Disclose market boundaries: Specify balancing authority/ISO or franchise area; auto-validate via API (e.g., EIA data query).
- [ ] Acknowledge data privacy: Consent to GDPR/CSRD-compliant handling; disclose data use (e.g., for pro-rata allocation only).

**Attestation:** Digital signature: "I attest that the provided information accurately reflects our operations as an SSS provider, meeting GHG Protocol Scope 2 eligibility (e.g., traceable financial relationships). False statements may invalidate claims. [Date/Timestamp]"



## Phase 2: Data Submission and Upload
**Objective:** Collect core SSS datasets (e.g., REC retirements, emission factors, load/generation profiles) with structured formats to enable pro-rata allocation. This phase tackles data quality gaps by prioritizing hierarchies (e.g., API > CSV) and providing proxies for incomplete submissions.

**Wizard Flow:** Multi-step uploader with progress bars; AI-assisted parsing (e.g., validate CSV schema); fallbacks for non-digital suppliers (e.g., PDF OCR).

**Checklist:**
- [ ] Submit retail sales volumes: Annual MWh from sources like EIA Form 861 (US) or Eurostat; include hourly profiles if available (e.g., for hourly matching).
- [ ] Provide RPS/CES compliance data: Statutory targets, actual REC retirements by technology tier; document obligations vs. actuals (e.g., gap calculations).
- [ ] Detail non-RPS zero-carbon resources: MWh from legacy hydro/nuclear; disclose public ownership/subsidies with decision tree validation (e.g., "Is resource taxpayer-funded?").
- [ ] Upload SSEF and CFE shares: Published factors (e.g., EEI/Climate Registry); break down by technology (e.g., Ember grid mix %).
- [ ] Handle arbitraged/unbundled RECs: Chain-of-custody docs (sales proofs, replacement contracts); flag timestamp gaps with proxies (e.g., facility averages).
- [ ] Optional hourly extensions: Time-stamped data from registries (e.g., EIA Hourly Grid Monitor); if absent, disclose limitations per Scope 2 criteria.

**Attestation:** Digital signature: "I attest that submitted data is accurate, sourced from credible origins (e.g., meeting Scope 2 Quality Criteria: ownership, no double-counting, market boundaries), and reflects SSS resources without shuffling. Supporting docs are verifiable. [Date/Timestamp]"



## Phase 3: Verification and Quality Assurance
**Objective:** Cross-validate submitted data against external sources to ensure integrity, preventing misallocation or fraud. This phase addresses challenges like integrity risks and regulatory variations through multi-method checks.

**Wizard Flow:** Automated backend processing with user notifications (e.g., "Verification in Progress—85% Complete"); manual review flags for anomalies (e.g., volumes exceeding RPS).

**Checklist:**
- [ ] Internal consistency: Validate calculations (e.g., SSS_REC_MWh = RPS_retired + Public_zero-carbon - External_sales; use math libs for pro-rata: Claimable = (SSS / Retail) × Load).
- [ ] External cross-checks: API queries to registries (e.g., M-RETS compliance module); match against public data (e.g., EEI CFE % by technology).
- [ ] Quality criteria alignment: Confirm Scope 2 standards (e.g., exclusivity, temporal matching); flag failures (e.g., non-deliverable imports).
- [ ] Anomaly detection: Scan for discrepancies (e.g., arbitrage without docs); apply confidence scores (High: API-confirmed; Low: Screenshots).
- [ ] Third-party audit option: For high-risk submissions (e.g., >10% CFE claim), trigger external review (e.g., Deloitte integration).
- [ ] Privacy/security scan: Ensure anonymization; comply with GDPR (e.g., data minimization).

**Attestation:** N/A (system-generated); supplier re-attests if revisions needed: "I confirm corrections address flagged issues and maintain data integrity per GHG Protocol. [Date/Timestamp]"



## Phase 4: Attestation, Finalization, and Reporting
**Objective:** Secure formal commitments, generate outputs (e.g., pro-rata shares), and enable customer claims. This phase resolves cooperation barriers by emphasizing value (e.g., streamlined reporting).

**Wizard Flow:** Review summary dashboard; e-signature integration; export reports (e.g., PDF/CSV for SSS claims).

**Checklist:**
- [ ] Review aggregated data: Display calculated outputs (e.g., CFE % by technology, SSEF); allow edits with re-verification.
- [ ] Disclose limitations: Flag uncertainties (e.g., "Medium confidence due to annual proxies"); include policy context (e.g., subsidies).
- [ ] Generate reports: Pro-rata allocations, emission factors; integrate with customer portals.
- [ ] Post-submission actions: Schedule annual refresh; opt-in for updates (e.g., Protocol changes).
- [ ] Feedback loop: Collect supplier input on process for iterations.

**Attestation:** Comprehensive digital signature: "Under penalty of perjury, I attest that all data complies with GHG Protocol Scope 2 (e.g., Quality Criteria, no shuffling), is free from double-counting, and enables accurate SSS claims. I authorize third-party audits. [Date/Timestamp]"

