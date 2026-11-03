<h1 align="center">Amazon India Product Analysis</h1>

<p align="center">
  <b>Pricing, discounts and ratings: Python EDA and an interactive Tableau dashboard</b>
</p>

<p align="center">
  <a href="https://colab.research.google.com/github/YOUR-USERNAME/amazon-india-product-analysis/blob/main/notebooks/amazon_eda_colab.ipynb">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab">
  </a>
  <img src="https://img.shields.io/badge/Python-pandas%20%7C%20seaborn%20%7C%20scipy-blue" alt="Python">
  <img src="https://img.shields.io/badge/Tableau-Dashboard-orange" alt="Tableau">
</p>

<p align="center">
  <img src="images/dashboard.png" alt="Amazon India Product Dashboard" width="900">
</p>

<p align="center">
  <i>Interactive in Tableau: 4 KPI cards, 7 charts, 4 filters and 3 dashboard actions. The workbook is in the <code>tableau/</code> folder.</i>
</p>

---

## About the project

This project analyses **1,351 Amazon India products** to understand how discounts, prices and categories relate to customer ratings. I cleaned the raw Kaggle data in **Python (Google Colab)**, explored it from basic statistics through to hypothesis tests, and built an **interactive Tableau dashboard** with filters and click-through actions. The main finding is that heavily discounted products (80% or more) are rated slightly lower, averaging **3.97 stars** versus **4.17** for light discounts of 0-20%.

## Dataset

- **Source:** Amazon Sales Dataset on Kaggle (add the link here)
- **Size:** 1,465 rows and 16 columns raw; **1,351 unique products** after cleaning
- **Key columns:** product name, category hierarchy, discounted price, actual price (MRP), discount percentage, rating, rating count, review text
- **Not included in the data:** dates, order counts, quantities, sales figures or locations. This is a product, pricing and ratings analysis, not a revenue analysis.

## Tools

- **Python:** pandas, NumPy, seaborn, matplotlib, SciPy
- **Google Colab** for the notebook
- **Tableau** for the dashboard

## Process

1. **Cleaned the data in Python.** Converted text prices (`₹1,099`) and discounts (`64%`) to numbers, fixed one invalid rating, split the category hierarchy into main, sub and leaf categories, handled missing values, and removed 114 duplicate products.
2. **Explored the data from basic to advanced.** Distributions, bivariate comparisons, Spearman correlations, IQR outliers, and segmentation into discount buckets, price bands and popularity tiers.
3. **Tested the patterns statistically.** Used non-parametric tests (Spearman, Kruskal-Wallis, Mann-Whitney) because prices and rating counts are heavily skewed.
4. **Built a weighted rating** (Bayesian average) so that a 5.0 from a handful of reviews does not outrank a 4.5 from thousands.
5. **Visualised in Tableau.** Exported the cleaned data and built the dashboard with filters and click-through actions.

## Key findings

- **Heavier discounts go with slightly lower ratings.** Products discounted 80% or more average **3.97** stars, versus **4.17** for discounts of 0-20% (Spearman rho = -0.15). The link is weak but statistically significant.
- **Three categories dominate.** Electronics, Home & Kitchen and Computers & Accessories make up about **97%** of products, so conclusions about other categories are unreliable.
- **Wearable Technology discounts hardest,** at about **70%** on average. Headphones, Earbuds & Accessories has the lowest average rating among the larger sub-categories (**3.92**).
- **Price alone barely predicts rating.** Ratings cluster between 3.8 and 4.5 across all price bands.
- **Overall:** 1,351 products, average rating **4.09**, average discount **46.7%**, average sale price about **₹3,305**.

## Limitations

- No dates or sales data, so no trend or revenue analysis is possible.
- Colour variants of one product share the same rating count, so total review counts are inflated.
- Missing ratings and rating counts were filled with the median.
- The discount-rating relationship is an association, not proof that discounts cause lower ratings.
- A product's listed "actual price" may itself be inflated, so a high discount does not always mean a real saving.
