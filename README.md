# Real vs Fake Job Posting Analysis  
*This project explores patterns in real and fake job listings using data analysis in Python.*  

---

## Project Overview  
This project looks at **17,880 job posts** to understand how fake jobs differ from real ones.  
The main idea is to study how scammers create fake job ads and find simple ways to catch them early.  

Fake job postings waste people’s time, mislead job seekers, and lower trust in online job platforms.  
By finding patterns in the data, we can identify warning signs that often appear in fake job posts and build steps to stop them.  

---

## Objectives  
The goal of this analysis is to clearly show what makes a fake job post look different from a real one.  
With these findings, we can suggest simple steps that can:  
- Identify risky job posts early.  
- Protect job seekers from scams.  
- Build more trust between job seekers and job platforms.  

---

## Why This Project Matters  
Many people apply for jobs online, but not every listing is real.  
A single fake post can waste hours of effort or even lead to personal data theft.  
This project helps highlight patterns that separate fake job posts from real ones.  

> **Quick Insight:** Fake job posts often skip company details, use vague descriptions, and promise easy work-from-home opportunities.  

---

## Dataset  
- **Source:** [Kaggle – Fake Job Postings Dataset](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction)  
- **File Used:** `fake_job_postings.csv`  
- **Size:** 17,880 rows and 18 columns  

**Main Columns:**  
`title`, `location`, `company_profile`, `description`, `requirements`, `telecommuting`,  
`has_company_logo`, `employment_type`, `industry`, and `fraudulent` (1 = fake, 0 = real).  

The dataset contains both real and fake job posts, allowing comparisons based on company info, job descriptions, and key text patterns.  

---

## Tools and Libraries Used  
- **Python:** Main language for analysis.  
- **Pandas:** For cleaning and handling data.  
- **NumPy:** For calculations.  
- **Matplotlib & Seaborn:** For charts and visual analysis.  
- **WordCloud:** To show common words used in fake and real job posts.  

---

## Project Steps  

### 1. Loading and Cleaning the Data  
The dataset was loaded into a Pandas DataFrame.  
Columns like company profile, salary, department, and industry had missing values, which were filled with “Unknown” for easy comparison.

### 2. Creating New Features  
New features were added to study patterns:  
- `desc_length` – word count in job description.  
- `req_length` – word count in requirements.  
- `company_missing` – marks if the company profile was missing.

### 3. Exploring the Data  
Charts were created to compare real and fake posts on fields such as company info, salary, job type, and text length.  
Word clouds were also generated to see common terms used in both categories.  

> **Quick Insight:** Fake job descriptions are usually short and use words that sound too easy or appealing.

---

## Key Findings  

### 1. Real vs Fake Ratio  
<p align="center">
  <img src="Real%20vs%20Fake.png" alt="Real vs Fake Job Posts" width="600"/>
</p>
<p align="center"><i>Chart showing the number of real vs fake job postings.<br>Fake jobs are fewer in number but still cause major issues for job seekers.</i></p>

Out of **17,880** jobs, only about **4.8%** were fake.  
Even though fake jobs are a small percentage, they create big trust problems on job platforms.  

---

### 2. Missing Information  
<p align="center">
  <img src="Company%20Logo%20Presence.png" alt="Company Logo Presence" width="600"/>
</p>
<p align="center"><i>Chart comparing presence of company logos in real and fake job posts.<br>Fake jobs often skip company logos, while real jobs almost always include them.</i></p>

<p align="center">
  <img src="Missing%20Company%20Profile.png" alt="Missing Company Profile" width="600"/>
</p>
<p align="center"><i>Chart comparing missing company profiles.<br>Fake posts are more likely to hide company details or profiles.</i></p>

> **Quick Insight:** Missing company logo and profile are strong signs of suspicious or fake job listings.  

---

### 3. Short or Vague Text  
<p align="center">
  <img src="Job%20Description%20Length.png" alt="Job Description Length" width="600"/>
</p>
<p align="center"><i>Boxplot comparing job description lengths.<br>Fake posts have shorter descriptions and fewer details.</i></p>

<p align="center">
  <img src="Requirements%20Length.png" alt="Requirements Length" width="600"/>
</p>
<p align="center"><i>Chart showing word count in requirements.<br>Fake jobs list fewer skills or give unclear requirements.</i></p>

> **Quick Insight:** Real companies write longer, more detailed job descriptions and mention skills clearly.  

---

