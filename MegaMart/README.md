# Team members 
- Axel Palacios Granados A01666972  
- Alan Ulises Luna Hernandez A01424523  
- Cristian Cruz Orozco A01665590  

# Case 03 – MegaMart Customer Segmentation with Cluster Analysis

This folder contains the analysis for **Case 03** of the MA2003B portfolio.  
The goal is to use **Cluster Analysis** to segment MegaMart’s customers into clear, actionable groups based on their shopping and digital behavior.

---

## 1. Business Problem

MegaMart currently treats its entire customer base as a **single, uniform group**. Promotions, email campaigns and digital experiences are largely **generic**, without considering how different customers:

- Shop (frequency and basket size),
- Spend (total value over time),
- Interact with digital channels (website, app, email),
- Return products or stop visiting.

This “one size fits all” approach generates three main challenges:

1. Marketing resources are spread thin across all customers, instead of focusing on the **most valuable** or **most promising** segments.  
2. Campaigns are not sufficiently relevant, which lowers **engagement and conversion rates**.  
3. There is limited visibility into **which customers are at risk of leaving** and which have **high growth potential**.

**Objective**  
Analyze the behavior of **3,000 MegaMart customers** and, using their shopping and interaction history, identify natural behavioral groups. Then translate those groups into **clear customer segments** and propose strategies for each one.

---

## 2. Data Description

- **Unit of analysis:**  
  One row = one customer.

- **Key variables (behavioral and digital):**
  - Purchase **frequency** (how often the customer buys).
  - **Basket size** (number of items per visit).
  - **Total spend** over the observed period.
  - Response to **email campaigns**.
  - **Returns** (number or rate).
  - **Recency**: time since last purchase.
  - **Web/app activity** (browsing and product views).

There is **no target label**. The objective is **unsupervised segmentation**: discover groups that emerge naturally from behavioral patterns.

(Exact variable names and preprocessing steps can be found in the first section of the notebook.)

---

## 3. Methodology

All the steps are implemented and documented in:

**`cluster_analysis.ipynb`**

### 3.1 Data Preparation

- Load the customer-level dataset.
- Inspect descriptive statistics and distributions for all variables.
- Treat missing values and potential outliers.
- Standardize or normalize numerical variables so that features with larger scales do not dominate the clustering.

### 3.2 Clustering Approach

- Explore different clustering options (e.g., **K-means** with varying numbers of clusters).
- Use metrics such as:
  - **Within-cluster sum of squares**,  
  - **Elbow method**,  
  - **Silhouette scores**,  

  to select a reasonable number of clusters.

- Interpret cluster centers and distributions to ensure that each cluster corresponds to a **coherent behavior pattern** rather than a purely statistical artifact.

### 3.3 Final Segmentation

Based on the analysis, four segments are identified:

1. **High-Value Loyalists – 17.5% of customers**  
2. **Big-Basket Planners – 14.4% of customers**  
3. **Everyday Value Seekers – 37.1% of customers**  
4. **At-Risk Occasionals – 31.0% of customers**

Each segment is defined by its purchasing, spending and engagement patterns, described below.

---

## 4. Key Findings: Customer Segments

### 4.1 High-Value Loyalists (17.5%)

**Who they are**  
MegaMart’s **most valuable group**.

**Key behaviors**

- Very **high total spend** and **high purchase frequency** (close to weekly).  
- Larger-than-average baskets with a mix of everyday items and higher-margin products.  
- High engagement with **email campaigns** and digital channels.  
- **Low return rates**.  
- Comfortable shopping both **in-store and online** and often buying across multiple categories.

**Business interpretation**  
These customers already behave like **loyal fans**. The main risk is **taking them for granted** instead of strengthening the relationship.

---

### 4.2 Big-Basket Planners (14.4%)

**Who they are**  
Customers who **do not shop very often**, but when they do, they place **large orders**.

**Key behaviors**

- Medium purchase frequency but **very large baskets**.  
- Strong total spend **concentrated in fewer visits**.  
- Many have been customers for a long time, with **stable habits**.

