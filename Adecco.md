# Adecco India | HR Attrition Analysis

A data analysis workbook examining employee attrition patterns across Adecco India's workforce. Built to answer 10 specific HR questions using an employee dataset of 1,470 people.

---

## At a Glance

| Metric | Value |
|---|---|
| Total Employees | 1,470 |
| Attritioned | 237 |
| Retained | 1,233 |
| Overall Attrition Rate | 16.12% |

---

## What's in the File

The workbook has 11 sheets. One overview sheet summarizes all findings, and the remaining 10 each answer a specific HR question.

### Overview Medium Q
A one-page summary of all 10 analyses with key findings and attrition rates at a glance. Good starting point before diving into individual sheets.

---

### Q1 — Top 3 Attrition Drivers
Uses Pearson correlation to rank every numeric variable by its relationship to attrition.

**Top 3 factors:**
- **Total Working Years** (corr: -0.17) — Newer employees leave more. First 2-3 years are the highest-risk window.
- **Job Level** (corr: -0.17) — Junior roles have the highest attrition. Career path clarity is a gap.
- **Years in Current Role** (corr: -0.16) — Employees stuck in the same role too long disengage and leave.

Full correlation table for all 17 factors is included.

---

### Q2 — Job Involvement vs Attrition
Breaks attrition down by job involvement level (1=Low to 4=Very High).

| Involvement | Attrition Rate |
|---|---|
| Low | 33.7% |
| Medium | 18.9% |
| High | 14.4% |
| Very High | 9.0% |

Disengaged employees are **3.7x more likely to leave** than highly involved ones. This is the strongest single actionable signal in the dataset.

---

### Q3 — Age vs Job Satisfaction
Checks whether job satisfaction differs across age groups (18-60).

Satisfaction scores are flat across all age bands (range: 2.63–2.78 out of 4). This isn't a generational issue — it's a company-wide culture and work design problem. Younger employees (18-30) leave more, but not because they're less satisfied — they have more job mobility and fewer personal anchors.

---

### Q4 — Marital Status vs Attrition

| Status | Attrition Rate | Avg Monthly Income |
|---|---|---|
| Single | 25.5% | ₹5,889 |
| Married | 12.5% | ₹6,793 |
| Divorced | 10.1% | ₹6,786 |

Single employees leave at more than double the rate of married ones. They tend to be younger, earn less, and have higher mobility — all of which make them more likely to switch for growth or better pay.

---

### Q5 — Training Impact on Attrition
Looks at attrition rates by number of training sessions attended in the past year.

| Sessions | Attrition Rate |
|---|---|
| 0 | 27.8% |
| 3 | 14.1% |
| 6 | 9.2% |

Training is one of the cheapest and most effective retention tools in this dataset. The spike at 4 sessions (21%) may point to overloaded employees — quality and relevance matter too, not just volume.

---

### Q6 — Work-Life Balance vs Performance Rating
Checks whether poor WLB shows up as lower performance scores.

Performance ratings are nearly identical across all WLB groups (3.14–3.18 out of 4). This likely reflects that manager-given ratings don't capture burnout well — people can perform fine on paper while quietly disengaging. Pulse surveys for the WLB=1 and WLB=2 groups would give a better read.

---

### Q7 — Stock Options vs Attrition

| Stock Level | Attrition Rate |
|---|---|
| 0 (None) | 24.4% |
| 1 (Basic) | 9.4% |
| 2 (Mid) | 7.6% |
| 3 (High) | 17.6% |

Going from zero stock options to even a basic allocation cuts attrition by more than half. Level 3 is an outlier — likely senior employees who get poached regardless of equity, and may need different retention levers (role scope, growth).

---

### Q8 — Tenure vs Job Satisfaction
Checks whether long-tenured employees lose satisfaction over time.

Satisfaction scores don't show a clear decline with tenure (range: 2.65–2.81). Attrition, however, tells a clearer story — it drops sharply from 29.8% in years 0-2 down to 6.5% by years 11-15. The real retention risk is the first two years, not long tenure.

---

### Q9 — Business Travel vs Job Satisfaction

| Travel | Attrition Rate |
|---|---|
| Non-Travel | 8.0% |
| Rarely | 15.0% |
| Frequently | 24.9% |

Frequent travelers don't report lower satisfaction, but they leave at 3x the rate of non-travelers. Travel seems to act as a tipping point factor rather than a direct satisfaction driver — it adds friction that pushes people out when something else isn't working.

---

### Q10 — Years Since Last Promotion vs Performance Rating
Checks whether employees who haven't been promoted recently show lower performance scores.

Performance ratings are essentially flat across all groups (3.13–3.17), including those who haven't been promoted in 6+ years. This could mean lack of promotion genuinely isn't hurting output — or that the rating scale is too compressed to detect subtle motivation dips. A pulse survey for the 6+ years group would be more informative than performance scores alone.

---

## Key Takeaways

1. **The first 2 years are the highest-risk window.** Almost 30% of new employees leave in years 0-2. Focus retention spend here.
2. **Job involvement is the strongest lever.** Disengaged employees leave at 3.7x the rate of highly involved ones. Pulse surveys and meaningful work assignments are worth prioritizing.
3. **Training works.** Going from 0 to 6 training sessions cuts attrition from 28% to 9%. Mandate at least 3 sessions per employee per year.
4. **Basic stock options have a big impact.** Extending Level 1 equity to the 631 employees currently at Level 0 is probably the highest-leverage, lowest-cost fix on this list.
5. **Frequent travelers are a silent attrition risk.** They represent ~19% of the workforce but leave at nearly 25% — worth addressing with travel caps or comp-off policies.
6. **Satisfaction scores look similar across age, tenure, and WLB groups.** That means these metrics alone won't catch who's at risk — pair them with attrition data and pulse surveys for a fuller picture.

---

## Data Source

IBM HR Analytics Employee Attrition dataset, applied to an Adecco India HR analysis context. Dataset includes 1,470 employee records with 35 attributes covering demographics, compensation, job characteristics, satisfaction scores, and attrition status.