### 4. High-Risk Categories  
<p align="center">
  <img src="Telecommuting%20Jobs.png" alt="Telecommuting Jobs" width="600"/>
</p>
<p align="center"><i>Chart comparing remote vs on-site jobs.<br>Fake jobs are slightly more likely to advertise remote or “work from home” roles.</i></p>

<p align="center">
  <img src="Employment%20Type.png" alt="Employment Type" width="600"/>
</p>
<p align="center"><i>Employment type comparison.<br>Fake jobs often list “Unknown” or misleading types.</i></p>

<p align="center">
  <img src="Top%20Industries.png" alt="Top Industries" width="600"/>
</p>
<p align="center"><i>Fraud rate by industry.<br>Industries like Oil & Energy and Telecom show higher fake job activity.</i></p>

> **Quick Insight:** Some industries attract more fake postings, especially where jobs sound flexible or high-paying.  

---

### 5. Red Flag Words  
<p align="center">
  <img src="Word%20Cloud%20for%20Fake.png" alt="Fake Job Word Cloud" width="600"/>
</p>
<p align="center"><i>Word cloud for fake job descriptions.<br>Shows common terms like “work from home”, “quick money”, and “no experience”.</i></p>

<p align="center">
  <img src="Word%20Cloud%20for%20Real.png" alt="Real Job Word Cloud" width="600"/>
</p>
<p align="center"><i>Word cloud for real job descriptions.<br>Highlights words like “team”, “development”, and “project”.</i></p>

> **Quick Insight:** Fake job descriptions sound attractive but lack specific job details, while real posts use professional and role-based language.  

---

## Quick Insights Summary  
> **1.** Fake job posts skip company logos and profiles.  
> **2.** Short, vague descriptions are a warning sign.  
> **3.** Certain industries like Oil & Energy or Telecom have more fake listings.  
> **4.** Fake posts often include words like “work from home” or “quick money.”  
> **5.** The more fields missing in a post, the higher the fraud risk.  
> **6.** Real job posts are longer and more detailed, showing clear requirements.  

---

## Recommendations  
- Make company name, logo, salary, and location **mandatory fields** in job postings.  
- Add a **minimum word limit** for job descriptions.  
- Use a simple **“Trust Score”** to flag posts missing important details.  
- Watch for **red-flag keywords** such as “quick money” or “no experience needed.”  
- Apply extra checks for **high-risk industries** like Oil & Energy and Telecom.  
- Share short **safety reminders** with job seekers (for example, “Be cautious of jobs that sound too good to be true”).  
- Review and update the fraud-detection rules regularly.  

---

## Future Work  
- Create a small web tool where users can paste a job post and get a quick “real or fake” rating.  
- Use deeper text analysis to detect patterns across industries and roles.  
- Check how fake job trends change over time.  
- Test these methods on newer datasets to confirm consistent patterns.  

---

## Project Summary and Conclusion  
This analysis of **17,880 job postings** clearly shows that fake job posts follow a predictable pattern.  
They often skip company details, use short descriptions, and rely on catchy or vague words.  

Even without complex models, simple checks — like verifying company info, checking text length, and spotting certain keywords — can stop fake listings before they reach users.  
These small steps help protect job seekers, save time, and make online hiring safer.  

> **Quick Insight:** Data analysis can be used in practical ways to improve user safety and build trust in digital hiring systems.  

---

## How to Run This Project  
1. Download the dataset from [Kaggle](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction).  
2. Place it inside a `data` folder.  
3. Open `Job_post.ipynb` in Jupyter Notebook or VS Code.  
4. Run all cells in order to reproduce the analysis and visuals.  

---

## Profile & Dataset

* 🔗 **LinkedIn:** [View My Profile](https://www.linkedin.com/in/analytics-ashish/)
* 📂 **Dataset:** [Real VS Fake Jobs Prediction Dataset on Kaggle](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction)
* 💻 **GitHub Repository:** [Real VS Fake Job Postings Analysis](https://github.com/analytics-ak/real-vs-fake-job-postings)
* 📘 **Notebook:** [Job_post.ipynb](https://github.com/analytics-ak/funnel-drop-analysis/blob/main/funnel-drop.ipynb)

<br>

## Author: Ashish Kumar Dongre — Senior Data Analyst
I love working with data and finding simple insights that help businesses grow. Skilled in **Python (Jupyter, pandas, seaborn, matplotlib, Wordcloud)**, and experienced in turning raw data into clear, useful reports.

--- 
**End of README**

