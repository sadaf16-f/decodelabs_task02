# E-Commerce Order Data — Exploratory Data Analysis

**Project 2 · Data Analytics Internship**

Exploratory analysis of 1,200 e-commerce orders (Jan 2023 – Jun 2025) to uncover purchasing patterns, revenue drivers, and operational risks.

📄 Full written report: [`reports/EDA_Report_Project2.docx`](reports/EDA_Report_Project2.docx)

---

## 📌 Problem Statement

Before building any dashboard or predictive model, the order data needed to be explored to answer three questions:
1. What do the core statistics tell us about a typical order?
2. Are there trends over time or outliers that need investigation?
3. What actionable insight can be handed to stakeholders?

## 🗂️ Dataset

- **1,200 orders**, 14 fields (`Quantity`, `UnitPrice`, `TotalPrice`, `ItemsInCart`, `Product`, `PaymentMethod`, `OrderStatus`, `CouponCode`, `ReferralSource`, etc.)
- No missing values or malformed entries
- Date range: **Jan 2023 – Jun 2025**

## 🛠️ Methodology

Analysis performed in **Python** (`pandas`, `matplotlib`):
- Descriptive statistics (mean, median, standard deviation, five-number summary)
- Outlier detection using the IQR method (1.5×IQR fence)
- Time-series aggregation of monthly revenue
- Correlation analysis (Pearson coefficient)
- Categorical breakdowns by product, payment method, order status, referral source, and coupon usage

---

## 📊 Key Findings

### Summary stats

| Total Orders | Total Revenue | Avg Order Value | Median Order Value |
|---|---|---|---|
| 1,200 | $1.26M | $1,053.97 | $823.62 |

Order value is **right-skewed** — a small number of bulk orders pull the mean above the median, so the median is the more reliable "typical order" figure.

![Unit Price Distribution](charts/unitprice_dist.png)

### Outlier detection

8 orders (0.7%) exceed the IQR outlier threshold of $3,330.41. All are legitimate bulk purchases (max quantity × premium unit price) — not data errors.

![Boxplot of Total Order Value](charts/boxplot_totalprice.png)

### Revenue trend

Monthly revenue is **flat**, ranging $27.7K–$68.1K with no clear growth trend or seasonality across 30 months.

![Monthly Revenue Trend](charts/monthly_revenue.png)

### Product performance

Revenue is spread evenly across all 7 product categories — no single-product concentration risk.

![Revenue by Product](charts/revenue_by_product.png)

### Order fulfilment risk

**Cancelled (20.8%) + Returned (20.6%) = 41.4%** of all orders — the single largest risk signal in the dataset.

![Order Status Breakdown](charts/order_status.png)

### Correlation analysis

`TotalPrice` correlates strongly with `UnitPrice` (r=0.72) and moderately with `Quantity` (r=0.62). `UnitPrice` and `Quantity` are essentially uncorrelated (r=0.01) — customers don't self-select higher quantities at lower price points.

![Correlation Matrix](charts/correlation_heatmap.png)

---

## 💡 So What? — Business Diagnosis

| What the Data Says | Business Diagnosis |
|---|---|
| Mean ($1,053.97) sits well above median ($823.62) | Use median, not mean, for typical-customer benchmarks |
| 8 statistical outliers, all high-value bulk orders | Candidates for a dedicated VIP/bulk-buyer program |
| Cancelled + Returned = 41.4% of orders | Top operational priority — root-cause review of checkout/fulfilment |
| Revenue is flat, no seasonality | Test a promotional calendar to create trend lift |
| Revenue evenly spread across 7 products | No single-SKU dependency risk |
| Quantity and price move independently | Bundle/volume pricing can be tested freely |

## ✅ Recommendations

- Report **median** order value in leadership dashboards, not mean
- Investigate root cause of the 41.4% cancel/return rate, segmented by payment method and referral source
- Build a bulk-buyer outreach segment from the 8 flagged high-value orders
- Pilot a promotional calendar to test for seasonal lift
- Test volume-based bundle pricing

---

## 📁 Repo Structure

```
├── README.md
├── data/
│   └── Cleaned_Dataset_In_Excel.xlsx
├── charts/
│   ├── monthly_revenue.png
│   ├── revenue_by_product.png
│   ├── boxplot_totalprice.png
│   ├── correlation_heatmap.png
│   ├── order_status.png
│   └── unitprice_dist.png
└── reports/
    └── EDA_Report_Project2.docx
```

## 🧰 Tools Used

Python · pandas · matplotlib

---

*Part of a Data Analytics Internship portfolio — Project 2: Exploratory Data Analysis.*
