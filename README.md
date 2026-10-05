# D2C E-Commerce Conversion Funnel Analysis

An end-to-end data analytics project analyzing 120,000+ direct-to-consumer user sessions to evaluate user journey drop-offs, track conversion efficiency, and uncover optimization opportunities across different device segments.


# Project Overview
In the fast-paced e-commerce landscape, understanding user behavior from initial click to final checkout is critical. This project maps out a 5-stage D2C conversion funnel to identify where potential customers abandon their journey and provides actionable insights for product optimization.

* **Dataset Size:** 120,000 user sessions
* **Tools Used:** Python (Pandas, Plotly), Google Colab
* **Key Focus:** Funnel drop-off analysis and device segmentation (Mobile vs. Desktop)


## The Conversion Funnel Stages
1. **Website Visit:** 120,000 users (100.00%)
2. **Product View:** 77,870 users (64.89%)
3. **Add to Cart:** 27,156 users (22.63%)
4. **Checkout Started:** 16,234 users (13.53%)
5. **Purchase Completed:** 8,181 users (6.82%)

<img width="900" height="600" alt="newplot" src="https://github.com/user-attachments/assets/62852a52-c244-4f52-b0d5-1207fc82fc37" />


# Key Insights & Findings

* Healthy Overall Conversion: The store maintains an overall conversion rate of **6.82%** from visit to purchase, performing well relative to standard digital retail baselines.
* The Primary Funnel Bottleneck: The steepest drop-off occurs between the **Product View** and **Add to Cart** stages. While nearly 65% of visitors view a product, **only 34.87% of those viewers add the item to their cart** (resulting in a **65.13% drop-off** at this single step). This highlights friction in product page engagement, pricing clarity, or calls-to-action.
* Balanced Device Performance: Surprisingly, device-level segmentation showed minimal performance variance, with **Desktop converting at 6.91%** and **Mobile converting at 6.78%**. This indicates that the mobile user experience is functioning effectively and that optimization efforts should focus universally on product consideration rather than assuming mobile is a primary leak source.

---

# Code Snippet Example
Here is a snippet of how the funnel conversion rates were calculated using Python and Pandas:

```python
# Calculate stage-to-stage transition rates
funnel_df["Stage_To_Stage_%"] = (
    funnel_df["User_Count"] / funnel_df["User_Count"].shift(1)
) * 100
