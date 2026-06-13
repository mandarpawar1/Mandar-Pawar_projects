# Hospital Readmission Analysis

A multi-level analytics workbook examining patient readmission patterns across 66,587 hospital records. It's structured in three tiers — Basic, Medium, and Advanced — each building on the last, from simple group comparisons all the way to machine learning models and a full post-discharge program design.

---

## Dataset Overview

| Metric | Value |
|---|---|
| Total Patients | 66,587 |
| Total Readmitted | 30,764 |
| Overall Readmission Rate | 46.21% |
| Diabetic Patients | 51,205 (76.9%) |
| Age Groups | 10 |
| Medical Specialties | 65 |

The 46% readmission rate is significantly above the ~15% national benchmark, which is what makes this dataset worth digging into.

---

## Workbook Structure

The file has three levels of analysis with a total of 25 question sheets plus overview summaries.

### Basic Level (10 Questions)

Covers the foundational questions using grouping, proportions, and basic correlations.

**Q1 — Readmission by Age**
Readmission rates peak in the 70-90 age group (~48%). The 90-100 group actually dips to 38%, possibly due to palliative care patterns. The youngest patients (0-10) have the lowest rate at 22%.

**Q2 — Average Hospital Stay by Specialty**
Pediatrics-Pulmonology tops the list at 10.7 days. Physical Medicine and Rehabilitation comes in second at 8.9 days. Pediatrics-Emergency Medicine is the shortest at 1 day. Full rankings for top 15 and bottom 10 specialties are in this sheet.

**Q3 — Prior Emergency Visits vs Readmission**
One of the strongest signals in the dataset. Patients with zero prior ER visits have a 44% readmission rate. That climbs to 59% after just one prior ER visit, and hits 89% for patients with 6 or more. Correlation: r = 0.108, p < 0.001.

**Q4 — Diabetic Patients**
Diabetic patients are readmitted at 47.96% vs 40.34% for non-diabetics, an 8 percentage point gap. Since diabetics make up 76.9% of the dataset, this has an outsized effect on overall numbers.

**Q5 — Medication Change vs Readmission**
Patients whose diabetic medication was changed during the stay had a 48.62% readmission rate vs 44.13% for those without a change. Chi-square confirms this is statistically significant, though the direction of causality isn't clear. Sicker patients with worse baseline control are more likely to get medication changes and also more likely to be readmitted.

**Q6 — Lab Procedures vs Readmission**
Weak but statistically significant positive correlation (r = 0.036). Readmission rises from 43% for patients with 1-20 lab tests to about 50% for 61-80 tests, then dips. More labs probably reflects sicker patients, not a cause of readmission.

**Q7 — Race and Gender**
Caucasian patients have the highest readmission rate at 47%, followed by African Americans at 46%. Hispanic and Asian groups are around 39-41%, though their sample sizes are much smaller. Female patients are readmitted at 46.85% vs 45.44% for males.

**Q8 — Weight**
The weight column is 96.8% missing. Only 2,133 of 66,587 patients have valid weight data, so any weight-based analysis is statistically unreliable. Among valid records, very low weight groups (0-25 kg) show 80%+ readmission, likely reflecting frail or severely ill patients. The recommendation here is to make weight recording mandatory at admission.

**Q9 — Medications vs Length of Stay**
The strongest correlation in basic analysis (r = 0.466, p < 0.001). Patients on 1-5 medications average 2.3 days. Those on 31+ medications average 8 days. Makes clinical sense: complex cases need more drugs and more time. Useful for predicting resource needs at the point of admission.

**Q10 — Prior Outpatient Visits vs Readmission**
Counterintuitive result: more outpatient visits = higher readmission. Patients with zero prior outpatient visits have a 44% readmission rate. Those with 6+ have a 65% rate. This isn't a failure of outpatient care — it's a marker of chronic disease complexity. These patients use more outpatient care precisely because they're sicker.

---

### Medium Level (10 Questions)

Moves into multi-variable analysis, composite scores, and statistical testing.

