# Team members 
- Axel Palacios Granados A01666972  
- Alan Ulises Luna Hernandez A01424523  
- Cristian Cruz Orozco A01665590  

# Case 01 – Customer Satisfaction Factor Analysis (TechnoServe Solutions)

This folder contains the analysis for **Case 01** of the MA2003B portfolio.  
The goal is to use **Exploratory Factor Analysis (EFA)** to identify latent dimensions that explain how clients evaluate the service provided by **TechnoServe Solutions** and to translate those patterns into concrete management recommendations.

---

## 1. Business Problem

TechnoServe Solutions collected a **customer satisfaction survey** from B2B clients.  
The questionnaire includes many items that ask about different aspects of the service (technical quality, project delivery, communication, pricing, support, etc.).

With 20+ questions, managers face three issues:

- It is hard to see the **big picture** of the client experience.  
- It is difficult to design **clear KPIs**, because each indicator only reflects one item.  
- It is not obvious **where to intervene first** to increase renewals and recommendations.

**Objective**  
Use **Factor Analysis** to reduce the 23 survey items into a smaller number of **latent factors** that summarize how clients really evaluate the service, and use those factors to guide improvements and renewal strategies.

---

## 2. Data Description

- **Unit of analysis:**  
  One row = one client / one completed survey.

- **Variables:**
  - **23 satisfaction items**, measured on Likert-type scales.
  - Items grouped conceptually in:
    - Technical capabilities and solution quality.
    - Relationship and access to executives.
    - Project management and delivery.
    - Billing, value and ROI.
    - Post-delivery support and training.

- **Target variable:**  
  There is **no single dependent variable**. The goal is to uncover the **structure** behind the answers, not to predict a specific outcome.

(Exact variable names and coding can be found in the first section of the notebook.)

---

## 3. Methodology

All steps are implemented and documented in:

**`factor_analysis.ipynb`**

### 3.1 Data Preparation

- Load the survey dataset.
- Compute descriptive statistics for each item (mean, standard deviation, missing values).
- Check for inconsistent or extreme responses.
- Work with complete cases and ensure items are on comparable scales for the factor analysis.

### 3.2 Factor Extraction

- Apply **Exploratory Factor Analysis (EFA)** with **Varimax rotation**.
- The analysis separates **5 factors** that together explain **50.7%** of the total variance  
  (13.8% + 11.4% + 11.4% + 9.6% + 4.5%).
- The structure is **not random**: it aligns with how the company actually delivers its service, so the questionnaire can be used as a base for **management indicators**.

### 3.3 Factors Identified

**Factor 1 – Technical Excellence (13.8%)**  
Highest loadings on:

- `innovation_solutions` (0.72)  
- `problem_solving` (0.71)  
- `system_integration` (0.71)  
- `technical_expertise` (0.69)  
- `technical_documentation` (0.69)

This factor represents the ability to **know**, **solve**, **integrate** and **document**.  
If this component goes down, the company stops being perceived as a **technical partner**.

---

**Factor 2 – Relationship, Access & Trust (11.4%; cumulative 25.2%)**  
Highest loadings on:

- `executive_access` (0.63)  
- `trust_reliability` (0.64)  
- `long_term_partnership` (0.63)  
- `communication_clarity` (0.62)  
- `account_manager_responsive` (0.61)

Here the client is evaluating whether they are **properly attended**, whether they can **escalate issues**, and whether there is a **long-term relationship**.  
This is the most delicate block for **NPS and recommendations**.

---

**Factor 3 – Project Delivery & Fulfillment (11.4%; cumulative 36.6%)**  
Highest loadings on:

- `project_management` (0.65)  
- `quality_deliverables` (0.64)  
- `timeline_adherence` (0.63)  
- `budget_control` (0.62)  
- `change_management` (0.62)

This factor answers the question:  
> “Did you deliver what we agreed, on time and within budget?”

It is the factor **most closely related to renewal**, because it captures whether expectations were met in execution.

---

**Factor 4 – Value, Price & ROI (9.6%; cumulative 46.2%)**  
Highest loadings on:

- `billing_accuracy` (0.61)  
- `roi_demonstration` (0.58)  
- `competitive_pricing` (0.57)  
- `cost_transparency` (0.57)  
- `value_for_money` (0.53)

