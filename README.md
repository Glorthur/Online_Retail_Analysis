# Online_Retail_Analysis
Link to Dataset and Article: https://archive.ics.uci.edu/dataset/352/online+retail

![image.png](attachment:3c81172f-fd6d-449f-a4ef-129fd179f412:image.png)

# Customer Lifetime Value and Retention Analysis

## Problem Statement

"How can the retailer identify its most valuable customers and improve retention strategies based on purchasing patterns and transaction history?"

## Background

This online retailer has operated for two years, offering various gift products through their e-commerce platform. The company aims to identify both its most valuable and least valuable customers to implement targeted retention strategies to drive business growth.

## Analysis Components

- Calculate customer-level metrics (total spend, frequency, average order value)
- Identify high-value vs. at-risk customers
- Analyze purchase timing patterns
- Develop recommendations to improve customer retention

# Data Cleaning and Preprocessing

1. Created an aggregated variable named "Amount" by multiplying "Quantity" with "Price" to calculate the total money spent per item in each transaction.
2. Split the "InvoiceDate" Column into "Date" and "Time" variables. This separation helps distinguish between multiple transactions made by the same customer on a single day at different times.
3. Missing/Null Values: Removed null rows in the “description” column.
4. Under Stock Code, rows labelled as P(Post), S (sample), and M (manual) were renamed accordingly.
5. Rows containing missing data, lost or damaged items, and related entries were removed since they were irrelevant to the analysis and represented only a small fraction of the dataset.
6. Rows with descriptions such as "thrown away," "wrong barcode," and "wrongly sold as sets" were removed since they did not represent actual product sales, as evidenced by their zero amount and unit price.
7. After data cleaning, the dataset contained 406,829 rows.
8. Data types were set as follows: Customer_ID as text, Invoice_Date as date, and amount, unit price, and quantity as numeric values.

# RFM Metrics

## Recency

To calculate recency, I identified the last purchase date for each distinct customer ID and compared it to the most recent transaction date in the dataset. The difference between these dates represents how many days elapsed between a customer's last purchase and the dataset's final transaction date (09/12/2011).

## Frequency

To calculate the Frequency metric, I counted the number of invoices per customer ID to determine how many times each customer made a purchase.

## Monetary

To calculate the monetary metric, I multiplied quantity by price to determine the total amount spent by each customer (Customer_ID) on gift products.

## Scores

Using Percentiles, I generated R, F, and M scores from 1-5:

- For Recency, lower values receive higher scores (4-5) since this indicates a more recent—and therefore more valuable—customer.
- For Frequency, customers with the highest purchase frequency received a score of 5—higher frequency values correspond to higher scores.
- For Monetary, customers with the highest spending received a score of 5—higher spending amounts correspond to higher scores.

I then combined these scores into a single RFM value.

# Customer Segmentation

## Customer Segmentation by RFM Metrics

Based on these scores, segments were created to categorize customers as follows:

- **Champions**: High scores in all RFM (555, 554, 544, etc)
- **Loyal Customers**: Good RFM scores (444, 434, 443, etc)
- **Recent Customers**: Recent shoppers but low F and M
- **At Risk**: Low recency but good F and M (past good customers who haven't bought recently)
- **Can't Lose**: Low R and F but high M (big spenders who aren't frequent)
- **Hibernating**: Very low recency but good F and M
- **Lost**: All RFM values are low
- **Needs Attention**: Other combinations

## Customer Segmentation by Frequency of Purchases

Based on the time since a customer's last purchase, they were classified into three categories: active (less than 30 days), at risk (30-90 days), or dormant (over 90 days).

## Count of Customers in Customer Segments

- **Needs Attention**: Largest segment (31.56%, 1,380 customers)
    - Nearly one-third of the customer base requires intervention
    - These customers show moderate activity but haven't fully engaged
- **High-Value Segments**: Combined 40.43% (1,768 customers)
    - Champions (21.31%, 932 customers)
    - Loyal Customers (19.12%, 836 customers)
    - These segments represent the core revenue generators
- **At-Risk Categories**: Combined 22.16% (969 customers)
    - At Risk (11.62%, 508 customers)
    - Can't Lose (4.34%, 190 customers)
    - Lost (6.20%, 271 customers)
    - These segments represent customers with declining engagement patterns
- **New Blood**: Recent Customers (5.85%, 256 customers)
    - Smallest major segment, representing new customer acquisition