**M1 — Comorbidity Effect**
Clear staircase pattern: more diagnoses = longer stays and higher readmissions. Very Low comorbidity (1-3 diagnoses) = 34% readmission and 2.76 days average stay. Very High (13-16 diagnoses) = 50% readmission and 6.44 days. Comorbidity is a solid predictor for both outcomes.

**M2 — Prior Inpatient Visits**
The strongest predictor at medium level (r = 0.217). No prior inpatient history = 38.66% readmission. One prior stay pushes that to 54%. Six or more = 85.79%. Nearly linear relationship. These high-frequency inpatients are the hospital's most vulnerable population.

**M3 — Demographics vs Medical Interventions**
Caucasian patients receive the most medications on average (16.28), followed by African Americans (15.39). Hispanic and Asian patients receive significantly fewer (14.05 and 13.18). ANOVA confirms this variation is statistically significant, not random. Medication counts also peak at 60-70 years of age and taper at both ends of the age spectrum.

**M4 — Prior Visit Patterns by Diagnosis**
Top 10 ICD-9 diagnoses ranked by readmission rate and prior hospital contact. Chronic Bronchitis (60.5%) and Heart Failure (58.6%) are the highest. Osteoarthrosis is the lowest at 35.9%. Chronic and respiratory conditions drive the most repeat hospital contact.

**M5 — Inpatient, Outpatient, Emergency Visits by Diagnosis**
Side-by-side view of all three visit types for the top 10 diagnoses. Chronic Bronchitis and Heart Failure patients have the highest total prior hospital contact. Osteoarthrosis patients are mostly first-time or elective cases with very low emergency history.

**M6 — Diabetic Medication Effectiveness**
X3 (likely metformin or a similar first-line diabetes drug) stands out: patients prescribed it have a 43.06% readmission rate vs 49.64% for those not prescribed it. Statistically significant (p < 0.001). X14 is the concerning outlier — patients on it have a 61.57% readmission rate, 13.67 percentage points above baseline. Flags a clinical review.

**M7 — Medication Prescribing by Specialty**
Nephrology has the highest readmission rate (55.1%) and moderate medication count (17.46 avg). Orthopedics and Orthopedics-Reconstructive have the lowest readmission rates (30-33%) despite the highest medication counts (20+). Internal Medicine has the most patients (9,460) and a 44% readmission rate — biggest volume opportunity for improvement.

**M8 — Weight and Diagnosis**
Extended analysis of the 3.2% of patients with valid weight data, cross-referenced with diagnosis. Results are directionally interesting but not statistically reliable given the sample size. Data quality warning is repeated here.

**M9 — Composite Patient Burden Score**
A custom composite metric: hospital stay + (readmitted × 3) + prior inpatient visits. Patients aged 80-90 carry the highest burden score (6.90). The metric rises with comorbidity level from 4.13 (Very Low) to 8.58 (Very High). More useful than any single variable for prioritizing discharge intervention resources.

**M10 — Patient Satisfaction**
Patient satisfaction data is not in this dataset. The sheet documents the gap and lists what fields are missing (HCAHPS scores, complaint data, discharge compliance, patient-reported outcomes). As a proxy, healthcare utilization history is used: patients with 7+ prior visits have a 78% readmission rate vs 36% for those with no prior contact. Recommendation: integrate HCAHPS or equivalent data for a fuller picture.

---

### Advanced Level (5 Analyses)

**A1 — Readmission Prediction Model**
Two models were built and compared: Logistic Regression and Decision Tree, both trained on 80% of records (53,269 patients) and tested on 20% (13,318 patients).

| Metric | Logistic Regression | Decision Tree |
|---|---|---|
| Accuracy | 61.6% | 62.0% |
| AUC-ROC | 0.652 | 0.650 |

Top predictors by feature importance:
1. Prior inpatient visits (critical)
2. Number of diagnoses (critical)
3. Prior emergency visits (high)
4. Prior outpatient visits (high)
5. Patient age, diabetes, and medication count (medium)

Prior inpatient visits alone account for 70% of Decision Tree feature importance. Gender and medication change had minimal predictive value.

