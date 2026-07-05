# LACI Assess Card - Sample: Yemen Data-Driven Early Detection Model

**Purpose:** This card supports Step 2 (Assess) of the LACI framework. It evaluates whether the model-generated output is technically credible, IPC-relevant, and sufficiently documented.

---

## Part 1. General Assessment

### A. Technical Screening Questions

| Screening Question                                                  | Response | Justification / Link                                                                          |
| :------------------------------------------------------------------ | :------- | :-------------------------------------------------------------------------------------------- |
| Are variables, metadata, and source definitions clearly documented? | Yes      | Uses FEWS NET, WFP RTFP, ACLED, IOM-DTM, SPI.                                                 |
| Is data cleaning and schema handling described?                     | Yes      | Mapped livelihood zones to districts using spatial overlay and Meta high-res population data. |
| Are outliers handled systematically and transparently?              | Yes      | Smoothed out using Exponential Moving Averages (EMA) and Relative Strength Index (RSI).       |
| Is missing data treatment documented and justified?                 | Yes      | RTFP uses ML for missing prices; LOCF used for missing IPC data.                              |
| Is missingness assessed across relevant splits or settings?         | Yes      | Acknowledges missing data in AA-controlled areas due to access constraints.                   |
| Is spatial harmonization documented?                                | Yes      | Mapped from FEWS NET livelihood zones to 333 districts.                                       |
| Is temporal ordering enforced to avoid leakage?                     | Yes      | Warnings for time t+1 are generated with information available at time t.                     |
| Is there an appropriate held-out test strategy?                     | Yes      | Historical validation against specific subsets (prior rating < 4 transitioning to >= 4).      |
| Is hyperparameter tuning documented?                                | Yes      | Thresholds optimized by weighting FNR vs FPR (1/3 vs 2/3).                                    |
| Is class imbalance handled appropriately where relevant?            | Yes      | Adjusted loss function explicitly weights false negatives higher for alerts.                  |
| Is feature selection documented or justified?                       | Yes      | Recursive Feature Elimination (RFE) used.                                                     |
| Do the evaluation metrics match the prediction task?                | Yes      | Balanced Accuracy, F1, FPR, FNR, Brier Score.                                                 |
| Is the model compared against meaningful baselines?                 | Yes      | Compared univariate indicators vs combined models vs base GLM.                                |
| Are subgroup or residual errors examined?                           | Yes      | Analyzed specifically across the IRG (Internally Recognized Gov) and AA (Ansar Allah) divide. |
| Is uncertainty quantified?                                          | Yes      | False Positive and False Negative rates are explicitly tracked and published.                 |
| Is code or implementation sufficiently available for review?        | Yes      | Verified reproducibility package available at World Bank repository.                          |
| Is there a model card or equivalent technical documentation?        | Yes      | The working paper acts as comprehensive documentation.                                        |

### B. Minimum Requirements Checklist

| Requirement | Evaluator Assessment |
| :--- | :--- |
| **MR1: No unstated/unverifiable variables** | Pass |
| **MR2: Output is precisely defined** | Pass |
| **MR3: No target leakage in validation** | Pass |
| **MR4: Methodological documentation available** | Pass |

---

## Part 2. Context-Specific Assessments & Limitations

