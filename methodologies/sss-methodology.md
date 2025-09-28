# Methodology for Standard Supply Service (SSS) Reporting in the Granular Registry

## 1. Introduction

The Granular Registry SSS Reporting platform provides utilities (suppliers) and their customers with a standardized, verifiable process for identifying, allocating, and claiming Standard Supply Service (SSS) resources in alignment with the draft Greenhouse Gas (GHG) Protocol Scope 2 Guidance updates (as of September 2025, following the March-June 2025 Technical Working Group (TWG) drafts, with public consultation approved in August 2025 and finalization anticipated by mid-2026). SSS refers to electricity supplied through a traceable, mandated financial relationship, such as regulated cost recovery, non-bypassable charges (e.g., for Renewable Portfolio Standards (RPS) or Clean Energy Standards (CES)), or publicly/taxpayer-funded resources, delivered by default without voluntary action. This methodology ensures prevention of resource shuffling, double-counting, and misalignment with voluntary procurement, while supporting both annual and hourly market-based (MB) Scope 2 accounting.

The platform follows a unified process for data collection and analysis, with branching deliverable options to accommodate varying data availability and user needs. This includes annual reports for basic compliance and hourly options for advanced temporal matching. Where actual hourly meter data is unavailable from suppliers, hourly proxy data (e.g., from public sources like U.S. Energy Information Administration (EIA) hourly grid monitor data for regions such as ERCOT, including wind generation profiles and load shapes) may be used to estimate CFE shapes and customer allocations, providing a feasible approximation for carbon accounting purposes. Proxies are not issued as formal Granular Certificates (GCs) in the registry but serve as supplementary deliverables (e.g., estimated hourly profiles) to support planning, with disclosures on limitations (e.g., potential inaccuracies in real-time dispatch or curtailment). All processes adhere to Scope 2 Quality Criteria, including EAC retirement, deliverability, and no double-claiming.

## 2. Data Collection from Suppliers

Suppliers (e.g., utilities, load-serving entities) submit data via a secure portal or API, with validation against public sources (e.g., EEI, Ember, regulatory filings) for accuracy. The process collects comprehensive data upfront, enabling flexibility in deliverables.

- **Supplier Portfolio Inventory**: List of all generators, facilities, contracts, and purchases, including:
  - Resource identifiers (e.g., plant name, EIA ID, location).
  - Fuel type/technology (e.g., hydro, nuclear, solar, fossil).
  - Ownership structure (e.g., monopoly, public/government-owned, merchant).
  - Funding mechanisms (e.g., regulated cost recovery via Integrated Resource Plan (IRP), non-bypassable charges for RPS/CES, taxpayer subsidies).
  - Commissioning/recommissioning dates.
  - Associated Energy Attribute Certificates (EACs)/Renewable Energy Certificates (RECs) or equivalents, including retirement status and tracking system details (e.g., M-RETS, PJM-GATS).
- **Load and Sales Data**: Aggregate retail sales volume (MWh) served by SSS, segmented by product (e.g., default service) and optionally by rate class/customer type. Include customer-specific load profiles where available.
- **Generation and Meter Data**: Annual and (preferably) hourly/time-stamped generation output (MWh) per resource, including imports/exports. If hourly meter data is not shared, flag for proxy use.
- **Emissions Data**: Resource-specific emission factors (e.g., CO₂e/MWh from Continuous Emissions Monitoring Systems (CEMS), eGRID, or fuel defaults), including CH₄ and N₂O where required.
- **Attestations and Documentation**: Supplier attestations confirming no double-counting, compliance with Scope 2 criteria, and exclusions (e.g., green tariffs funded solely by subscribers).
- **Customer Metadata**: Anonymized load profiles (utility-wide or class-specific) and product enrollment data to enable pro-rata allocation.

Data is collected annually or as updated (e.g., quarterly for dynamic markets), with supplier consent for sharing aggregated insights. Fallback to public proxies (e.g., EEI supplier mixes, regulatory reports, or EIA hourly data for estimates) if direct submission is incomplete, flagged with uncertainty disclosures.

## 3. Analysis Process

Submitted data is analyzed to classify and validate SSS resources, ensuring alignment with GHG Protocol decision trees and quality criteria.

### 3.1 Resource Classification
- Apply SSS Designation Decision Trees to each resource:
  - **Monopoly/Regulated Cost Recovery Tree**: Checks if part of default service, IRP, or excluded as subscriber-funded (e.g., green tariffs without cost-shifting).
  - **Policy Mandates/Compliance Tree**: Evaluates participation in RPS/CES, certificate retirement due to subsidies, or non-bypassable charges (e.g., nuclear ZECs).
  - **Public Ownership/Funding Tree**: Assesses government ownership, taxpayer funding within deliverable boundaries, and exclusions (e.g., competitive tenders without differential support).