**Business interpretation**  
They are “**monthly stock-up**” shoppers: they plan large purchases and concentrate spending in specific visits. They are important for revenue but are sensitive to prices and convenience in those key trips.

---

### 4.3 Everyday Value Seekers (37.1%)

**Who they are**  
MegaMart’s **largest segment**.

**Key behaviors**

- **Moderate total spend** with steady purchase frequency.  
- Smaller baskets, often focused on offers and everyday items.  
- High browsing and product-view activity on the website or app.  
- Interested in **promotions and value**, even if each ticket is not very large.

**Business interpretation**  
They are **very open to suggestions** and promotions. With the right incentives, they can be nudged to add items to their baskets or try new categories.

---

### 4.4 At-Risk Occasionals (31.0%)

**Who they are**  
Customers with **low activity levels** and **higher churn risk**.

**Key behaviors**

- Low purchase frequency and **small baskets**.  
- Long gaps between visits and weaker loyalty.  
- Higher-than-average **return rates**, which may indicate dissatisfaction or mismatched expectations.  
- Weak engagement with digital channels.

**Business interpretation**  
This is the group **most likely to leave**. Without specific actions, their activity may keep decreasing until they almost completely stop buying from MegaMart.

---

## 5. Strategies by Segment

The segmentation allows MegaMart to replace generic marketing with **targeted strategies**:

### High-Value Loyalists

- **VIP Rewards Program**  
  - Exclusive tier with:
    - Early access to sales,  
    - Special discounts,  
    - Occasional “surprise and delight” gifts (birthday coupons, free samples).  
- **Personalized recognition** to reinforce loyalty and prevent migration to competitors.

### Big-Basket Planners

- **Bulk bundles and family packs**  
  - Design “monthly stock-up” bundles for common household staples with attractive discounts, clearly communicated before their usual purchase cycle.  
- **Cart value incentives**  
  - Free delivery, extra loyalty points or small gifts above a threshold to secure a larger share of their monthly spend.

### Everyday Value Seekers

- **Personalized promotions**  
  - Use browsing and purchase patterns to send targeted offers in categories they explore but do not yet buy frequently.  
- **Digital engagement**  
  - Gamified elements (digital stamps, challenges, instant-win coupons) that reward regular visits and small additional purchases.

### At-Risk Occasionals

- **Reactivation campaigns**  
  - “Welcome back” messages with simple, time-limited coupons to give them a clear reason to return.  
- **Friction reduction**  
  - Review pain points behind higher returns (product info, sizing, delivery times) to remove barriers for this group.

---

## 6. Expected Impact

By adopting this segment-based strategy, MegaMart can:

- Increase **revenue** by focusing on the most valuable and most promising segments.  
- Improve **customer loyalty**, especially among High-Value Loyalists and Big-Basket Planners.  
- Make **marketing investments more efficient**, aligning promotions and communication with actual customer behavior.  
- Reduce **churn risk** by addressing the needs of At-Risk Occasionals in a structured way.

---

## 7. File Structure (Case 03)

This folder contains:

- `README.md` – This file (executive summary and documentation for Case 03).  
- `MegaMart.ipynb` – Main notebook with all the code, clustering analysis and visualizations.  
- `retail_customer_data.csv` – Dataset used in the analysis (customer-level behavioral data).  
- `MEGAMART.pdf` – Executive summary report for this case.

---

## 8. How to Run the Notebook

1. From the root of the repository, install the project dependencies:

   ```bash
   pip install -r requirements.txt


## Resources and Deliverables

| Resource           | Link |
|--------------------|------|
| Main notebook      | [`MegaMart.ipynb`](MegaMart(2).ipynb) |
| Dataset            | [`retail_customer_data.csv`](retail_customer_data-1.csv) |
| Executive summary  | [`MEGAMART.pdf`](MEGAMART(1).pdf) |
| Presentation video | [YouTube](https://youtu.be/US8B2CBnwUw) |
