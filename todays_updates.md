# LACI Framework Updates - July 3, 2026

Today, we significantly advanced the operationalization of the LACI framework by restructuring its core templates and documenting a complete, real-world case study.

## 1. Restructuring of the Core Templates
We transitioned the **Learn** and **Assess** cards away from theoretical constructs into strictly defined, actionable templates.

*   **LACI Learn Card Refactoring:**
    *   Consolidated into a strict **3-Part Structure**:
        *   **Part 1 (Model Metadata, Output & Methodology):** Merged model descriptions, operational readiness, and methodology (data sources, target profile, missing data handling, and assumptions).
        *   **Part 2 (Model Typology):** Isolated to focus purely on classification (e.g., Content Typology, Temporal Typology, Prediction Horizon).
        *   **Part 3 (IPC Application Mapping):** Stripped out confusing "Reliability Mapping" to strictly handle initial IPC suitability and the final IPC GSU routing summary.
*   **LACI Assess Card Refactoring:**
    *   Consolidated into a strict **4-Part Structure**:
        *   **Part 1 (General Assessment):** Merged Technical Screening and Minimum Requirements Checklists into a single pass.
        *   **Part 2 (Context-Specific Assessments & Limitations):** *This was the major addition.* We merged the previously independent "Limitation Sheet" directly into the Assess Card, establishing a structured Q&A to interrogate Target Geography, Crisis Profiles, Localized Error, Data Dependency Risks, Vulnerable Subgroups, and Data Staleness.
        *   **Part 3 (Special Rule for IPC-Trained Models):** Added strict guardrails for models outputting IPC phase estimations to prevent analyst replacement.
        *   **Part 4 (IPC GSU Summary):** Added actionable routing outputs (e.g., "Use with documented limitation") and explicit Analyst Instructions.

## 2. Framework Document Synchronization
*   Updated the master `LACI_framework_content_structure_v1.md` document to accurately mirror the new 3-Part Learn Card and 4-Part Assess Card definitions.

## 3. Real-World Application: Yemen Case Study
We applied the newly restructured templates to the World Bank Policy Research Working Paper: *A Data-Driven Approach for Early Detection of Food Insecurity in Yemen’s Humanitarian Crisis*.

*   **Learn Card (Yemen):** Cataloged the model's reliance on six key indicators (Food/Fuel RTFP, RTFX, SPI, ACLED, IOM-DTM) to generate a 5-month forecast of IPC Phase 4+ transitions.
*   **Assess Card (Yemen):**
    *   Successfully executed the Context-Specific Assessment.
    *   Identified that food security drivers split sharply across the IRG (inflation-driven) and AA (drought-driven) geographic divide.
    *   Flagged severe data staleness and dependency risks in AA-controlled areas post-COVID due to a lack of ground-truth IPC assessments.
    *   *Anti-Hallucination Enforced:* Explicitly marked "Vulnerable Demographic/Livelihood Subgroups" as "Cannot be assessed" since the paper only provided spatial disaggregations.
    *   Issued a **Major Flag** in the Special Rules section because the model outputs "expected population in IPC Phase 4+", which carries a high risk of being misinterpreted as an official, consensus-based IPC phase classification if not accompanied by strict UI disclaimers.

## 4. Consolidation
*   Created a new consolidated folder (`LACI_Consolidated_v1`) containing the finalized `LACI_Overview.md`, the updated Framework Structure, the two newly finalized blank templates, and the two completed Yemen sample cards.
*   Deleted obsolete standalone limitation sheets.
