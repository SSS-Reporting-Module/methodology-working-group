# What are Residual Mix Types?

As a key component of the Granular Registry's Standard Supply Service (SSS) reporting platform, residual mixes play a crucial role in ensuring accurate and transparent Scope 2 GHG emissions accounting. Our methodology draws on established frameworks, such as those from the Center for Resource Solutions (CRS), to allocate unclaimed or shared clean energy attributes. Below, we address common questions about Residual Mix Type A and Type B, explaining their definitions, applications, and relevance to SSS proxy calculations when direct supplier data is unavailable.

## What is a Residual Mix in the Context of GHG Accounting?

A residual mix represents the emissions intensity of electricity that remains after all specified claims (e.g., via Energy Attribute Certificates or EACs) have been subtracted from the total grid generation. It prevents double-counting by ensuring that only unclaimed attributes are allocated to default or unspecified loads. In the Granular Registry, residual mixes are used as a fallback for SSS proxies, helping reporters claim their pro-rata share of mandated clean energy (e.g., from RPS programs) without over- or under-attributing zero-carbon resources.

## What is Residual Mix Type A?

Type A is the most conservative residual mix, consisting solely of unclaimed or unsold electricity generation attributes after removing all transacted attributes and specified sales within a defined period. It focuses on the "leftover" grid mix, excluding any voluntary or compliance-based claims that have been tracked and retired.

* **Key Features**: Geographic boundaries align with the reporting entity's market (e.g., ISO/RTO or eGRID subregion). It utilizes data from all-generation certificate tracking systems, such as PJM-GATS or M-RETS.
* **Calculation**: (Total emissions - Emissions from specified transactions) / (Total MWh generated - MWh from specified transactions).
* **Use in Granular Registry**: Ideal for null power or unspecified purchases where no utility-specific data exists. In SSS contexts, Type A serves as a baseline proxy, ensuring allocations reflect only truly unclaimed attributes, which helps avoid resource shuffling in compliance-heavy markets.
* **Pros and Cons**: Provides high precision in tracked markets but may result in higher emissions factors if clean attributes are heavily claimed elsewhere.

## What is Residual Mix Type B?

Type B builds on Type A by incorporating shared specified attributes, such as those from Renewable Portfolio Standards (RPS) or Clean Energy Standards (CES), while excluding voluntary sales. It is used when RPS/CES attributes are retired on behalf of standard offer customers, substantiated by EACs, and allocated equally among consumers within the boundary (typically state-level).

* **Key Features**: Adds RPS/CES generation to the mix, making it more inclusive of mandated clean energy. It applies in regions without utility-specific data, reflecting policy-driven renewables as part of default supply.
* **Calculation**: (Total emissions - Emissions from specified transactions + Emissions from RPS) / (Total MWh generated - MWh from specified transactions + MWh from RPS).
* **Use in Granular Registry**: Preferred for SSS proxies in RPS states, as it equitably allocates compliance renewables to default customers. This aligns with our platform's goal of preventing double-paying for clean energy while enhancing the feasibility for reporters without direct supplier attestations.
* **Pros and Cons**: More reflective of real-world policy benefits (e.g., lower emissions for default loads) but requires careful verification to avoid double-counting; less conservative than Type A.

## How Do Type A and Type B Differ?

* **Scope**: Type A excludes all specified claims (voluntary and compliance), focusing on purely unclaimed attributes. Type B includes shared RPS/CES attributes, treating them as part of the default mix for equitable allocation.
* **Boundaries**: Type A uses market-based boundaries (e.g., wholesale markets); Type B often defaults to state-level for policy alignment.
* **When to Use Each**: Use Type A for strict avoidance of any shared claims; opt for Type B in RPS/CES contexts to credit mandated clean energy without utility data. In the Granular Registry, we recommend starting with Type A and escalating to Type B if RPS substantiation is available, ensuring compliance with Scope 2 Quality Criteria.
* **Impact on Emissions**: Type B typically yields lower (cleaner) factors due to included renewables, promoting broader participation in decarbonization.

## Why Does the Granular Registry Use These Residual Mix Types in SSS Methodology?

Our SSS proxies rely on credible third-party data to allocate clean free energy (CFE) when suppliers don't provide direct allocations. CRS's residual mix types ensure transparency, prevent double-counting, and align with GHG Protocol updates. For instance, in data-scarce regions, Type A/B calculations utilize public sources such as eGRID, EEI, or LBNL RPS reports to estimate pro-rata shares, thereby enhancing the accuracy of market-based inventories.

## Are There Limitations or Challenges with These Residual Mix Types?

Yes—data availability varies by region; approximations may be necessary for untracked generation, which could potentially introduce uncertainty. Type B risks over-crediting if RPS retirements aren't fully substantiated. In the Granular Registry, we mitigate this through QA/QC steps, including cross-verification with multiple sources and flagging high-uncertainty regions. Hourly extensions (e.g., for 24/7 accounting) are currently planned but will be annual.

## Where Can I Find More Details on CRS's Residual Mix Guidance?

For the full methodology, including equations, data sources, and examples, refer to the official CRS document: [Guidance for Calculating Residual Mix (March 2024)](https://resource-solutions.org/document/030624/). Note: As of September 16, 2025, this is the latest version; check the CRS website for any updates.
