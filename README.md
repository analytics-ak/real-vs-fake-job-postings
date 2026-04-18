<div align="center">

# Real vs. Fake Job Posting Analysis

**Python | Pandas | Matplotlib | Seaborn**

Analyzed 17,880 job listings to find what separates fake posts from real ones — and built a simple Trust Score system to flag suspicious listings before they reach job seekers.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/analytics-ak/real-vs-fake-job-postings/blob/main/scam_job_detection_and_risk_analysis.ipynb)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/analytics-ak/real-vs-fake-job-postings/main?labpath=scam_job_detection_and_risk_analysis.ipynb)

</div>

---

## The Short Version

866 out of 17,880 job postings in this dataset are fake. That is 4.8% — and at the scale of a real job platform serving millions of listings, that means hundreds of thousands of fake posts reaching real job seekers every year.

The problem is not identifying that fake posts exist. The problem is catching them before they go live — fast enough to scale, without slowing down legitimate employers.

This analysis finds the five signals that consistently separate fake posts from real ones, and turns them into a scoring system any platform can implement without machine learning.

---

## The Core Finding

**A post with no company logo, no company profile, a short description, and suspicious keywords has a 66.7% chance of being fake — up from a 4.8% baseline.**

That jump is achieved using four simple checks. No model training. No complex infrastructure. Just pattern-based rules derived directly from the data.

---

## How Fraud Rate Climbs as Red Flags Stack

This is the most important finding in the entire analysis.

| Red Flag Combination | Fraud Rate |
|---|---|
| All jobs (baseline) | 4.8% |
| No company logo | 15.9% |
| No logo + no profile | 21.8% |
| + Short description | 26.7% |
| + Suspicious keywords | **66.7%** |

Individual signals are useful. Combined, they become a reliable detection system.

![Stacked Red Flags](images/risk_factor_bold_high_res.png)

---

## What the Data Shows

### Missing company info is the strongest single signal

Real companies show who they are. Scammers hide. Fake posts almost never include a company logo or profile — and that pattern holds consistently across the entire dataset.

![Company Logo Comparison](images/company_logo_comparison_high_res.png)
![Missing Company Profile](images/missing_company_profile_fraud_high_res.png)

---

### Fake descriptions are short and vague

Real job posts are detailed. Scammers do not bother writing thorough role descriptions. Real company profiles average ~96 words. Fake ones average ~32 words.

Short profile + vague language = significantly higher fraud risk.

![Description Length](images/description_length_fixed_legend.png)

---

### Suspicious keywords appear 3x more in fake posts

Words like "easy money," "fast cash," "urgent," and "work from home" appear in ~12% of fake posts vs ~4% of real ones. One keyword alone is not enough. Two or more together is a strong signal.

---

### Missing fields compound the risk

A single missing field is normal — not every employer fills everything in. But four or more missing fields is a pattern. The fraud rate drops sharply as post completeness goes up.

![Completeness Score](images/completeness_vs_fraud_rate.png)

---

### Salary presence is not a safety signal

This one is counterintuitive. Posts that include salary details actually have a slightly higher fraud rate. Some scammers add fake salary ranges to look more convincing. Salary presence alone tells you nothing.

![Salary vs Fraud](images/salary_transparency_fraud_rate.png)

---

### Remote job claims carry slightly higher risk

Fake listings lean toward remote claims because it widens the target audience. Not a strong standalone signal — but it contributes to the overall score.

![Telecommuting](images/telecommuting_comparison_high_res.png)

---

### Employment type does not matter

Fake posts are spread evenly across full-time, part-time, contract, and other types. This is not a useful filter.

![Employment Type](images/employment_type_distribution_high_res.png)

---

## The Trust Score System

Based on these patterns, a simple five-point scoring system can flag risky posts at submission time — before they go live.

| Signal | Red Flag Condition | Points |
|---|---|---|
| Company logo | Missing | +1 |
| Company profile | Missing or blank | +1 |
| Description length | Below minimum character threshold | +1 |
| Suspicious keywords | Contains 2+ flagged words | +1 |
| Missing fields | 3+ fields left blank | +1 |

**How the score works:**