| Question                                                                                                                                                        | Response / Details                                                                                                                         |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| **Target Geography & Scale:** What is the specific geography and spatial resolution this assessment covers?                                                     | Yemen, all 333 districts.                                                                                                                  |
| **Target Crisis Profile:** What specific types of shocks, seasons, or crisis typologies does this assessment cover?                                             | Macroeconomic inflation, localized and neighboring conflict, forced displacement, and drought.                                             |
| **Time Horizon Assessed:** Is the output predicting current conditions, 3-months ahead, 6-months ahead?                                                         | Forecasts 5 months ahead.                                                                                                                  |
| **Context-Specific Validation:** Has the model’s performance been evaluated *specifically* on the target geography, crisis profile, and time horizon?             | Yes. Historical validation over 2014-2023 specifically isolates the IRG/AA geographic divide to evaluate localized performance.            |
| **Localized Error & Uncertainty:** Are there known error patterns in this specific geography?                                                                   | Yes. Food security in IRG areas is driven primarily by inflation, while in AA areas it is driven by drought. Exchange rates are highly volatile and perform better when modeled with the North/South divide context. |
| **Relevance of the Target:** Is the model's target an appropriate proxy for the intended phenomenon?                                                            | Yes. It is proxy-trained specifically on historical FEWS NET IPC Phase 4+ estimates (escalations only).                                    |
| **Uncertainty Communication:** How does the model communicate uncertainty for this specific context?                                                            | Uses threshold-dichotomized "Alerts" (prioritizing False Negatives) and "Alarms" (prioritizing False Positives) to convey severity and likelihood. |
| **Data Dependency Risks:** Does the model rely on datasets that are fragile, delayed, or subject to manipulation in this context?                               | Yes. FEWS NET outcome data in AA areas has suffered from significant evidence scarcity and access constraints post-COVID-19. Exchange rates in AA areas are also complex due to the dual currency system. |
| **Assumption Violations:** What conditions would break the model’s core assumptions in this context?                                                            | Severe disruption to the dual-currency dynamic or massive changes to humanitarian food aid inflows that decouple historical inflation from food access. |
| **Vulnerable Subgroups:** Does the model demonstrably mischaracterize or fail to capture the severity experienced by specific demographic or livelihood groups? | Cannot be assessed based on provided documentation. The paper evaluates spatial subgroups (IRG vs AA) but does not disaggregate performance by livelihood or demographic subgroup. |
| **Data Staleness:** Has the underlying relationship between variables shifted since the model was trained?                                                      | The paper notes that FEWS NET data in AA areas has shown minimal variation since the pandemic due to assessment constraints, meaning the historical training relationship may be artificially static in those regions post-2020. |
| **Shock Triggers:** What major, unprecedented shocks in this context require immediate reassessment?                                                            | Major global market shocks affecting import pipelines (e.g., Ukraine war impacting wheat prices), or radical shifts in the central banking structure of Yemen. |

---

## Part 3. Special Rule for IPC-Trained Models

*Because this model is classified as an IPC-Indicative Model trained on FEWS NET IPC outcomes, this special rule applies.*

| Question                                                                                | Response                                                                                                                                                     | Assessment Implication / Flag                                                                                         |
| :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
| How is the IPC training data consolidated and prepared?                                 | FEWS NET livelihood zones were mapped to 333 districts using spatial overlay and population density weighting. IPC Phases <=3 were coded as 0, and >=4 as 1. | Minor flag: Spatial overlay from livelihood zones to districts introduces some spatial approximation error.           |
| Is the target definition correct and aligned with IPC protocols (e.g., Phase 3+ vs 4+)? | Yes, the model explicitly targets the transition from Phase 3 (Crisis) to Phase 4 (Emergency).                                                               | No flag. Correct alignment with operational thresholds.                                                               |
| Could the output be misinterpreted as a direct, endorsed IPC classification?            | Yes, the final GLM output is scaled to "population in IPC Phase 4+".                                                                                         | Major flag: Requires explicit UI guardrails so users know this is a modeled forecast, not a consensus classification. |
| Does validation cover IPC-relevant contexts, shocks, geographies, and analysis cycles?  | Yes, covers 2014-2023 across Yemen, capturing currency crises, blockades, and the Ukraine war shock.                                                         | No flag.                                                                                                              |
| What guardrails prevent the output from replacing analyst-led consensus classification? | The paper positions this as an "early warning" to "complement existing assessments."                                                                         | Moderate flag: The tool itself needs visual disclaimers when deployed to analysts.                                    |

---

## Part 4. IPC GSU Summary

### A. Recommended Context-Specific Outcome

Based on the general assessment and context-specific limitations, how should this model output be used?

- [ ] **No additional limitation identified:** Use as standard.
- [x] **Use with documented limitation:** Output is useful but subject to specific constraints noted in Part 2.
- [ ] **Use only as contextual risk signal:** Output cannot be used as direct evidence, but can prompt further investigation.
- [ ] **Trigger reassessment:** Current context triggers require re-evaluating the model's appropriateness.
- [ ] **Do NOT use:** Under current conditions, the output is misleading or unsuitable.

### B. Operational Guidance / Instructions for Analysts

| Category | Guidance |
| :--- | :--- |
| **Permitted Analytical Functions** | Approved for use in **Contextual Risk Monitoring** (using Alerts and Alarms) and **Projection Assumption Tracking** (leveraging the 5-month lead time). |
| **Strict Prohibitions** | Must **not** be used as standalone evidence for Current Analysis. The "expected population in Phase 4+" metric must **not** be published or communicated externally as an official IPC phase population estimate. |
| **Accounting for Uncertainty** | Analysts reviewing AA-controlled areas should recognize that the model relies heavily on drought indicators, as historical inflation metrics behave differently under the dual currency system. |
| **Contextual Warning Flags** | Be aware that the ground-truth training data in AA-controlled areas has been sparse post-COVID, meaning the model's historical baselines may not fully capture recent localized shifts in vulnerability. |
