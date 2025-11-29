# MA2003B – Multivariate Methods Portfolio (Team 5)

This repository contains the integrative portfolio for the course **Application of Multivariate Methods in Data Science (MA2003B)**.  
It compiles three business-oriented case studies using **Factor Analysis**, **Discriminant Analysis** and **Cluster Analysis**, each documented in its own folder and summarized in this central README.

---

## 1. Team Information

**Team:** Team 5  

**Members:**

- Cristian Cruz Orozco – A01665590 – Data Science and Mathematics Engineering  
- Alan Ulises Luna Hernández – A01424523 – Data Science and Mathematics Engineering  
- Axel Palacios Granados – A01666972 – Data Science and Mathematics Engineering  

---

## 2. Case Overview

| Case | Folder                          | Business Context                                        | Main Technique           | Main Outcome |
|------|---------------------------------|---------------------------------------------------------|--------------------------|-------------|
| 1    | `case-01-factor-analysis/`      | Customer satisfaction survey for **TechnoServe Solutions** (B2B services). :contentReference[oaicite:0]{index=0} | Exploratory **Factor Analysis** | Identification of 5 latent factors that explain how clients evaluate technical quality, relationship, project delivery, pricing/value and post-delivery support. |
| 2    | `case-02-discriminant-analysis/`| Credit risk modeling for **LendSmart** (FinTech loans). :contentReference[oaicite:1]{index=1} | **Linear/Quadratic Discriminant Analysis** | LDA/QDA models that perfectly separate defaulters vs. non-defaulters on the test set, enabling a data-driven credit approval policy. |
| 3    | `case-03-cluster-analysis/`     | Customer segmentation for **MegaMart** (retail). :contentReference[oaicite:2]{index=2} | **Cluster Analysis** (behavioral segmentation) | Four interpretable customer segments (e.g., High-Value Loyalists, Big-Basket Planners, etc.) and targeted strategies for each group. |

---

## 3. Methodological Comparison  
**Factor Analysis vs. Discriminant Analysis vs. Cluster Analysis**

### 3.1 Conceptual Focus

| Aspect              | Factor Analysis                                      | Discriminant Analysis                                        | Cluster Analysis                                           |
|---------------------|------------------------------------------------------|--------------------------------------------------------------|-----------------------------------------------------------|
| Main goal           | Reduce many observed variables into a smaller set of latent factors. | Classify observations into predefined groups using predictors. | Discover **unknown** groups based on similarity patterns. |
| Type of problem     | **Dimension reduction** / structure discovery.      | **Supervised classification** (known labels).                | **Unsupervised segmentation** (no labels).                |
| Typical question    | “What hidden dimensions explain how clients respond to this survey?” | “Given these variables, is this client low or high risk?”     | “What types of customers do we have, and how do they differ?” |

### 3.2 Data and Inputs (in this portfolio)

- **Factor Analysis (Case 1 – TechnoServe)** :
  - 23 satisfaction items from a B2B client survey.  
  - Continuous Likert-scale variables (1–10 style).  
  - Objective: detect coherent dimensions of service experience.

- **Discriminant Analysis (Case 2 – LendSmart)** :
  - Financial and sociodemographic variables (income, credit score, debt-to-income ratio, utilization, etc.).  
  - Binary outcome: **default vs. non-default**.  
  - Objective: estimate probability of default and support credit decisions.

- **Cluster Analysis (Case 3 – MegaMart)** :
  - Behavioral metrics: purchase frequency, basket size, total spend, campaign response, returns, recency.  
  - No predefined labels.  
  - Objective: build meaningful customer segments for marketing strategy.

### 3.3 Model Output and Interpretation

| Aspect          | Factor Analysis                               | Discriminant Analysis                                  | Cluster Analysis                                      |
|-----------------|-----------------------------------------------|--------------------------------------------------------|------------------------------------------------------|
| Output objects  | Factor loadings, communalities, factor scores | Discriminant functions, classification rules, metrics  | Cluster centers, cluster sizes, profiles             |
| What we read    | Which variables “move together” and form factors. | How variables separate classes (low vs high risk).      | How each segment behaves (high-value, at-risk, etc.). |
| Business use    | Design KPIs by factor (technical quality, relationship, value, etc.). | Approve/reject loans and adjust conditions by risk level. | Personalize promotions and resource allocation by segment. |

