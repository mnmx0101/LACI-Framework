# LACI Assess Card Template

**Purpose:** This card supports Step 2 (Assess) of the LACI framework. It unifies two distinct but sequentially related assessment functions:
- **Part 1 (General Assessment):** A technical screening of the underlying model to identify critical integrity problems, flag warning signs, and establish initial exclusion criteria.
- **Part 2 (Context-Specific Assessment):** An evaluation of the specific model-generated output to determine its performance limitations, assumption validity, and appropriate use within targeted geographies and operational contexts.

**General Operational Guide:**
- **When is this done?** This card is completed *after* the Learn step (Step 1) has mapped the initial typology, and *before* the output can proceed to the Calibrate (Step 3) and Integrate (Step 4) steps.
- **Who completes it?** It is drafted by the model builder and critically reviewed/finalized by the IPC Data Innovation Team (DIT) and Context Limitation reviewers.
- **What is the operational output?** The completed Assess Card (specifically culminating in the *Part 4 IPC GSU Summary*) serves as the definitive technical audit record. It dictates the exact operational mapping, usage instructions, and constraints for analysts in the field.

---

## Part 1. General Assessment (Technical Screening & Initial Exclusion)

*This section uses technical screening questions to provide flagged points that indicate whether a model should not be considered for IPC applications at all. A failure in the Minimum Requirements Checklist acts as an initial exclusion criterion.*

### A. Technical Screening Questions

*These questions are simplified operational readings of the fuller assessment metrics and are intended to support consistent flagging and documentation. This technical screening provides the evidence base for context-specific limitations and the minimum requirements checklist.*

**The function of this screening is to:**

- Identify technical warning signs
- Surface integrity problems
- Flag issues that may weaken trust, traceability, or later IPC use

**Response format:**

- `Yes` = there is clear evidence that the issue has been addressed in a credible and reviewable way
- `No` = there is a clear weakness, gap, or unresolved concern
- `Unclear` = the available documentation is too limited to judge confidently

> [!IMPORTANT]
> Any `No` or `Unclear` response generates a **Flag**. A flag does not automatically disqualify a model generated output (unless it violates Minimum Requirements), but it should be documented in the **Flag Point** column and carried into the Context-Specific Assessment.

| Screening Dimension                       | Screening Question                                                          | Response (Yes/No/Unclear) | Flag Point (If not addressed/considered) | Justification / Link |
| :---------------------------------------- | :-------------------------------------------------------------------------- | :------------------------ | :--------------------------------------- | :------------------- |
| **1. Data Quality**                 | Are variables, metadata, and source definitions clearly documented?         |                           |                                          |                      |
| **1. Data Quality**                 | Is data cleaning and schema handling described?                             |                           |                                          |                      |
| **1. Data Quality**                 | Are outliers handled systematically and transparently?                      |                           |                                          |                      |
| **1. Data Quality**                 | Is missing data treatment documented and justified?                         |                           |                                          |                      |
| **2. Missing Data & Harmonization** | Is missingness assessed across relevant splits or settings?                 |                           |                                          |                      |
| **2. Missing Data & Harmonization** | Is spatial harmonization documented?                                        |                           |                                          |                      |
| **2. Missing Data & Harmonization** | Is temporal ordering enforced to avoid leakage?                             |                           |                                          |                      |
| **3. Model Design**                 | Is there an appropriate held-out test strategy?                             |                           |                                          |                      |
| **3. Model Design**                 | Is hyperparameter tuning documented?                                        |                           |                                          |                      |
| **3. Model Design**                 | Is class imbalance handled appropriately where relevant?                    |                           |                                          |                      |
| **3. Model Design**                 | Is feature selection documented or justified?                               |                           |                                          |                      |
| **4. Evaluation Rigor**             | Do the evaluation metrics match the prediction task?                        |                           |                                          |                      |
| **4. Evaluation Rigor**             | Is the model compared against meaningful baselines?                         |                           |                                          |                      |
| **4. Evaluation Rigor**             | Are subgroup or residual errors examined?                                   |                           |                                          |                      |
| **4. Evaluation Rigor**             | Is uncertainty quantified?                                                  |                           |                                          |                      |
| **5. Transparency**                 | Is code or implementation sufficiently available for review?                |                           |                                          |                      |
| **5. Transparency**                 | Is there a model card or equivalent technical documentation?                |                           |                                          |                      |
| **5. Transparency**                 | Are limitations clearly stated?                                             |                           |                                          |                      |
| **5. Transparency**                 | Can intended users understand how the output should and should not be used? |                           |                                          |                      |

