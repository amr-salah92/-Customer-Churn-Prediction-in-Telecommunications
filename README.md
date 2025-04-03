# Customer Churn Prediction in Telecommunications  
**Analysis Report**  

## Table of Contents  
1. [Project Name](#project-name)  
2. [Project Background](#project-background)  
3. [Project Goals](#project-goals)  
4. [Data Structure & Initial Checks](#data-structure--initial-checks)  
5. [Executive Summary](#executive-summary)  
6. [Insights Deep Dive](#insights-deep-dive)  
    - [Category 1: Customer Demographics & Behavior](#category-1-customer-demographics--behavior)  
    - [Category 2: Tenure & Subscription Trends](#category-2-tenure--subscription-trends)  
    - [Category 3: Internet Service Usage Patterns](#category-3-internet-service-usage-patterns)  
    - [Category 4: Financial Impact of Churn](#category-4-financial-impact-of-churn)  
7. [Recommendations](#recommendations)  
8. [Technical Details](#technical-details)  

---

### 1. Project Name  
**Customer Churn Prediction in Telecommunications**  

This analysis focuses on predicting customer churn for a telecommunications company using machine learning (K-Nearest Neighbors). The goal is to identify key factors influencing churn and provide actionable insights to reduce customer attrition.  

---

## Project Background  
The company operates in the telecommunications sector, providing internet, TV, and phone services via subscription-based models. Key metrics include:  
- **Churn Rate**: Current rate not disclosed, but reducing attrition is critical (industry average: 1.9–2.1% monthly).  
- **Dataset**: 10,000 customer records (42 features) spanning demographics, service usage, and contract details.  
- **Business Model**: Revenue relies on customer retention due to high acquisition costs (industry average: $300–$500 per customer).  

The analysis focuses on historical data from 2023 to predict churn drivers and improve retention strategies.
As a Data Analyst working at this company, I analyzed historical customer data to understand why customers leave and how to prevent churn. The dataset was sourced from internal customer records, with key metrics such as:  

- **Average customer tenure**: ~34.5 months  
- **Monthly charges**: ~$172.62  
- **Churn rate**: ~26.5% (based on preliminary analysis)  

The company has been operating for several years, and reducing churn is a top priority to improve revenue stability and customer satisfaction.  

---

### 3. Project Goals  
1. **Identify Key Churn Drivers**: Determine which factors (e.g., contract type, internet service, outage frequency,Bandwidth_GB_Year) most influence churn.  
2. **Predict Churn Risk**: Develop a machine learning model (KNN) to classify customers at risk of leaving.  
3. **Recommend Retention Strategies**: Provide data-driven insights to improve customer retention.  

---

### 4. Data Structure & Initial Checks  
#### Dataset Overview  
- **Rows**: 10,000  
- **Columns**: 42 (demographics, service details, usage metrics, churn status)  

### Key Tables/Features:  
1. **Demographics**:  
   - `Age`, `Income`, `Marital`, `Gender`, `Population` (county-level).  
   - **Usage**: Key for identifying low-engagement customers.  

2. **Service Usage**:  
   - `MonthlyCharge`, `Bandwidth_GB_Year`, `Outage_sec_perweek`, `StreamingTV`, `TechSupport`.  
   - **Missing Data**: `InternetService` has 21.3% missing values (2,129 records).  

3. **Contract Details**:  
   - `Tenure` (avg: 34.5 months), `Contract`, `PaperlessBilling`, `PaymentMethod`.  
   - **Key Insight**: 63% of customers use "Month-to-Month" contracts.  

4. **Churn Status**:  
   - Target variable (`Churn: Yes/No`).  

#### Initial Data Quality Checks  :
- No duplicates (`data.duplicated().sum() = 0`).
- Null values : InternetService (2129) 
- Numerical stats: `MonthlyCharge` ranges from $79.98 to $290.16 (avg: $172.62).  


#### Numeric Features:  
- **Tenure**: Avg. 34.5 months (min: 1, max: 72)  
- **Monthly Charge**: Avg. $172.62 (min: $79.98, max: $290.16)  
- **Bandwidth (GB/Year)**: Avg. 3,392 GB (min: 155.5, max: 7,158)  

---

### 5. Executive Summary  
#### Key Findings  
- **Churn is highly influenced by**:  
    - Contract type (Month-to-month subscribers churn more which form 76% of churned customers & form 20.34% of whole customers).  
    - Tenure (Newer customers are more likely to churn 0 - 20 months which form  85% of customers).
    - Age (>= 50 Years old churn more nearly 41 % of customers)
    - 50 % of customers leaveing due to high MonthlyCharge Range (200 - 291 $)
    - 17.96 % of the customers leaving despite Yearly_equip_failure = 0
    - sending frequent Emails (range between 10 - 15 Emails) associated with the 18% leaving percent
    - bandwidth users between (1000-1999 GB/year) are more likely to churn 51% of customers 
- **KNN model** achieved 85.8% accuracy, indicating strong predictive capability.  
- High monthly charges and frequent outages correlate with increased churn.
- sending frequent Emails negatively correlated with Tenture
- high MonthlyCharge negatively correlated with Tenture

#### Stakeholder Takeaways  
- **Marketing Team**: Target promotional offers for at-risk customers.  
- **Customer Support**: Prioritize retention efforts for DSL users.  
- **Product Team**: Improve service reliability to reduce outages.  
[Visualization: Heatmap of feature correlations with churn]  

---

### 6. Insights Deep Dive  

#### **Category 1: Customer Demographics & Behavior**  
- Gender: No significant impact on churn.  
- Age: >= 50 Years old churn more nearly 41 % of customers
- Income: moderate-income (20k - 50k) customers churn more (~45% of chured customers).  
[Visualization: Bar chart of churn by income bracket]  

#### **Category 2: Tenure & Subscription Trends**  
- New customers (<20 months) are more likely to churn than long-term customers.  
- One-year contracts have the lowest churn (~3%).  
[Visualization: Line graph of churn vs. tenure]  

#### **Category 3: Internet Service Usage Patterns**  
- Fiber optic users churn 7% more than DSL subscribers.  
- High bandwidth users (5,000+ GB/year) are less likely to leave (there is strong correlation 0.99 between Tenure & Bandwidth_GB_Year) .
[Visualization: Pie chart of churn by internet service type]  

#### **Category 4: Financial Impact of Churn**  
- Monthly charges >$200 correlate with 2x higher churn rate.  
- Customers with frequent Emails (range between 10 - 15 Emails) associated with the 18% leaving percent.  
[Visualization: Scatter plot of churn vs. monthly charges]  

---

### 7. Recommendations  
Based on the analysis, the following strategies are recommended to reduce customer churn and improve retention:  
#### **1. Incentivize Long-Term Contracts**  
- **Action**: Offer discounts (e.g., 10–15% off) or free service upgrades for customers switching from **month-to-month** to **1-year/2-year contracts**. 
#### **2. Proactive Retention Campaigns for High-Risk Groups**  
- **Target**:  
  - **New customers (0–20 months tenure)**: Provide onboarding support (e.g., dedicated account managers) and early incentives (e.g., 1 free month after 6 months).  
  - **Customers aged 50+**: Offer personalized plans (e.g., senior discounts) and simplified service bundles.  
  - **High monthly charges ($200+)** : Introduce loyalty discounts or value-added services (e.g., free streaming subscriptions) to offset perceived cost dissatisfaction.  
#### **3. Optimize Email Communication**  
- **Action**: Reduce email frequency for customers in their first year (currently 10–15 emails correlate with 18% churn).  
#### **4. Address Mid-Tier Bandwidth Users**  
- **Action**: Target customers using **1,000–1,999 GB/year** with tailored upgrades (e.g., "Boost Your Speed" campaigns) or loyalty rewards.  
#### **5. Improve Service Reliability**  
- **Action**:  
  - **Fiber optic users**: Invest in infrastructure to reduce outages (linked to 7% higher churn).  
  - **Yearly equipment failures**: Offer free equipment upgrades for customers with recurring issues (17.96% churn despite 0 failures suggests latent dissatisfaction).  

### **Expected Outcomes**  
- **15–20% reduction in churn** within 6–12 months.  
- Improved customer lifetime value (LTV) through loyalty incentives.  
- Enhanced brand perception via personalized engagement.  

---

### **Implementation Timeline**  
| **Initiative**                | **Priority** | **Timeframe** |  
|-------------------------------|--------------|---------------|  
| Long-term contract incentives  | High         | 1–3 months    |  
| High-risk customer monitoring  | High         | 1–2 months    |  
| Email frequency optimization  | Medium       | 2–4 months    |  
| Fiber optic reliability upgrades | Medium    | 6–12 months   |  

---

### 8. Technical Details  
#### **Tools Used**  
- **Python**: (Pandas, Scikit-learn, Seaborn, Matplotlib)  
    - Data cleaning, EDA, and KNN modeling.  
- **K-Nearest Neighbors (KNN)**  
    - Achieved 85.8% accuracy in predicting churn.  
    - Optimal neighbors: 6 (best balance of precision and recall).  


#### **Assumptions & Caveats**  
- Missing InternetService values were treated as non-subscribers.  
- Outage data was normalized to per-week metrics for consistency.  
- Model assumes no seasonality (future work: time-based trends).  

---

### Conclusion  
This analysis provides actionable strategies to reduce churn by 15-20% through targeted interventions. Further A/B testing on promotional offers is recommended.  

#### **Next Steps:**  
- Deploy the KNN model in production for real-time churn prediction.  
- Conduct customer surveys to validate retention strategies.  

**End of Report**  
