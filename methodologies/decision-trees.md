# SSS Designation Decision Trees

## Monopoly supplier or facilities with regulated cost recovery

{% @mermaid/diagram content="flowchart TB
A\["Is the resource part of default service for all customers?"] -- Yes --> B\["<b>Standard Supply Service</b><br>Option to claim up to your<br>pro rata share"]
A -- No --> C\["Is the resource part of a green tariff or<br>other specified product?"]
C -- Yes --> D\["Are all costs recovered through rates paid<br>by subscribers to the specified product<br>(e.g., green tariff)?"]
C -- No --> B
D -- Yes --> F\["Was the resource initially built to serve<br>the specified product?"]
D -- No --> B
F -- Yes --> E\["<b>Not SSS</b><br>Eligible for preferential claims without limitation"]
F -- No --> B
%% ───────────── Styling (optional) ──────
style B fill:#e6fff9,stroke:#e6fff9,stroke-width:1.5px
style E fill:#ffe6ec,stroke:#ffe6ec,stroke-width:1.5px

" %}

## Policy Mandates / Compliance Programs

{% @mermaid/diagram content="graph TD
Q1\["Does the resource participate in a<br>mandatory clean energy program required<br>by legislation or regulation?"] -->|Yes| Q2\["Is the certificate retired or made ineligible<br>by participation in the program?"]
Q1 -->|No| End\["<b>Not SSS</b><br>Eligible for preferential claims<br>beyond SSS allocation"]
Q2 -->|Yes| Q3\["Are the costs for this program being<br>recovered through the utility bill or<br>supplier contract?"]
Q2 -->|No| End
Q3 -->|Yes| SSS\["<b>Standard Supply Service</b><br>Option to claim up to your pro rata share"]
Q3 -->|No| End

```
    %% ───────────── Styling (optional) ──────
style SSS fill:#e6fff9,stroke:#e6fff9,stroke-width:1.5px
style End fill:#ffe6ec,stroke:#ffe6ec,stroke-width:1.5px" %}
```

## Publicly owned

{% @mermaid/diagram content="graph TD
Q1\["Is the resource majority owned by a<br>government entity supplying load in their<br>home country or region?"] -->|Yes| Q2\["Is the resource taxpayer funded?"]
Q1 -->|No| End\["<b>Not SSS</b><br>Eligible for preferential claims beyond SSS allocation"]
Q2 -->|Yes| Q3\["Was the resource developed through a<br>project awarded through competitive<br>process where government-owned<br>companies receive no taxpayer support<br>different from what a privately owned<br>company would receive?"]
Q2 -->|No| End
Q3 -->|Yes| End
Q3 -->|No| SSS\["<b>Standard Supply Service</b><br>Option to claim up to your pro rata share"]

```
    %% ───────────── Styling (optional) ──────
style SSS fill:#e6fff9,stroke:#e6fff9,stroke-width:1.5px
style End fill:#ffe6ec,stroke:#ffe6ec,stroke-width:1.5px" %}
```