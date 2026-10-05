#  D2C E-Commerce Conversion Funnel Analysis

An end-to-end data analytics project analyzing **120,000+ direct-to-consumer user sessions** to evaluate user journey drop-offs, track conversion efficiency, and uncover optimization opportunities across different device segments.



##  Motivation: How I Came Up With This Idea
I built this project to explore where direct-to-consumer (D2C) e-commerce brands leak the most revenue during the digital user journey. Specifically, I wanted to move beyond basic traffic metrics and pinpoint exactly where friction occurs—answering whether mobile usability or product consideration is the primary culprit behind lost sales.



## 📊 Project Overview & Data Sourcing
* **Dataset Size:** 120,000 anonymized user sessions.
* **Data Extraction & Tools:** The raw event logs were loaded into a Python environment via Google Colab. Using **Pandas**, I cleaned, filtered, and structured the data into sequential funnel stages, and used **Plotly** to build interactive data visualizations.
* **Key Focus:** Funnel drop-off analysis, step-to-step conversion friction, and device segmentation (Mobile vs. Desktop).



## 🔄 The Conversion Funnel Stages
1. **Website Visit:** 120,000 users (100.00% from start)
2. **Product View:** 77,870 users (64.89% from start)
3. **Add to Cart:** 27,156 users (22.63% from start)
4. **Checkout Started:** 16,234 users (13.53% from start)
5. **Purchase Completed:** 8,181 users (6.82% from start)

<img width="900" height="600" alt="newplot" src="https://github.com/user-attachments/assets/d09fb262-6cd7-4359-9f03-b29a2243f1fa" />



## Methodology & Metric Calculations
To evaluate performance objectively, the following core calculations were implemented in Python:

* **Overall Conversion Rate (Conversion from Start):** 
  $$\text{Overall Conversion} = \left(\frac{\text{Users in Final Stage}}{\text{Users in Initial Website Visit}}\right) \times 100$$
* **Step-to-Step Transition Rate:** 
  $$\text{Transition Rate} = \left(\frac{\text{Users in Current Stage}}{\text{Users in Previous Stage}}\right) \times 100$$
* **Stage Drop-Off Rate:** 
  $$\text{Drop-Off Rate} = 100\% - \text{Transition Rate}$$

---

##  Key Insights & Findings

* **Healthy Overall Baseline:** The store maintains an overall conversion rate of **6.82%**, performing well relative to general digital retail baselines.
* **The Primary Funnel Bottleneck:** The steepest friction occurs between the **Product View** and **Add to Cart** stages. While nearly 65% of visitors view a product, **only 34.87% of those viewers add the item to their cart** (resulting in a **65.13% drop-off** at this single step). This highlights potential opportunities in product copy, pricing clarity, or call-to-action placement.
* **Balanced Device Performance:** Surprisingly, device-level segmentation showed minimal variance, with **Desktop converting at 6.91%** and **Mobile converting at 6.78%**, proving the mobile experience is functioning efficiently.

---

##  Business Applicability & Scalability
While this project focuses on a D2C e-commerce brand, **this analytical methodology is universally applicable** to any digital product, SaaS platform, or subscription model:
* **For SaaS Products:** Swap out "Product View" and "Add to Cart" for steps like "Free Trial Started" and "Feature Activated."
* **For Marketplaces:** Use this exact pipeline to trace drop-offs from "Search Results Viewed" to "Listing Clicked" and "Checkout Completed."
By structuring user tracking this way, digital product teams can instantly diagnose conversion leaks in any user funnel.



##  Code Snippet Example
```python
# Calculate stage-to-stage transition rates
funnel_df["Stage_To_Stage_%"] = (
    funnel_df["User_Count"] / funnel_df["User_Count"].shift(1)
) * 100
