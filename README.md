# Global E-Commerce Delivery Delay & Profitability Analysis

An end-to-end analytics and machine learning project that diagnoses chronic late deliveries in a global e-commerce operation, quantifies their profitability impact, and identifies operational levers for improvement.

## Project Summary

This project analyzes **172,765 orders** from **January 2015 to January 2018** to answer four core business questions:

- How serious is the late-delivery problem?
- What is the financial impact of delays?
- Which operational factors drive lateness the most?
- Can risky orders be identified before delivery failure happens?

The analysis combines:
- data cleaning and feature engineering
- KPI design
- profitability analysis
- bottleneck detection
- regional root-cause analysis
- time-based delay analysis
- predictive modeling with Random Forest

## Business Problem

A global e-commerce company was experiencing frequent gaps between promised and actual delivery times. That created three major business risks:

- lower customer trust
- weaker operational reliability
- reduced order profitability

The goal of this project was to build a practical, data-driven framework for understanding the delay problem and turning the findings into actionable recommendations.

## Key Results

- **54.71%** of all orders were delivered late
- **45.29%** were delivered on time
- **172,765** orders were analyzed
- **$7.5M** total profit came from profitable orders
- **$2.1M** in profit was associated with delayed orders and therefore at risk
- A **Random Forest classifier achieved 74% accuracy**

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- imbalanced-learn (SMOTE)

## Project Structure

```text
project-root/
├── data/
├── notebooks/
├── images/
│   ├── profitability_distribution.png
│   ├── delay_distribution_profit_vs_delay.png
│   ├── bottleneck_detection.png
│   ├── root_cause_analysis.png
│   └── time_based_patterns.png
└── README.md
```

## Executive Summary

The analysis shows that late delivery is not a marginal issue. It is the default experience for a majority of customers. More than half of all orders arrive late, and delayed orders are tied to **$2.1M** in at-risk profit. The strongest operational failure is shipping mode performance, while time-based patterns and regional analysis reveal where targeted intervention is most valuable.

## Key Performance Indicators

- **Late Delivery Rate:** 54.71%
- **On-Time Delivery Rate:** 45.29%
- **Total Orders:** 172,765
- **Late Deliveries:** 94,523
- **Total Profit (Profitable Orders):** $7.5M
- **Profit at Risk (Delayed Orders):** $2.1M
- **90th Percentile Delay:** 3 days
- **Average Order Profit:** $22.03

## Profitability Analysis

Order profitability was split into three broad groups based on `Order Profit Per Order`:

- **Profit:** 80.7%
- **Loss:** 18.7%
- **Break-even:** 0.6%

This shows that while most orders are profitable, a meaningful share of the business is margin-negative, which becomes more concerning when combined with high delay rates.

<img width="446" height="409" alt="image" src="https://github.com/user-attachments/assets/31377647-eb48-45f2-99b3-bcd935d27822" />


### Delay Distribution & Profit vs. Delay Days

Delay-day analysis shows that:

- **31.0%** of all orders arrive exactly **1 day late**
- Delays of **1–4 days** account for most of the late-delivery burden
- Profit remains exposed across delayed cohorts, with delayed orders contributing heavily to financial risk

<img width="1590" height="590" alt="image" src="https://github.com/user-attachments/assets/f8d8c07c-0b52-4b2f-b263-cafdc3b83cf1" />


## Bottleneck Detection

Delay rates were analyzed across six important operating dimensions:

- Order Region
- Customer Segment
- Shipping Mode
- Order Status
- Type
- Department Name

### Main Findings

- **Shipping Mode is the biggest lever**
  - First Class: **100.0%** delay rate
  - Second Class: **79.8%**
  - Standard Class: **39.8%**
  - Same Day: **0.0%**
- Regional delay rates cluster tightly around **55%–59%**, which suggests a company-wide issue rather than a localized one
- Customer segments are nearly identical in delay exposure
- Department-level differences exist, but they are smaller than the shipping mode effect

<img width="1611" height="711" alt="image" src="https://github.com/user-attachments/assets/73dd26b1-72a9-41e1-bd16-e50213363b32" />


## Root Cause Analysis

A deeper root-cause analysis was performed for **Central Africa**, the worst-performing region at **58.7%** delay rate.

The top drivers in that region include:

- **Shipping Mode: First Class**
- **Shipping Mode: Second Class**
- **Order Status: PAYMENT_REVIEW**
- **Order Status: PENDING**
- **Type: PAYMENT / TRANSFER**
- **Department Name: Outdoors / Golf**
- **Customer Segment: Consumer**

This points to operational design and process bottlenecks rather than random fluctuation.

<img width="764" height="444" alt="image" src="https://github.com/user-attachments/assets/39f7874c-5920-4c63-aae6-fa19e7675f95" />


## Time-Based Delay Patterns

Three temporal dimensions were analyzed:

- month of year
- day of week
- hour of day

### Main Findings

- Delay rates stay in a relatively narrow range, around **53%–57%**
- **August and September** are the highest months at **55.4%**
- Day-of-week variation is minimal, so weekday is not a strong intervention lever
- **Hour 21** has the highest delay rate at **57.1%**, with other notable peaks around midday

These patterns suggest that capacity planning and cutoff-time management are more important than calendar-day scheduling changes.

<img width="1790" height="590" alt="image" src="https://github.com/user-attachments/assets/3bf23699-bd44-46a7-8ed6-3f80a4f19e10" />


## Machine Learning Model

A supervised classification model was built to predict whether an order would be delivered late.

### Pipeline

- Selected structured operational features
- Encoded categorical variables
- Used stratified train/test split
- Applied **SMOTE** to balance the training data
- Trained a **Random Forest Classifier**

### Performance

- **Accuracy:** 74%
- Stronger precision on late orders than on-time orders
- Suitable as a first-pass alert system for flagging risky orders before shipment failure

## Strategic Recommendations

1. **Audit First Class and Second Class shipping immediately**  
   These modes are performing far below their service promise and should be reviewed first.

2. **Deploy a predictive late-delivery alert workflow**  
   Use model predictions to flag risky orders early and trigger proactive interventions.

3. **Fix payment-processing bottlenecks**  
   Orders in `PAYMENT_REVIEW` and related statuses show materially elevated delay rates.

4. **Create seasonal surge plans**  
   Prepare extra fulfillment capacity for peak months such as August, September, and December.

5. **Review high-delay departments in Africa**  
   Especially categories such as Outdoors and Golf.

6. **Reduce the loss-making order share**  
   Combine discount and delay analysis to identify where margin loss is being amplified.

## Conclusion

This project shows a clear operational problem: late delivery is widespread, financially meaningful, and diagnosable with data.

The strongest insight is that the problem is **systemic but actionable**. Shipping mode design, payment friction, and fulfillment timing patterns explain much of the delay burden. At the same time, a machine learning model already provides a useful foundation for proactive order-risk detection.


