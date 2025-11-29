# Team members 
- Axel Palacios Granados A01666972  
- Alan Ulises Luna Hernandez A01424523  
- Cristian Cruz Orozco A01665590  

# Case 02 – LendSmart Credit Risk Discriminant Analysis

This folder contains the analysis for *Case 02* of the MA2003B portfolio.  
The goal is to use *Discriminant Analysis (LDA and QDA)* to model credit risk for *LendSmart*, a FinTech company that offers personal and small business loans.

---

## 1. Business Problem

LendSmart currently faces a *default rate of about 28%* of its loans.  
This level of default generates direct financial losses and a risk profile that management considers too high.

The company has historical information for *2,500 loan applicants*, including financial, credit and sociodemographic variables, as well as the final loan outcome (loan_status: default vs. non-default).

*Objective*  
Analyze the history of these 2,500 applicants to build a model that estimates the probability that a new applicant will default on their loan. With this model, LendSmart can:

- Support *approval/rejection decisions*.
- *Adjust loan conditions* (amount, interest rate, etc.) according to risk.
- Reduce overall default rates and improve portfolio profitability.

Two related statistical approaches were evaluated:

- *LDA – Linear Discriminant Analysis*  
- *QDA – Quadratic Discriminant Analysis*

The goal is to select the most suitable one for integration into the credit risk process.

---

## 2. Data Description

- *Unit of analysis:*  
  One row = one loan application (one applicant).

- *Key variables:*
  - *Credit score* (overall credit quality).
  - *Annual income*.
  - *Debt-to-income ratio (DTI)*.
  - *Credit utilization* (use of available credit lines).
  - Indicators of *payment history* and *job stability*.
  - *Sociodemographic variables*, such as education level and marital status.
  - *Target variable:*
    - loan_status  
      - 0 = non-default (loan paid on time)  
      - 1 = default (loan ended in non-payment)

There is no separate “training label” aside from loan_status; the task is *supervised classification* of applicants into low-risk and high-risk groups.

(Exact variable names and preprocessing steps are documented in the notebook.)

---

## 3. Methodology

All steps are implemented in:

**discriminant_analysis.ipynb**

### 3.1 Data Preparation

- Load and explore the historical dataset.
- Compute descriptive statistics and visualize key variables (distributions, group comparisons).
- Treat missing values and potential inconsistencies.
- Standardize or rescale numerical variables where appropriate to stabilize the discriminant models.

### 3.2 Exploratory Analysis

Using distribution plots and the correlation matrix, the team identifies *clear differences* between:

- Customers who *pay on time*, and  
- Customers who *default*.

Two profiles emerge.

#### Low-Risk Customer Profile (Non-default)

Customers who pay their loans on time tend to have:

- *High credit scores, typically between **680 and 780, with a median around **720*.  
- *Higher annual incomes, with median values around **75,000–80,000 USD*.  
- *Low debt-to-income ratios, generally between **0.15 and 0.40*.  
- *Moderate credit utilization*, i.e., they are not constantly at the limit of their lines.

#### High-Risk Customer Profile (Default)

Borrowers who default are characterized by:

- *Lower credit scores, concentrated between **500 and 650*.  
- *Lower annual incomes*, with a median clearly below the non-default group.  
- *High debt-to-income ratios, often in the **0.60–0.80* range.  
- *High credit utilization*, close to the limits of their credit lines.

---

### 3.3 Model Building: LDA and QDA

Two models are built and compared using the same set of predictors:

1. *Model A – Linear Discriminant Analysis (LDA)*  
2. *Model B – Quadratic Discriminant Analysis (QDA)*  

For each model:

- Split the data into *training* and *test* sets.
- Fit the model on the training data.
- Obtain predicted classes and probabilities of default on the test data.
- Evaluate performance using:
  - Confusion matrix.
  - Error rates.
  - ROC curves and *AUC*.

---

## 4. Key Findings (Executive Summary)

### 4.1 Drivers of Default

The *LDA model* confirms that the strongest drivers of default risk are:

- *Payment history*.  
- *Job stability*.  
- *Credit utilization*.  
- *Debt-to-income ratio (DTI)*.  
- *Overall credit score*.

A *strong payment history, **stable employment* and a *healthy level of debt* act as protective factors.  
In contrast, being close to the limit on credit lines and having a large share of income already committed to payments are *clear warning signs*.

Sociodemographic variables (such as education and marital status) show some groups with higher default rates (for example, High School level or Single/Widowed status), but their impact is *smaller compared to financial indicators*.

### 4.2 Model Performance and Selection

On the *test set* (customers not used for training), the two models (LDA and QDA) produce *exactly the same classification*:

- *367* customers who in reality did *not default* are classified as *low risk*.  
- *133* customers who *did default* are classified as *high risk*.  
- *0 false positives* (no high-risk customers misclassified as low risk).  
- *0 false negatives* (no defaulters misclassified as low risk).

The ROC curves for both models *overlap, with an **AUC of 1.0, confirming **perfect separation* on these historical test data.

Since LDA and QDA display the same performance, the selection is based on:

- *Ease of interpretation*, and  
- *Ease of implementation* in the business process.

Therefore, the *LDA model* is recommended as the *main technical model* for LendSmart’s credit risk evaluation.

---

## 5. Business Implications & Recommendations

### 5.1 Proposed Decision

The final recommendation is *“Go”*:

> *LendSmart should adopt the LDA model as a decision-support tool to evaluate credit applications.*

This model helps minimize the most costly scenario:

- *Approving loans that are very likely to default*,  

while keeping under control the risk of:

- *Rejecting good customers*,  

thanks to the strong separation observed in the historical data.

### 5.2 Suggested Next Steps

Although the historical results are very favorable, in real-world operations there will always be some errors. Therefore, the following steps are proposed:

1. *Pilot deployment*  
   - Deploy the LDA model initially in a *pilot phase*, comparing its recommendations with the current decisions of the risk team before fully integrating it into production.

2. *Monitoring and feedback loop*  
   - Establish *monthly monitoring* of:
     - The *actual default rate*, and  
     - The *good customers that the model may be rejecting*.  
   - Use this feedback to identify any systematic biases or drifts.

3. *Threshold adjustment according to risk appetite*  
   - Adjust the *decision threshold* (cut-off probability) according to LendSmart’s *risk appetite* and strategic goals (growth vs. protection).

### 5.3 Expected Impact

If implemented with monitoring and regular adjustments, the LDA model will allow LendSmart to:

- Reduce the overall *default rate*.  
- Improve the *profitability* of the loan portfolio.  
- Make credit approval criteria more *consistent* and *data-driven*.  

---

## 6. File Structure (Case 02)

This folder contains:

- README.md – This file (executive summary and documentation for Case 02).  
- discriminant_analysis.ipynb – Main notebook with code, analysis and visualizations.  
- lendsmart_credit_data.csv – Dataset used in the analysis (loan-level data).  
- Lendsmart.pdf – Original executive summary in PDF format.

---

## 7. How to Run the Notebook

1. From the root of the repository, install the project dependencies:

   ```bash
   pip install -r requirements.txt


## Resources and Deliverables

| Resource           | Link |
|--------------------|------|
| Main notebook      | [LendSmart(2).ipynb](LendSmart(2).ipynb) |
| Dataset            | [credit_risk_data-1.csv](credit_risk_data-1.csv) |
| Executive summary  | [Lendsmart.pdf](Lendsmart.pdf) |
| Presentation video | https://youtu.be/Pp-CgQ5JIC4?si=JpZoAOssP_rKuvZD |
