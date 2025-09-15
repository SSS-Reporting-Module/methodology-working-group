# Step 4: Execute ETL Pipeline and Perform Data Quality Assessment

**Objective**: Transform and load compiled public data into a centralized database via ETL processes, then rigorously evaluate its quality against GHG Protocol Scope 2 criteria (e.g., accuracy, completeness, timeliness, granularity, and usability as per the 2015 Guidance amendments and 2025 TWG updates emphasizing integrity and impact). This step ensures data robustness for SSS emissions calculations, identifying issues like staleness or biases early to support Scope 2 revisions (e.g., market-based method alignment with decarbonization actions post-August 2025 ISB approval for consultations).

**Key Activities** (Hybrid: Automated ETL First, Manual Assessment Refined by Metric/Pair):

* **ETL Execution**: Use pre-built scripts (e.g., Python Airflow) to extract from compiled sources (Step 3), transform (e.g., standardize units like gCO2e/kWh, handle missing values via imputation or flagging), and load into the DB (e.g., PostgreSQL with schema for pairs/metrics). Automate validation checks (e.g., sum percentages=100% for mixes; ratios <1 for EAC coverage).
* **Quality Scoring Framework**: Apply a multi-criteria rubric aligned with GHG Protocol Scope 2 Quality Criteria (e.g., temporal/deliverability matching from 2025 TWG proposals):
  * **Granularity**: Score supplier-specific vs. aggregated (e.g., hourly data > annual; deduct for proxies).
  * **Accuracy/Timeliness**: Verify against benchmarks (e.g., cross-check resource mix with IEA 2025 data; flag pre-2024 vintages as low-quality per RED III updates).
  * **Completeness/Usability**: Assess coverage (>70% threshold) and format (e.g., APIs score higher than PDFs); link to SSS (e.g., RPS-tied EACs under Non-Bypassable Charges).
  * Multi-Angle Verification: For each metric, use at least three methods (e.g., mathematical: sensitivity analysis ±10%; external: compare to Ember 2025 reviews; logical: challenge biases like overreported renewables).

**Pair-Level Review**: Query DB for each qualifying pair; assign scores (e.g., 1-5 scale per criterion, overall >3.5 = usable); document remediations (e.g., fallback to location-based if market data fails integrity).

**Automation & Iteration**: Schedule quarterly ETL refreshes (e.g., post-IEA September 2025 releases); flag uncertainties (e.g., ISO-GHG harmonization impacts pending mid-2026 finalization).

**Output**: Populated DB with quality-annotated data; per-pair quality reports (e.g., CSV with scores, flags, and audit trails); aggregated dashboard (e.g., heat maps of gaps by region/supplier) for Phase 3 inputs.

**Efficiency Notes**: Leverage DB queries to reduce manual effort (e.g., SQL batch scoring); assign regional specialists for reviews; integrate ISO 2025 partnership standards for unified quality benchmarks; re-assess post-consultation (late 2025) for alignment with finalized Scope 2 text.