### B. Minimum Requirements Checklist

> [!CAUTION]
> The model **fails** minimum requirements and should not be considered for IPC applications if any of the following critical flags apply. These points represent severe technical or conceptual flaws identified during the screening above.

- [ ] **Data Quality Failure:** The model output, training target, or ground truth is fundamentally undefined or undocumented, making it impossible to know what the model is actually predicting.
- [ ] **Data Quality Failure:** Missing data treatment is entirely undocumented despite missingness being a known material issue in the input data.
- [ ] **Model Design Failure:** There is a clear, unaddressed risk of temporal leakage (e.g., training data contains future information that would not be available in real-world forecasting).
- [ ] **Evaluation Rigor Failure:** There is no meaningful out-of-sample validation or testing strategy (e.g., the model is only evaluated on the data it was trained on).
- [ ] **Transparency Failure:** There is absolutely no documentation of uncertainty, error bounds, or limitations, making the output unsafe for high-stakes IPC decision-making.
- [ ] **Transparency Failure:** There is no explanation provided for how end-users or analysts are supposed to interpret the output values.
- [ ] **Misalignment Risk:** The output claims to represent a specific high-stakes outcome or hazard severity (e.g., direct IPC phases, acute malnutrition, extreme drought) but lacks validation against established domain protocols or ground truth data.
- [ ] **Misalignment Risk:** The model is trained on proxy data (e.g., NDVI for drought, or FEWS NET outcomes for food security) but is presented as directly translating to the target phenomenon or IPC classification without sufficient evidence or calibration.

---

## Part 2. Context-Specific Assessments & Limitations

*While Part 1 evaluates the general technical soundness of the model, Part 2 evaluates whether the specific model-generated output is valid, performant, and reliable for a **specific operational context** (e.g., a specific country, crisis type, or season). This section identifies the contextual boundaries of the output and flags when caution or reassessment is needed.*

### A. Assessment Context