- Exclusions: Cross-border ownership (unless tied to local rates), subsidies without EAC action, or resources exceeding load (exportable for voluntary claims).
- Validation: Cross-check against public data (e.g., EPA eGRID for ownership, LBNL RPS reports for compliance) and supplier attestations. Flag discrepancies for audit.

### 3.2 Data Quality and Verification
- Hierarchy: EAC retirement > Supplier attestation > Third-party registry proxy (including hourly proxies where applicable).
- Checks: Ensure deliverability (e.g., within balancing authority), no double-counting (via tracking systems), and temporal alignment (especially for hourly proxies).
- Uncertainties: Document gaps (e.g., missing hourly data defaults to proxies like EIA ERCOT wind/load shapes, with potential limitations in precision for carbon accounting) and alternatives (e.g., resource age fallback if no credible claim).

## 4. Calculations

Calculations derive pro-rata shares, emission factors, and residuals, following the Guidance's order of operations (SSS first, then voluntary). Proxies are applied where needed for hourly estimates.

### 4.1 Pro-Rata SSS CFE Allocation
- Formula: For customer load \( L_{customer} \), share = \( \frac{L_{customer}}{L_{total,SSS}} \times CFE_{SSS} \), where \( CFE_{SSS} \) is zero-emission MWh from classified resources.
- Annual: Use totals; e.g., 10% load share claims 10% annual CFE.
- Hourly: Time-specific; \( CFE_{customer,h} = \frac{L_{customer,h}}{L_{total,h}} \times CFE_{SSS,h} \), accounting for curtailment/imports. If no actual data, apply proxies (e.g., scale SSS wind % by EIA hourly ERCOT wind profiles).

### 4.2 Supplier-Specific Emission Factor (SSEF)
- Bundled: \( SSEF = \frac{\sum Emissions_{SSS}}{\sum L_{total,SSS}} \) (includes CFE at 0 emissions).
- Separated (CFE Removed): Fossil residual = \( \frac{\sum Emissions_{fossil,SSS}}{\sum L_{total,SSS}} \), using fossil-average or coal defaults for unspecified.
- Hourly: Time-matched versions, with proxies for shapes if needed.

### 4.3 Residual Mix
- Supplier-specific fossil-only (SSS CFE excluded); broader grid residuals not used absent claims.

## 5. Deliverables to Users

Deliverables branch based on data availability and user selection:
- **Annual Report**: Downloadable PDF/CSV with CFE percentages, pro-rata volumes, bundled/separated SSEFs, and residuals. Suitable for basic reporting.
- **Hourly Opt-In with Meter Data**: Subaccount in Granular Registry showing hourly load, allocated GCs (issued from SSS resources, retired in underlying registries), CFE profiles by resource type (e.g., filter nuclear). Includes insights opt-in (CFE scores, matching visualizations). Exports: Raw CSVs (8,760 rows: load, CFE MWh per resource, SSEF/residual per hour).
- **Hourly Proxies (If No Meter Data)**: Supplementary deliverable (e.g., estimated hourly profiles via EIA/ERCOT data for wind/load shapes), as CSV or dashboard view. Not formal GCs, but usable for planning/approximate accounting, with caveats on accuracy.

All deliverables include disclosures (e.g., uncertainties, exclusions) and audit trails.

## 6. Claiming in Scope 2 Reporting

Users incorporate deliverables into MB Scope 2 inventories per Guidance, with choices based on goals (rules still evolving through 2025 consultation). At the highest level, customers decide if pursuing zero Scope 2 via voluntary REC procurement:
- **If Not Pursuing Zero**: Download the annual report (or hourly equivalent) and claim the bundled SSEF for their SSS load in MB inventory. This reflects the standard product mix and is simpler for non-advanced reporters.
- **If Pursuing Zero**: Claim pro-rata CFE (via GCs where available) as a foundation, applying fossil residual to the remainder; stack voluntary procurement for gaps. Use GC subaccount for hourly strategies, or proxies for estimates if no meter data.

- **Order of Operations**: Claim SSS pro-rata CFE first (via GCs/RECs), apply fossil residual to remainder; stack voluntary for unmet load.
- **Annual Claims**: Use pro-rata CFE MWh to reduce emissions (e.g., 500 MWh CFE at 0 kg CO₂e); apply SSEF/residual to balance for total MB emissions.
- **Hourly Claims**: Match GCs/proxies to load hours for 24/7 CFE; use time-matched residual for gaps. Substantiate with Registry exports/attestations.
- **Reporting**: Disclose SSS relationships, policies (e.g., subsidies), and stackability in inventories (e.g., "30% CFE from SSS, 70% voluntary"). Cannot achieve zero MB via bundled SSEF alone.
- **Verification**: Retire GCs/RECs in Registry; align with deliverability (e.g., balancing authority).

This methodology is subject to updates post-2026 Guidance finalization.