**A2 — Patient Segmentation (K-Means, 4 Clusters)**

| Segment | Patients | Readmission Rate | Strategy |
|---|---|---|---|
| High Risk (Frequent, Complex) | 4,482 | 74.8% | Intensive case management, daily contact week 1 |
| Elevated Risk (Multi-Condition Chronic) | 14,134 | 47.5% | Telehealth check-ins, chronic disease program |
| Moderate Risk | 28,872 | 47.2% | Follow-up calls at Day 3, 7, 14 |
| Low Risk | 19,099 | 37.1% | Standard discharge, 30-day PCP appointment |

**A3 — Financial Impact**
Based on an estimated $15,000 cost per readmission and $10,000 per initial stay:

| Metric | Value |
|---|---|
| Total cost of all readmissions | $461M |
| Avoidable readmissions (27%) | 8,306 cases |
| Avoidable cost | $124.6M |
| Intervention cost (at $500/patient) | $4.2M |
| Net potential savings | $120.4M |
| ROI on intervention program | 29x |

Emergency/Trauma (50.2% readmission rate) and Nephrology (55.1%) have the highest rates by specialty. The '?' specialty group — patients with no recorded specialty — accounts for $235M in estimated cost, which points to a documentation problem.

**A4 — Social Determinants**
Caucasian patients have the highest absolute readmission count (23,477) due to population size, and sit slightly above the overall average rate. African American patients show higher ER utilization (0.26 avg prior ER visits vs 0.19 average), which may indicate healthcare access barriers. Female patients aged 80-90 have the highest readmission rate in any demographic subgroup (48.7%). Young adults (10-20) also show concerning rates (39-49%), suggesting gaps in transition care.

**A5 — Post-Discharge Follow-Up Program**
A full risk-stratified program design targeting a 20-30% readmission reduction over 12 months.

- **High Risk** (22,635 patients): Daily contact in week 1, home visits at Day 7, multidisciplinary team review at Day 14, estimated $8,500 savings per patient
- **Medium Risk** (21,971 patients): Contact at Day 1, 3, 7, 14, 30, estimated $5,200 savings per patient
- **Low Risk** (21,981 patients): Standard discharge + Day 7 and Day 30 check-in, estimated $800 savings per patient

Staffing model: 19 FTEs total (8 RN care coordinators, 4 community health workers, 2 clinical pharmacists, 3 social workers, 1 data analyst, 1 program manager) at an estimated $1.63M annual cost.

Target KPIs: overall readmission rate down from 46.2% to 35% by month 12, high-risk rate from 60.7% to 42%, PCP visit within 7 days up from ~30% to 75%.

---

## Key Findings

1. **Prior inpatient visits is the strongest predictor of readmission**, both in the correlation analysis and the ML model. Patients with 6+ prior inpatient visits are readmitted at 85.79%.

2. **The first hospitalization is a signal.** Patients with no prior hospital history are readmitted at 38.66%. A single prior stay pushes that to 54%. This is where early intervention programs pay off.

3. **ER visit frequency is a close second signal.** Six or more prior ER visits = 89% readmission. These patients need to be flagged and enrolled in ER diversion and intensive management programs.

4. **Chronic Bronchitis and Heart Failure drive readmissions the most.** Both show 58-60% readmission rates and the highest prior hospital contact of any diagnosis group.

5. **Weight data is nearly unusable.** 96.8% of the weight column is missing. Making weight recording mandatory at admission is a necessary first step before this variable can be used in any clinical model.

6. **Diabetic medication X3 is protective. X14 is not.** X3 reduces readmission by 6.58 percentage points; X14 raises it by 13.67. The diabetes management team should review medication protocols with these numbers in hand.

7. **$120M in potential savings is on the table.** The financial model estimates that a $4.2M intervention program targeting the 27% of readmissions considered avoidable could deliver a 29x return.

---

## Data Source

Derived from the UCI / Kaggle Diabetes 130-US Hospitals dataset (1999-2008), adapted for hospital administration case study purposes under the Novartis Hospital Administration branding in the Advanced section.
