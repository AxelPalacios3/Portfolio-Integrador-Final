# Case 01 – Customer Satisfaction Factor Analysis (TechnoServe Solutions)

This folder contains the analysis for **Case 01** of the MA2003B portfolio.  
The goal is to use **Exploratory Factor Analysis (EFA)** to identify latent dimensions that explain how clients evaluate the service provided by **TechnoServe Solutions**.

---

## 1. Business Problem

TechnoServe Solutions collected a **customer satisfaction survey** from B2B clients.  
The survey contains many items that ask about different aspects of the service (communication, project delivery, technical quality, pricing, support, etc.).

Having too many individual questions makes it difficult for managers to:

- See the **big picture** of client experience.
- Design **focused KPIs** instead of tracking every single item.
- Prioritize **improvement initiatives** on the most relevant dimensions.

**Objective:**  
Use **Factor Analysis** to reduce the survey into a smaller number of **latent factors** that summarize the main dimensions of satisfaction, and translate them into actionable insights for management.

---

## 2. Data Description

- **Unit of analysis:** one row = one client / one completed survey.
- **Variables:**
  - Multiple **Likert-type items** (e.g., 1–10 or 1–5 scale).
  - Items cover topics such as:
    - Technical competence of the team.
    - Communication and responsiveness.
    - Project management and delivery.
    - Pricing and perceived value for money.
    - Post-delivery support and guarantee.
- **Target:**  
  There is no dependent variable. The goal is **structure discovery**, not prediction.

(For exact variable names, see the first section of the notebook.)

---

## 3. Methodology

All the steps are implemented and documented in the notebook:

**`factor_analysis.ipynb`**

### 3.1 Data Preparation

- Load the dataset from the provided source.
- Inspect basic summary statistics (mean, variance, missing values).
- Drop or impute records/columns with excessive missing data (if any).
- Standardize or scale items where appropriate so that all questions are on a comparable scale.

### 3.2 Suitability Checks

Before running factor analysis, we check whether the survey is suitable for EFA (conceptually and/or computationally), for example:

- Correlation matrix: look for meaningful correlations between items.
- (Optional, depending on the notebook) KMO / Bartlett’s test to support factorability.

### 3.3 Factor Extraction

- Choose a factor extraction method (e.g., **Principal Axis Factoring** or similar).
- Decide the **number of factors** based on:
  - Eigenvalues (e.g., > 1 rule).
  - Scree plot.
  - Interpretability of the factors.
- Extract factors and compute **factor loadings**.

### 3.4 Rotation and Interpretation

- Apply an appropriate rotation (e.g., **varimax** for orthogonal rotation) to obtain clearer loadings.
- Inspect which items load highly on each factor.
- Give each factor a **business-friendly name** based on its items. For example (illustrative):

  - **F1 – Technical Quality & Expertise**  
  - **F2 – Relationship & Communication**  
  - **F3 – Project Delivery & Planning**  
  - **F4 – Pricing & Perceived Value**  
  - **F5 – Post-delivery Support**

- (Optional) Compute **factor scores** for each respondent to compare clients across factors.

---

## 4. Key Findings (Executive Summary)

At a high level, the factor analysis shows that:

- The many survey questions can be summarized into a **small number of interpretable factors**.
- Each factor groups items that “move together”, revealing **coherent dimensions** of client experience.
- Some factors explain more variance than others, indicating which aspects contribute most to overall satisfaction.
- Certain items may have low loadings or cross-loadings, suggesting they might be:
  - Redundant, or  
  - Not clearly associated with a single dimension.

(For exact loadings, percentages of variance explained and factor names, see the relevant tables and plots inside the notebook.)

---

## 5. Business Implications & Recommendations

Based on the factor structure, TechnoServe Solutions can:

1. **Design high-level KPIs by factor**  
   - Instead of tracking 20+ individual items, define dashboards around 4–5 key dimensions (e.g., Technical Quality, Communication, Delivery, Value, Support).

2. **Focus improvement efforts**  
   - Identify which factor scores are lower on average and prioritize those dimensions in action plans (training, process redesign, better communication, etc.).

3. **Segment clients by factor scores**  
   - Analyze which clients or segments (by industry, size, region) have lower scores in specific factors to design **targeted interventions**.

4. **Refine the survey instrument**  
   - Drop or reword items with poor or confusing loadings.
   - Keep a **reduced, more efficient questionnaire** that still captures the core dimensions of satisfaction.

---

## 6. File Structure (Case 01)

This folder contains:

- `README.md` – This file (executive summary and documentation).
- `factor_analysis.ipynb` – The main notebook with all the code, analysis, tables and visualizations for Case 01.

---

## 7. How to Run the Notebook

1. Install the project dependencies from the root of the repository:

   ```bash
   pip install -r requirements.txt
## Resources and Deliverables

| Resource           | Link |
|--------------------|------|
| Main notebook      | [`factor_analysis.ipynb`](factor_analysis.ipynb) |
| Dataset            | [`customer_satisfaction_data.csv`](customer_satisfaction_data.csv) |
| Executive summary  | [`executive_summary_team_5__pdf.pdf`](executive_summary_team_5__pdf.pdf) |
| Presentation video | [YouTube](https://www.google.com/url?q=https%3A%2F%2Fyoutu.be%2FzWHmeM03y9s%3Fsi%3DJi_EV-GlsqSTPz2U%255D) |
