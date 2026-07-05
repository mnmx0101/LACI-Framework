# LACI Learn Card: Yemen Data-Driven Early Warning Model

**Purpose:** This card supports Step 1 (Learn) of the LACI framework. It is used to document the model, describe its outputs, and provide an initial mapping to plausible IPC use pathways based on the World Bank paper "A Data-Driven Approach for Early Detection of Food Insecurity in Yemen’s Humanitarian Crisis".

---

## Part 1. Model Metadata, Output & Methodology

### A. Model Summary

| Field                                   | Description                                                                     |
| :-------------------------------------- | :------------------------------------------------------------------------------ |
| **Model Title**                   | Yemen Data-Driven Food Security Early Warning Model (from "A Data-Driven Approach for Early Detection of Food Insecurity in Yemen’s Humanitarian Crisis") |
| **Developer / Organization**      | World Bank Group (Poverty and Equity Global Practice, Development Data Group, Agriculture and Food Global Practice) |
| **Version and Date**              | May 2024 (Policy Research Working Paper 10768) |
| **Model Type**                    | IPC-Indicative Model |
| **Operational Readiness**         | Pilot / Research Paper |
| **License and Access Conditions** | Open Access, Reproducible Research Repository available |
| **Main Contacts**                 | Steve Penson (spenson@worldbank.org), Bo Pieter Johannes Andrée (bandree@worldbank.org) |
| **Documentation & Links**         | http://reproducibility.worldbank.org |

### B. Model-Generated Output Profile

| Field                                            | Description                                                   |
| :----------------------------------------------- | :------------------------------------------------------------ |
| **Output Name**                            | Food Security Emergency Alerts, Alarms, and Expected Population in IPC Phase 4+ |
| **Output Type**                            | Categorical (Alert/Alarm) and Continuous (population estimates) |
| **Output Unit and Interpretation**         | **Alerts** indicate heightened risks (more sensitive, captures more potential emergencies early). **Alarms** indicate critical risks (more specific, lower false positives). Continuous output gives the probability or number of people at risk of experiencing an IPC Phase 4+ deterioration. |
| **Spatial Coverage and Resolution**        | Yemen, 333 districts |
| **Temporal Coverage and Update Frequency** | Historical coverage 2014-2023, designed for monthly tracking |
| **Intended Users**                         | IPC technical staff, food security analysts, monitoring teams, humanitarian programmers |

### C. Data and Target Profile

| Field                                               | Description                                                     |
| :-------------------------------------------------- | :-------------------------------------------------------------- |
| **Input Data Sources**                        | 1) Food prices (RTFP), 2) Fuel prices (RTEP), 3) Exchange rates (RTFX), 4) Drought (SPI), 5) Conflict (ACLED fatalities), 6) Displacement (IOM-DTM) |
| **Training Target or Ground Truth**           | Transition into a food security emergency, defined as IPC Phase 4 or 5 (adjusted to exclude impacts of aid delivery). |
| **Target Nature**                             | Proxy-trained (FEWS NET IPC data, mapped to district level). |
| **Geographic and Temporal Training Coverage** | Yemen (333 districts), October 2014 to July 2023. |
| **Missing Data Profile**                      | High-frequency price surveys are imputed using Machine Learning. District-level IPC data gaps are handled using Last Observation Carried Forward (LOCF). |
| **Major Assumptions**                         | FEWS NET IPC phase ratings accurately reflect the ground truth of food security stress, despite data access issues. The regional divide between IRG and AA controlled areas results in distinct macroeconomic dynamics (e.g., dual currency). |

---

## Part 2. Model Typology

### A. Typology Classification

| Field                                | Description / Classification                                                                                                                         |
| :----------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Content Typology**           | **IPC-Indicative Model** (Proxy-trained on IPC outcomes)                                                                                             |
| **Temporal Typology**          | **Forecasting**                                                                                                                                      |
| **Prediction Horizon**         | **5 months ahead** (The model's optimal lag was determined to be 5 months, showing it can reliably anticipate escalations before they manifest).     |
| **Typology Rationale**         | Contributing factors (prices, conflict, etc.) are trained against a food-security proxy outcome (FEWS NET IPC data) to establish mathematically optimal threshold triggers (alerts and alarms) that forecast escalations. |
| **Special Assessment Routing** | **Yes - Route to Part 3 Special Rule in Assess Card**. The output uses FEWS NET data as ground truth and estimates populations in IPC Phase 4+, which risks being misinterpreted as an official IPC phase classification. |

---

## Part 3. Initial IPC Application Mapping

### A. Initial IPC Mapping

| Potential IPC Application     | Suitability (High/Med/Low/None) | Rationale (Link to Framework Definitions)              |
| :---------------------------- | :------------------------------ | :----------------------------------------------------- |
| **Current Analysis**    | **Low**                         | The model is explicitly designed to predict future transitions (5 months ahead) rather than estimating unobserved current conditions. While underlying price/conflict indicators may support current analysis, the model's ultimate output is not direct current evidence. |
| **Projection Analysis** | **High**                        | The output successfully tracks conditions that drive forecasts. The 5-month lead time is perfectly aligned with testing whether conditions underlying existing projections remain plausible. |
| **Risk Monitoring**     | **High**                        | The continuous calculation of "Alerts" and "Alarms" flags unusual patterns or emerging risks (e.g., compounding inflation and drought) requiring immediate analyst attention between assessment cycles. |

### B. IPC GSU Summary

| Field | Summary / Decision |
| :--- | :--- |
| **Reviewer Name / Title** | [Enter Name and Title] |
| **Review Date** | [Enter Date] |
| **Operational Readiness** | Pilot / Research Paper |
| **Confirmed Content Typology** | IPC-Indicative Models |
| **Confirmed Temporal Typology**| Forecasting |
| **Primary IPC Application(s)** | Projection Analysis, Risk Monitoring |
| **Special Routing Required?** | Yes - route to Part 3 Special Rule in Assess Card |
| **GSU Notes / Caveats** | Output framing requires clear UX distinctions to avoid confusion with official IPC. |