| Score | Risk Level | Action |
|---|---|---|
| 0–1 | Low | Post goes live immediately |
| 2–3 | Medium | Flag for quick review |
| 4–5 | High | Hold for manual review before publishing |

This check runs in milliseconds. It catches most fake posts without creating any friction for real employers who fill in their details properly — which they naturally do.

---

## What Should Be Done

**Action 1 — Make company identity fields mandatory**

Require company name, logo upload, and profile description at submission. This single change blocks the most common pattern in fake posts. Real employers already provide this information. Scammers cannot fake it without effort.

**Action 2 — Set minimum content standards**

Add a minimum character count for job descriptions and requirements. A floor of 200–300 characters filters out the laziest scams without affecting real listings.

**Action 3 — Deploy the Trust Score at submission**

Build the five-signal scorer as a pre-publication check. Posts scoring 4–5 go to manual review. Posts scoring 2–3 get flagged in the moderation queue. This scales without needing a dedicated fraud team reviewing every listing.

These three changes require no machine learning, no model retraining, and no complex infrastructure. They are implementable immediately.

---

## What Did Not Matter

| Factor | Result |
|---|---|
| Employment type | Fake posts spread evenly across all types — not a useful filter |
| Salary presence | Slightly higher fraud rate in posts with salary — counterintuitive and unreliable |
| Remote work alone | Slightly elevated risk but too weak to use as a standalone signal |

Testing and ruling these out is just as important as finding what does work.

---

## Data Quality

Before any analysis, the data was validated:

- Missing values identified and handled across all 18 columns
- Text fields with blanks filled as "Unknown" for consistency
- Binary flags created for missing company info, salary, location, education, and industry
- All features validated before being used in scoring

---

## Dataset

| Detail | Info |
|---|---|
| **Source** | [Kaggle — Real or Fake Job Posting Prediction](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction) |
| **Total Rows** | 17,880 |
| **Fake Posts** | 866 (4.8%) |
| **Columns** | 18 |
| **Type** | Mix of text fields and binary flags |

---

## Tools Used

| Tool | Used For |
|---|---|
| Python | Data cleaning, feature engineering, scoring logic |
| Pandas | Data manipulation and grouping |
| NumPy | Numerical operations |
| Matplotlib | All charts and visualizations |
| Seaborn | Statistical plots and styled visuals |
| Jupyter Notebook | Full end-to-end analysis |

---

## Project Structure

```
fake-job-detection/
│
├── scam_job_detection_and_risk_analysis.ipynb  ← Full analysis notebook
├── README.md                                    ← You are reading this
│
└── images/
    ├── missing_data_chart_high_res.png
    ├── real_vs_fake_jobs_high_res.png
    ├── top_missing_columns_high_res.png
    ├── company_logo_comparison_high_res.png
    ├── telecommuting_comparison_high_res.png
    ├── employment_type_distribution_high_res.png
    ├── missing_company_profile_fraud_high_res.png
    ├── description_length_fixed_legend.png
    ├── salary_transparency_fraud_rate.png
    ├── completeness_vs_fraud_rate.png
    └── risk_factor_bold_high_res.png
```

---

## How to Run This

1. Clone this repo
   ```bash
   git clone https://github.com/analytics-ak/real-vs-fake-job-postings.git
   ```
2. Install required libraries
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open the notebook
   ```bash
   jupyter notebook scam_job_detection_and_risk_analysis.ipynb
   ```
4. Run all cells — charts generate automatically

---

## Conclusion

Fake job posts are not sophisticated. They are lazy — missing logos, missing profiles, short descriptions, and obvious keyword patterns. The data shows this consistently across the entire dataset.

The five signals identified here are enough to catch most fraud at submission time, before a single job seeker sees the listing. No model training required. No complex infrastructure. Just pattern-based rules that work because scammers consistently cut corners in the same places.

This analysis shows that fraud detection does not have to be complicated to be effective — it has to be applied at the right point in the process.

---

## Author

**Ashish Kumar Dongre**

🔗 [LinkedIn](https://www.linkedin.com/in/analytics-ashish/) &nbsp;|&nbsp; 💻 [GitHub](https://github.com/analytics-ak/real-vs-fake-job-postings) &nbsp;|&nbsp; 📂 [Dataset on Kaggle](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction)
