# Global Public Data Assessment

## Introduction

This methodology document outlines a structured, six-step process for conducting a comprehensive global assessment of publicly available data to support Supplier-Specific Scope 2 (SSS) emissions reporting under the GHG Protocol. Developed for the Granular Registry SSS Reporting platform, this process evaluates data availability, quality, and usability to inform revisions to Scope 2 Guidance, particularly enhancements to supplier-specific methods within location-based and market-based accounting frameworks.

The assessment aligns with ongoing GHG Protocol updates as of September 15, 2025, including the Independent Standards Board (ISB) approval for public consultation on market- and location-based revisions in August 2025, the ISO-GHG Protocol strategic partnership announced September 9, 2025, for harmonized standards, and Technical Working Group (TWG) progress on temporal matching, deliverability, and consequential impacts. Objectives include identifying data gaps, recommending improvements for SSS adoption, and ensuring alignment with emerging requirements, such as ISO 14064 harmonization and granular EAC tracking.

The process emphasizes public data sources, multi-angle verification (e.g., cross-checking with IEA, EIA, ENTSO-E), and efficiency through ETL pipelines. It covers geographic scopes, prioritizing high-emission regions (e.g., EU, US, China), and assumes a 6-month timeline starting from September 15, 2025, with deliverables for Secretariat discussions by March 2026.

## Overall Process Overview

Each step builds upon the previous one, incorporating verification tools (e.g., web searches, code execution for calculations) and addressing uncertainties through sensitivity analysis and alternative viewpoints.

{% stepper %}
{% step %}
## Compile List of Supplier-Region Pairs

Establish a foundational inventory of unique supplier-region pairs to define the assessment's scope, ensuring comprehensive global coverage while prioritizing regions with high emissions or data potential.
{% endstep %}

{% step %}
## Assign SSS Resource Categories

Qualify pairs for SSS categories (Regulated Cost Recovery, Non-Bypassable Charges, Customer Funding) to filter for relevant data compilation, ensuring focus on viable SSS pathways per Scope 2 TWG proposals.
{% endstep %}

{% step %}
## Compile Public Data Sources for ETL (Resource Mix, EAC Retirements, Sales Volume)

Gather structured public data for qualifying pairs to enable ETL, focusing on SSS-tied metrics for granular Scope 2 calculations.
{% endstep %}

{% step %}
## Execute ETL Pipeline and Perform Data Quality Assessment

Ingest data into a database and assess quality per Scope 2 criteria to ensure usability for SSS reporting.
{% endstep %}

{% step %}
## Conduct Gap Analysis and Formulate Recommendations

Identify gaps and recommend improvements to advance SSS in Scope 2 revisions.
{% endstep %}

{% step %}
## Synthesize Findings into Final Report

Deliver synthesized insights for GHG Protocol Scope 2 updates.
{% endstep %}
{% endstepper %}