*Define the specific operational environment being evaluated. (Do not repeat the model's global characteristics from the Learn Card; specify the exact context under review).*

| Field                                 | User Entry                                             |
| :------------------------------------ | :----------------------------------------------------- |
| **Target Geography & Scale**          | [e.g., South Sudan, ADM2 level]                        |
| **Target Crisis Profile**             | [e.g., Conflict-driven displacement, prolonged drought]|
| **Time Horizon Assessed**             | [e.g., Current monitoring, 3-month projection]         |

### B. Localized Performance & Validation

*Evaluate whether the model's general performance holds up in this specific context.*

| Question                                                                                                                    | Response / Details                           |
| :-------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------- |
| **Context-Specific Validation:** Has the model been explicitly tested and validated in this geography and crisis type?      |                                              |
| **Localized Error & Uncertainty:** How does the model perform here compared to its global baseline? (e.g., higher false positive rate?) | [Include context-specific metrics if available] |
| **Relevance of the Target:** Is the model's training target an appropriate proxy for the intended phenomenon (e.g., acute food insecurity, drought severity, market stress, displacement) in this specific region? |                                              |
| **Uncertainty Communication:** Is the uncertainty of the output accurately communicated for this specific context?          |                                              |

### C. Contextual Limitations & Assumption Risks

*Identify the local conditions, data gaps, or assumption violations that weaken the output's reliability.*

| Question | Response / Details |
| :--- | :--- |
| **Data Dependency Risks:** Are the critical input data streams (e.g., market prices, rainfall) reliable, timely, and representative for this specific region? | |
| **Assumption Violations:** What local conditions (e.g., border closures, informal markets, sudden displacement) violate the model's core assumptions? | |
| **Vulnerable Subgroups:** Are there specific populations (e.g., IDPs, pastoralists, riverine/coastal communities) within this context that the model systematically misrepresents or excludes? | |

### D. Reassessment Triggers

*Define the thresholds that require immediate re-evaluation of the output's appropriateness.*

| Question | Response / Details |
| :--- | :--- |
| **Data Staleness:** Is the input data or ground-truth training data too old to reflect current realities in this context? | [Enter date / frequency thresholds] |
| **Shock Triggers:** What specific contextual shocks (e.g., sudden conflict escalation, major currency devaluation) would immediately invalidate the model's assumptions here? | [List specific trigger events] |

---

## Part 3. Special Rule for IPC Estimates & IPC-Indicative Models

*Complete this section ONLY if the model falls under the Content Typology of **IPC Estimates (AFI/AMN Estimates)** or **IPC-Indicative Models**. Because these models have a direct implication for IPC estimates, separate assessing is needed.*

* **IPC Estimates (AFI/AMN Estimates):** Models that directly estimate IPC phase classifications or affected populations. These estimates represent analytical outputs that directly approximate IPC classifications or population estimates rather than individual contributing factors or outcome indicators (e.g., IPC Phase Outcome nowcast and forecasting model generated outputs).
* **IPC-Indicative Models:** Models that estimate IPC-indicative severity based on contributing factors. They generate indicative severity levels, warning scores or alerts that can support current analyses, projection analyses and ongoing monitoring.

| Guiding Question | Response / Assessment |
| :--- | :--- |
| **How do they define the outcome?** Is the target definition correct and aligned with IPC protocols? | |
| **How is data merged?** How is historical IPC data consolidated and prepared alongside predictor data? | |
| **Misinterpretation Risk:** Could the output be misinterpreted as a direct, endorsed IPC classification? | |
| **Guardrails:** What prevents the output from replacing analyst-led consensus classification? | |

---

## Part 4. IPC GSU Summary

*This section defines the specific verdict on how the assessment informs the subsequent steps (Calibrate and Integrate). It summarizes the context-specific outcomes for model output users.*

### A. Recommended Context-Specific Outcome

Based on the general assessment and context-specific limitations, how should this model output be used? *(Select one or more)*:

- [ ] **No additional limitation identified:** Use as standard.
- [ ] **Use with documented limitation:** Output is useful but subject to specific constraints noted in Part 2.
- [ ] **Use only as contextual risk signal:** Output cannot be used as direct evidence, but can prompt further investigation.
- [ ] **Trigger reassessment:** Current context triggers (from Part 2D) require re-evaluating the model's appropriateness.
- [ ] **Do NOT use:** Under current conditions, or due to initial exclusion in Part 1, the output is misleading or unsuitable.

### B. Operational Mapping & Guidance for Analysts
*This section translates the assessment findings into direct, actionable guidance. It maps the output against its potential IPC application and serves as the direct basis for **Step 3: Calibrate** (translating outputs into interpretation rules, thresholds, and uncertainty framing).*

| Operational Domain | Actionable Guidance / Instructions | Supporting Rationale |
| :--- | :--- | :--- |
| **Application Mapping** | [Specify the exact potential IPC application(s) this output is approved for: e.g., Risk Monitoring] | [Narrative rationale derived from Part 2] |
| **Usage Instructions** | [Specify exactly how analysts should use the output in the current cycle] | [Narrative rationale based on model performance] |
| **Uncertainty & Risks** | [Specify how to account for uncertainty and known risks] | [Narrative rationale based on limitations/assumptions] |
| **Strict Prohibitions** | [Specify what analysts must NOT do with this output] | [Narrative rationale based on initial exclusions or guardrails] |
