# Standard Supplier Service (SSS) Methodology — Verified-first with Public Data Fallbacks

## 1) Scope

- Purpose: Calculate (i) SSS-retired zero-carbon attributes (MWh) and (ii) supplier-specific emission factor (SSEF, kg CO₂e/MWh) for market-based Scope 2.
- Priority: Utility-submitted, verifiable data. When unavailable, populate the same schema using public/third-party sources with graded confidence.
- Granularity: Annual required; hourly optional where time-stamped data exists.

## 2) Required Data Schema (single source of truth)

- context:
  - reporting_year
  - jurisdiction / market_region (BA/ISO, state/province, LSE legal entity)
  - tracking_system(s) (e.g., WREGIS, PJM-GATS, AIB)
- retail_sales:
  - total_mwh
  - by_customer_class (optional)
- rec_retirements_for_sss:
  - records: [{ certificate_id|batch_id, technology, vintage_year, retirement_date, mwh, program (RPS/CES/voluntary), allocation: "SSS"|"non-SSS" }]
  - external_sales_mwh (to subtract)
- non_rps_zero_carbon_for_sss:
  - records: [{ resource_type (large_hydro|nuclear|public hydro etc.), mwh, proof (program/ZEC/contract/ref) }]
- generation_mix:
  - owned/contracted/purchases by fuel/tech with mwh
- emissions:
  - plant_or_fuel_level_intensities: [{ fuel_or_unit, kgco2e_per_mwh, source }]
  - supplier_published_ssef (if provided) with documentation
- compliance:
  - rps_ces_obligation_mwh_or_percent
  - filings/reports (refs and dates)
- provenance_and_quality:
  - sources: [{field, source_name, url_or_ref, retrieved_at}]
  - confidence_score (0–1)
  - notes_on_banking_and_deadlines

Example JSON (software-facing):
```json
{
  "context": {"reporting_year": 2024, "market_region": "CAISO", "lse": "PG&E", "tracking_systems": ["WREGIS"]},
  "retail_sales": {"total_mwh": 80000000},
  "rec_retirements_for_sss": {"records": [], "external_sales_mwh": 0},
  "non_rps_zero_carbon_for_sss": {"records": []},
  "generation_mix": {"owned": [], "contracted": [], "purchases": []},
  "emissions": {"plant_or_fuel_level_intensities": [], "supplier_published_ssef": null},
  "compliance": {"rps_ces_obligation": {"percent": 44}},
  "provenance_and_quality": {"sources": [], "confidence_score": 0.0, "notes": ""}
}
```

## 3) Core Calculations (common to verified and public paths)

- SSS_REC_MWh = RPS/CES retired for SSS (post-vintage rules) + Non-RPS zero-carbon SSS MWh − Externally sold RECs MWh
- SSEF (if not supplier-published):
  1) Start with generation_mix (owned + contracted + net purchases)
  2) Subtract zero-carbon MWh matched to SSS retirements
  3) Apply fuel-specific CO₂e intensities to residual fossil MWh
  4) SSEF = total_kgCO2e / retail_sales.total_mwh
- Pro-rata allocation for a customer load L_customer:
  - Claimable_REC_MWh = (SSS_REC_MWh / retail_sales.total_mwh) × L_customer
  - Market-based Scope 2 = L_customer × SSEF

## 4) Primary Path — Verified Utility Data

- Validate: format completeness, tracking-system checks, compliance cross-checks.
- Vintage banking: ensure retirements meet program rules and deadlines; include only allowable banked vintages.
- Use supplier_published_ssef if attested and consistent with verified retirements; otherwise compute via Core Calculations.
- QA/QC: duplication checks between compliance and voluntary; versioning.

## 5) Fallback Path — Public Data ETL (same schema, graded confidence)

Populate each schema field with this priority:

- retail_sales:
  - Utility submission → regulatory filings (e.g., EIA 861, Eurostat) → utility annual reports → modeled estimate (flag high-uncertainty)
- rec_retirements_for_sss:
  - Tracking-system compliance reports (WREGIS, GATS, AIB) → regulator RPS/CES reports → utility disclosures (PCL, EEI) → infer from obligation × observed mix; subtract known external sales if disclosed
- non_rps_zero_carbon_for_sss:
  - Regulated/public asset disclosures (IRPs, FERC Form 1, PCL notes, ZEC dockets) → utility annual reports → national stats (ownership-tagged hydro/nuclear)
- generation_mix:
  - Supplier disclosures (PCL, EEI, sustainability reports) → national stats with ownership/purchase annotations → bottom-up reconstruction from plant-level datasets (eGRID, EU ETS, PRTR)
- emissions:
  - Supplier-published EF → residual-mix EF (AIB/RE-DISS) → fuel-specific factors (eGRID, national inventories) applied to reconstructed mix
- compliance:
  - Regulator RPS/CES obligation filings → DSIRE/policy databases → statute implied percentages
- provenance_and_quality:
  - Always record sources, retrieval dates, confidence; downgrade confidence when imputing.

Decision rule: if any field remains missing after the chain, set conservative defaults (e.g., regional average EF, zero additional zero-carbon beyond evidenced compliance) and mark high-uncertainty.

## 6) Hourly Extension (optional)

- Use time-stamped retirements and hourly residual mix where available; otherwise disclose annual-to-hourly approximations and uncertainty.

## 7) Region Annexes

- Keep concise annexes documenting local quirks (e.g., banking limits, retirement deadlines, disclosure formats) that affect Steps 4–5.

## 8) Outputs

- SSS bundle: { SSS_REC_MWh, SSEF, Claimable_REC_MWh for each customer, provenance, confidence }
- Attach calculation notebook and source package; version-stamp.