### Strategic Implications

- **Customer Portfolio Strength**:
    - 40% of customers in high-value segments indicates a solid core business
    - However, the large "Needs Attention" segment suggests challenges in moving customers up the value ladder
- **Retention Warning Signs**:
    - 22% of customers showing signs of disengagement (At Risk, Can't Lose, Lost)
    - This represents a significant revenue risk if not addressed

# Recommendations

## High-Priority Intervention

Focus immediate resources on:

- **Needs Attention (31.56%)**: Develop engagement campaigns to move these customers to higher-value segments
- **At Risk (11.62%)**: Create targeted retention offers before they slide into lost status

## Value Maximization

- **Champions (21.31%)**: Implement VIP programs and exclusive benefits
- **Loyal Customers (19.12%)**: Create pathways to elevate them to Champion status

## Strategic Recovery

- **Can't Lose (4.34%)**: Despite small size, this segment warrants premium attention due to high spending potential
- **Lost (6.20%)**: Evaluate reactivation ROI vs. focusing on other segments

## Growth

- **Recent Customers (5.85%)**: Develop structured onboarding to prevent them from becoming "Needs Attention"

# Quarterly Purchase Distribution for High Value Segments

## Extreme Q4 Concentration for Top Customers

- **Nearly Exclusive Q4 Shopping**: 99.35% of purchases by the retailer’s best customers occur in Q4
- **Non-Existent Off-Season Activity**:
    - Q1: 0.18% (1,201 purchases)
    - Q2: 0.22% (1,453 purchases)
    - Q3: 0.24% (1,590 purchases)
- **More Seasonality**: High-value segments show more extreme Q4 concentration (99.35%) than the overall customer base (92.36%)

## Strategic Implications

### Customer Behaviour Patterns

- **Holiday Gift Specialists**: The retailer’s Champions, Loyal, and Can't Lose customers appear to be almost exclusively holiday shoppers.

# Actionable Recommendations

## Off-Season Activation Strategy

- Create exclusive pre-order campaigns for Q3 targeting these segments
- Develop specialized mid-year offerings available only to high-value customers

## Year-Round Engagement Plan

- Establish seasonal check-ins with personalized communications
- Create content/value that maintains relationships during off season-quarters
- Develop Q1 appreciation programs immediately following Q4

# Customer Segments by RFM Metrics

## Champions (21.31% of customers)

- **Exceptional across all RFM dimensions**
    - **R**: 11.33 days (best recency by far)
    - **F**: 698.98 purchases (extraordinary frequency - 3.8x higher than next segment)
    - **M**: $16,504.45 (highest monetary value - 6.2x higher than next segment)
- **Business impact**: Generate 81% of total revenue ($15.38M) despite being only 21% of customer base
- **Key insight**: These customers drive the business

## Loyal Customers (19.12%)

- **Strong RFM metrics with recent activity**
    - **R**: 34.03 days (good recency)
    - **F**: 92.94 purchases (solid frequency)
    - **M**: $1,712.30 (good monetary value)
- **Business impact**: Second largest revenue contributor at $1.43M (7.5% of total)
- **Key insight**: Good balance of all three metrics indicates consistent, reliable customers

## At Risk (11.62%)

- **Strong past behavior but declining engagement**
    - **R**: 148.06 days (poor recency)
    - **F**: 78.25 purchases (good historical frequency)
    - **M**: $1,440.48 (good monetary value)
- **Business impact**: $731,765 (3.8% of revenue) at risk of being lost
- **Key insight**: These customers' spending patterns mirror Loyal Customers but recency shows disengagement

## Can't Lose (4.34%)

- **Big spenders who shop infrequently**
    - **R**: 171.73 days (very poor recency)
    - **F**: 14.89 purchases (low frequency)
    - **M**: $2,672.21 (second highest monetary value)
- **Key insight**: High-value but infrequent shoppers with lengthening absence

## Needs Attention (31.56%)

- **Moderate value with declining engagement**
    - **R**: 125.69 days (poor recency)
    - **F**: 26.60 purchases (moderate frequency)
    - **M**: $647.05 (moderate value)
- **Business impact**: Largest customer segment, but contributes only 4.7% of revenue
- **Key insight**: The size of this segment indicates a significant development opportunity

## Recent Customers (5.85%)

- **New customers with promising recency**
    - **R**: 16.34 days (excellent recency)
    - **F**: 13.71 purchases (low but appropriate for new customers)
    - **M**: $252.24 (developing value)
- **Key insight**: Good recency shows initial engagement; need nurturing to increase F and M

## Lost (6.20%)

- **Minimal metrics across all dimensions**
    - **R**: 280.07 days (worst recency)
    - **F**: 6.31 purchases (lowest frequency)
    - **M**: $128.75 (lowest monetary value)
- **Business impact**: Nearly irrelevant to current revenue at 0.2%
- **Key insight**: Minimal recovery potential based on RFM values

# Strategic Implications

- **Revenue concentration risk**: 81% of revenue from 21% of customers
- **Development pipeline**: Large "Needs Attention" segment represents opportunity to boost metrics
- **Reactivation prioritization**: "At Risk" and "Can't Lose" warrant immediate intervention by business.

# KPI Metrics

## Customer Lifetime Value (CLV)

### Champions

- **Exceptional value**: These customers represent the most valuable segment by far with a CLV of $12,442.84 – over 13x higher than any other segment
- **Extremely high frequency**: With ~699 purchases per customer, these customers shop frequently
- **Solid purchase value**: Average purchase of $23.61 is higher than most segments
- **Action needed**: Retention of these customers should be the retailer’s highest priority due to their extraordinary value

### Loyal Customers

- **Strong long-term value**: Second highest CLV at $896.50
- **Good frequency**: With ~93 purchases, these customers shop regularly
- **Modest basket size**: Average purchase value of $18.42 is standard
- **Growth opportunity**: Increasing their average purchase value would yield significant returns

### At Risk & Can't Lose

- **Similar CLV, different behaviors**:
    - **At Risk**: More frequent shoppers (78.25 purchases) with lower average orders ($18.39)
    - **Can't Lose**: Big spenders ($179.41 per purchase) who rarely shop (14.89 purchases)
- **Critical intervention points**: These segments require different strategies:
    - **At Risk**: Focus on extending lifespan (currently 0.33)
    - **Can't Lose**: Focus on increasing purchase frequency

### Lower Value Segments

- **Recent Customers**: Show potential but haven't established strong patterns yet
- **Needs Attention**: Slightly higher purchase value ($24.33) than Champions but much lower frequency
- **Lost**: Essentially churned with minimal CLV ($1.99)

# Strategic Recommendations

## Segment-Specific Retention Strategies

- For Champions: Premium loyalty programs, exclusive benefits
- For Can't Lose: Subscription offers to increase frequency
- For At Risk: Re-engagement campaigns before they churn further

## Resource Allocation

- Focus retention budget primarily on **Champions** and **Can’t Lose** segments
- Limited investment in reactivating Lost customers given low potential return

# Customer Segmentation by Frequency of Purchases

## Customer Distribution

- **Active Customers**: 1,677 (38.35%)
    - These customers have made purchases within the last 30 days
    - While they represent the most engaged segment, it's concerning that only about 38% of total customer base is currently active
- **At-Risk Customers**: 1,242 (28.40%)
    - These customers haven't purchased in 30-90 days
    - This substantial segment is at a critical decision point - they could either return to active status or slide into dormancy - critical action is required.
- **Dormant Customers**: 1,454 (33.25%)
    - These customers haven't purchased in over 90 days
    - This large segment represents significant lost revenue potential

## Strategic Implications

### Customer Retention Challenge

- Nearly 62% of the customer base (At-Risk + Dormant) did not make a purchase in the last 30 days
- This indicates a significant retention challenge

### Immediate Opportunity

- The At-Risk segment (28.40%) represents the most immediate recovery opportunity for the retailer
- These customers haven't completely disengaged yet and may respond to re-engagement efforts

# Recommendations

## For Active Customers (38.35%)

- Focus on increasing purchase frequency and average order value
- Implement loyalty programs to maintain engagement
- Upsell opportunities to maximize value while they're engaged

## For At-Risk Customers (28.40%)

- Implement urgent win-back campaigns with time-sensitive offers
- Determine reasons for decreased engagement through surveys
- Create personalized re-engagement messages based on past purchase behaviour

## For Dormant Customers (33.25%)

- Test significant incentives for possible repurchase
- If reactivation fails after multiple attempts, the company should consider removing them from regular communications