Clients clearly distinguish between the **service experience** and the **economic experience**.  
If value is not explained properly, renewal becomes weaker **even when the project itself went well**.

---

**Factor 5 – Post-delivery Support & Training (4.5%; cumulative 50.7%)**  
Highest loadings on:

- `training_quality` (0.46)  
- `support_responsiveness` (0.44)  
- `documentation_help` (0.42)

This factor keeps the account “alive” **after delivery** and strongly influences **referrals** and **word-of-mouth**.

---

### 3.4 Overall Structure

The data show that clients do not evaluate just one attribute, but **five “moments” of the service**:

1. That the company **knows** (technical excellence).  
2. That they **take care** of the client and are accessible (relationship & trust).  
3. That they **deliver** what was promised (project fulfillment).  
4. That they **charge transparently** and demonstrate value (price & ROI).  
5. That they **do not disappear** after delivery (support & training).

Improving only one moment does **not guarantee better overall performance or renewal**.  
For example:

- If the technical side (Factor 1) improves but the relationship (Factor 2) does not, recommendations do **not** increase.  
- If the relationship (Factor 2) improves but delivery (Factor 3) does not, the client still hesitates to renew.  
- If delivery (Factor 3) is good but value (Factor 4) is not clearly explained, the typical objection is:  
  > “It was too expensive.”

---

## 4. Business Implications & Recommendations

Based on the factor structure, TechnoServe Solutions can move from a long list of items to **five concrete levers** of satisfaction and renewal.

### 4.1 Strategic Use of the Factors

- Use each factor as a **KPI block** in dashboards and internal reviews.  
- Track factor scores by **client segment** (industry, size, geography) to detect specific weaknesses.  
- Translate factor scores into **account plans** (e.g., accounts with low Factor 2 need relationship and access improvements).

### 4.2 Priority Recommendations

1. **Standardize the relationship and access experience**  
   - Define internal response plans for account managers.  
   - Set a **minimum frequency of communication** with clients.  
   - Establish clear **escalation routes** with executives.  
   - This directly strengthens **Factor 2 (Relationship, Access & Trust)**, the most critical driver of confidence and NPS.

2. **Align execution with value communication**  
   - Close every project milestone with a **short value sheet** summarizing benefits, savings and impact.  
   - Explicitly connect **Factor 3 (Delivery & Fulfillment)** with **Factor 4 (Value, Price & ROI)**.  
   - This makes renewal conversations easier and reduces objections such as “it was too expensive”.

3. **Maintain strong post-delivery support**  
   - Formalize **fast support channels** (SLA, response times, contact points).  
   - Keep **documentation and training materials up to date**.  
   - This reinforces **Factor 5 (Post-delivery Support & Training)** and increases the likelihood of **referrals** from already satisfied accounts.

### 4.3 Expected Impact

If the three recommendations are implemented consistently, the expected effects are:

- **Improved overall satisfaction** across the five factors.  
- **Higher probability of renewal**, especially in accounts where delivery is solid but value/relationship/support are not yet aligned.  
- **Greater portfolio stability and more referrals**, as satisfied clients are more willing to recommend TechnoServe Solutions as a trusted technical partner.

---

## 5. File Structure (Case 01)

This folder contains:

- `README.md` – This file (executive summary and documentation).  
- `factor_analysis.ipynb` – Main notebook with all code, analysis, tables and visualizations for Case 01.  
- `customer_satisfaction_data.csv` – Dataset used in the analysis.  
- `executive_summary_team_5__pdf.pdf` – Original executive summary in PDF format.

---

## 6. How to Run the Notebook

1. From the root of the repository, install the project dependencies:

   ```bash
   pip install -r requirements.txt

## Resources and Deliverables

| Resource           | Link |
|--------------------|------|
| Main notebook      | [`customer_satisfaction_analysis_team[5].ipynb`](customer_satisfaction_analysis_team[5].ipynb) |
| Dataset            | [`customer_satisfaction_data.csv`](customer_satisfaction_data.csv) |
| Executive summary  | [`executive_summary_team_5__pdf.pdf`](executive_summary_team_5__pdf.pdf) |
| Presentation video | [YouTube](https://www.google.com/url?q=https%3A%2F%2Fyoutu.be%2FzWHmeM03y9s%3Fsi%3DJi_EV-GlsqSTPz2U%255D) |