### 3.4 Strengths and Limitations (in our experience)

- **Factor Analysis**
  -  Strengths:  
    - Reduces complexity of long surveys into a manageable set of dimensions.  
    - Helps translate noisy items into business language (e.g., “technical excellence”, “relationship & trust”). : 
  -  Challenges:  
    - Requires decisions about number of factors and rotation.  
    - Interpretation depends on theory and context; loadings are not always “clean”.

- **Discriminant Analysis**
  -  Strengths:  
    - Clear separation of good vs. bad clients in LendSmart; excellent performance (AUC ~ 1.0). :
    - Easy to communicate to risk teams once the key drivers are identified.  
  -  Challenges:  
    - Assumptions about distributions and covariance structures.  
    - Risk of overfitting if performance is not monitored in production.

- **Cluster Analysis**
  -  Strengths:  
    - Naturally generated segments with intuitive business meaning (High-Value Loyalists, Big-Basket Planners, Everyday Value Seekers, At-Risk Occasionals). :
    - Direct link to marketing strategies and resource focus.  
  -  Challenges:  
    - Choosing number of clusters and validating stability.  
    - Segments must be revisited as behavior changes over time.

---

## 4. Lessons Learned & Acknowledgements

### 4.1 Technical Lessons Learned

- **Data preparation matters more than expected.**  
  Across the three cases we spent a significant amount of time cleaning data, handling missing values, scaling variables and checking distributions. Good preprocessing was essential for stable factors, robust discriminant functions and meaningful clusters.

- **Modeling is iterative, not linear.**  
  We often had to go back and forth between **exploration, modeling and interpretation**:
  - Adjusting the number of factors and checking the variance explained in Case 1. :
  - Comparing LDA and QDA, and confirming that performance was not just an artifact of the split in Case 2. :
  - Testing different values of *k* and features for clustering in Case 3. :

- **Evaluation is context-dependent.**  
  Accuracy, AUC, variance explained or silhouette scores only make sense when connected to business decisions:
  - In credit risk, avoiding false approvals is more critical than a purely symmetric metric.  
  - In segmentation, interpretability and business actionability are as important as numerical scores.

- **Narrative + code is mandatory.**  
  A notebook that “runs” is not enough. We needed to:
  - Document assumptions and decisions in Markdown.  
  - Explain each result using business language and not just statistical jargon.  
  - Make the analysis reproducible with `requirements.txt` and a clean repository structure.

### 4.2 Interpretative & Communication Lessons

- We learned to **translate multivariate results into stories**:
  - Factors became “moments of the service” (know, attend, deliver, charge, support). 
  - Discriminant functions became “profiles of low vs. high risk borrowers”. 
  - Clusters became “personas” with clear behaviors and strategies. 

- We practiced explaining complex outputs to **non-technical stakeholders**:
  - What does it mean that variance explained is ~50 %?  
  - Why is a model with AUC = 1.0 still something that must be monitored?  
  - Why not all customers should receive the same promotion?

This pushed us to design clearer visuals, concise executive summaries and explicit business recommendations.

### 4.3 Additional Reflection: Acknowledgements

We would like to close this portfolio by expressing our gratitude to:

- **Tecnológico de Monterrey**  
  For providing the academic environment, data sets and tools to work on realistic, business-oriented problems using multivariate methods.

- **Professors of MA2003B**  
  Especially for their guidance in connecting the mathematical foundations with practical decision-making. Their feedback helped us refine our analysis, improve our modeling choices and communicate results more clearly.

- **Our teammates**  
  Collaboration was essential for this portfolio. Each case required splitting responsibilities (EDA, modeling, validation, storytelling) and then integrating everything into a coherent narrative. Working together allowed us to go deeper than we could have individually, and to learn from each other’s strengths.

---

**Repository status:**  
If all checkboxes from the course checklist are satisfied (public repo, clean root, dependency file, structured folders and runnable, documented notebooks), this portfolio should be considered **Complete** under the MA2003B evaluation criteria.
