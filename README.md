# Customer Propensity to Buy & Lead Scoring Model

### About myself
**MSc Digital Marketing & AI Student | SKEMA Business School**
Focused on using Data Science to solve real-world marketing inefficiencies. This project builds a "Propensity Scoring" engine to help marketers target the right users with the right budget.

---

### The Business Problem
Marketing teams often waste budget on "Spray and Pray" tactics—targeting every visitor equally.
* **The Cost:** High CPA (Cost Per Acquisition) and low conversion rates.
* **The Solution:** A Machine Learning model that assigns a "Purchase Probability Score" (0-100%) to every user. This allows us to segment users: *Who is a "Window Shopper" vs. who is a "High-Intent Buyer"?*

### Technical Approach
* **Model:** Logistic Regression (Classification)
* **Handling Imbalance:** Applied `class_weight='balanced'` to ensure the model prioritizes the minority class (the 15% of users who actually convert) over the majority.
* **Preprocessing:** Built a Scikit-Learn `Pipeline` with `StandardScaler` for metrics (Time on Site, Pages) and `OneHotEncoder` for categories (Device, Traffic Source).

### Key Insights: The Precision-Recall Trade-off
The most valuable part of this analysis was determining **"Aggressiveness Thresholds."** We don't just predict Yes/No; we adjust the probability threshold based on the marketing channel cost.

| Threshold | Strategy | Business Application |
| :--- | :--- | :--- |
| **0.30 (Aggressive)** | **High Recall (63%)** | **Email / Push Notifications:** Since these channels are cheap, we lower the threshold to capture *more* potential buyers, even if we accidentally target some non-buyers. |
| **0.50 (Balanced)** | **Balanced** | **Standard Retargeting:** Good for general social media ads (Meta/TikTok). |
| **0.70 (Conservative)** | **High Precision (87%)** | **Direct Mail / Sales Calls:** Since these are expensive, we raise the threshold to only target users who are *highly likely* to buy. |

### 📈 Results
* **Accuracy:** ~88%
* **Business Impact:** By moving from random targeting to a **0.70 threshold** for paid ads, we can eliminate ad spend on low-intent users, significantly increasing ROAS (Return on Ad Spend).

### How to Run
1. Clone the repository:
   ```bash
   git clone [https://github.com/](https://github.com/vishaalgrizzly/conversion-propensity-scoring.git)
