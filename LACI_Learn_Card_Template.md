# LACI Learn Card Template

**Purpose:** This card supports Step 1 (Learn) of the LACI framework. It establishes the foundational understanding of the model before any technical evaluation occurs. It consists of three main components:
- **Part 1 (Model Metadata, Output & Methodology):** Captures essential metadata, operational readiness, the definition of the model-generated output, and the underlying data sources and assumptions.
- **Part 2 (Model Typology):** Classifies the model's analytical focus and temporal dimension to determine assessment routing.
- **Part 3 (IPC Application Mapping):** Performs an initial alignment of the output against specific potential IPC applications (e.g., Risk Monitoring) and provides the IPC GSU summary.

**General Operational Guide:**
- **When is this done?** This is the very first step in the LACI process. It must be completed *before* moving to the Assess step (Step 2).
- **Who completes it?** It is typically drafted by the model builder or data provider, and reviewed by the IPC Data Innovation Team (DIT) or designated Learn Agent.
- **What is the operational output?** The completed Learn Card serves as the definitive reference document (a "metadata dictionary") for the model. It provides the necessary context and initial IPC mapping required to conduct the rigorous technical screening in the subsequent Assess step.

---

## Part 1. Model Metadata, Output & Methodology

### A. Model Summary

| Field                                   | Description                                                                     |
| :-------------------------------------- | :------------------------------------------------------------------------------ |
| **Model Title**                   | [Enter Model Title]                                                             |
| **Developer / Organization**      | [Enter Developer or Organization]                                               |
| **Version and Date**              | [Enter Version and Date]                                                        |
| **Model Type**                    | [e.g., Contributing Factors, Outcome Indicators, IPC Estimates, IPC-Indicative] |
| **Operational Readiness**         | [e.g., Demo/Prototype, Pilot, Fully Operational]                                |
| **License and Access Conditions** | [Enter License Details]                                                         |
| **Main Contacts**                 | [Enter Contact Information]                                                     |
| **Documentation & Links**         | [Provide links to papers, repos, dashboards, or technical docs]                 |

### B. Model-Generated Output Profile

| Field                                            | Description                                                   |
| :----------------------------------------------- | :------------------------------------------------------------ |
| **Output Name**                            | [Enter Output Name]                                           |
| **Output Type**                            | [e.g., continuous, probabilistic, categorical, signal, index] |
| **Output Unit and Interpretation**         | [Explain how to read the output value]                        |
| **Spatial Coverage and Resolution**        | [e.g., National, ADM2, 10km grid]                             |
| **Temporal Coverage and Update Frequency** | [e.g., 2010-present, updated monthly]                         |
| **Intended Users**                         | [Who is this output built for?]                               |

### C. Data and Target Profile

| Field                                               | Description                                                     |
| :-------------------------------------------------- | :-------------------------------------------------------------- |
| **Input Data Sources**                        | [List main input datasets]                                      |
| **Training Target or Ground Truth**           | [What is the model trying to predict?]                          |
| **Target Nature**                             | [Is the target IPC, FEWS NET, an indicator, or a hazard proxy?] |
| **Geographic and Temporal Training Coverage** | [Where and when was the model trained?]                         |
| **Missing Data Profile**                      | [How are missing inputs handled?]                               |
| **Major Assumptions**                         | [List core assumptions the model relies on]                     |

---

## Part 2. Model Typology

### A. Typology Classification

*Classify the model's analytical focus and temporal dimension to determine assessment routing. According to the Framework, these typologies determine how outputs are reviewed, assessed, and calibrated.*

**1) Content Typology Reference:**
* **Contributing Factors:** Models that estimate the conditions and drivers influencing food security and nutrition outcomes.
* **Outcome Indicators:** Models that estimate the observed food security and nutrition outcomes experienced by a population.
* **IPC Estimates (AFI/AMN Estimates):** Models that directly estimate IPC phase classifications or affected populations.
* **IPC-Indicative Models:** Models that estimate IPC-indicative severity based on contributing factors.

**2) Temporal Typology Reference:**
* **Nowcasting / Monitoring:** Estimating current, unobserved conditions based on recent/current data.
* **Forecasting:** Predicting future conditions.

| Field                                | Description / Classification                                                                                                                         |
| :----------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Content Typology**           | [Enter Typology from Content Reference above]                                                                                                        |
| **Temporal Typology**          | [Enter Nowcasting / Monitoring OR Forecasting / Projection]                                                                                          |
| **Prediction Horizon**         | [Specify the exact horizon, e.g., Current status, 1-month ahead. This directly dictates which IPC mapping is feasible.]              |
| **Typology Rationale**         | [Explain why these classifications were chosen based on the relationship between inputs, target, and time horizon]                                   |
| **Special Assessment Routing** | [e.g., Route to Part 3 Special Rule in Assess Card if the output may be interpreted as direct food-security outcome evidence] |

---

## Part 3. Initial IPC Application Mapping

*Map the suitability of this output across the three potential IPC applications as defined in the Framework. This is a preliminary map to guide the assessment, not a final use decision.*

### A. Initial IPC Mapping

**Suitability Criteria:**
* **High:** The output format, timeliness, and target directly align with the analytical function of the application.
* **Medium:** The output is relevant but requires significant transformation, additional context, or has slight temporal/spatial mismatches.
* **Low:** The output provides only tangential information or requires major assumptions to be relevant.
* **None:** The output is completely mismatched.

| Potential IPC Application     | Suitability (High/Med/Low/None) | Rationale (Link to Framework Definitions)              |
| :---------------------------- | :------------------------------ | :----------------------------------------------------- |
| **Current Analysis**    | [ ]                             | [Explain how it supports current condition assessment] |
| **Projection Analysis** | [ ]                             | [Explain how it tracks forward-looking assumptions]    |
| **Risk Monitoring**     | [ ]                             | [Explain how it flags contextual risks and anomalies]  |

### B. IPC GSU Summary

*This section is to be completed by the IPC Global Support Unit (GSU). It summarizes the model's typology, operational readiness, and initial mapping for downstream assessment routing.*

| Field | Summary / Decision |
| :--- | :--- |
| **Reviewer Name / Title** | [Enter Name and Title] |
| **Review Date** | [Enter Date] |
| **Operational Readiness** | [Confirm if demo/prototype vs fully operational] |
| **Confirmed Content Typology** | [e.g., Contributing Factors, Outcome Indicators, IPC Estimates, IPC-Indicative Models] |
| **Confirmed Temporal Typology**| [e.g., Nowcasting / Monitoring, Forecasting] |
| **Primary IPC Application(s)** | [Which applications are deemed suitable enough to proceed to the Assess step?] |
| **Special Routing Required?** | [e.g., Yes - route to Part 3 Special Rule in Assess Card, No] |
| **GSU Notes / Caveats** | [Any additional context for the assessment team] |
