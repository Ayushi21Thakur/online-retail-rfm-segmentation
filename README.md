# Online Retail Customer Segmentation (RFM Analysis)

Customer segmentation using RFM (Recency, Frequency, Monetary) analysis in Python on the UCI Online Retail dataset to identify high-value customers and those at risk of churning.

## Business Question
Which customers are the most valuable, and which are at risk of leaving? Knowing this helps a retailer decide where to spend its marketing budget.

## Dataset
- **Source:** [UCI Machine Learning Repository: Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)
- **Description:** Transactions from a UK-based online retailer, Dec 2010 to Dec 2011
- **Raw size:** 541,909 rows, 8 columns
- **After cleaning:** 392,692 rows, covering 4,338 customers and 18,532 invoices
- **Total revenue in analysis period:** about 8.89M (GBP)

## Tools Used
Python, pandas, matplotlib, Google Colab

## Approach
1. **Data cleaning:** removed rows with no CustomerID, cancelled invoices (InvoiceNo starting with "C"), zero or negative quantity or price, and duplicate rows. Created a `TotalPrice` column (Quantity x UnitPrice).
2. **Exploratory analysis:** looked at monthly revenue trends and top countries by revenue.
3. **RFM calculation:** for each customer, calculated
   - **Recency:** days since last purchase (snapshot date = one day after the last invoice)
   - **Frequency:** number of unique invoices
   - **Monetary:** total spend
4. **Scoring:** scored each metric from 1 to 5 using quintiles (Recency scored in reverse, since fewer days is better).
5. **Segmentation:** assigned customers to rule-based segments (Champions, Loyal Customers, Recent Customers, At Risk, Need Attention, Lost).
6. **Analysis:** compared each segment's share of customers vs. share of revenue.

## Key Findings

| Segment | Customers | % of Customers | % of Revenue |
|---|---|---|---|
| Champions | 1,139 | 26.3% | 66.5% |
| Loyal Customers | 821 | 18.9% | 15.2% |
| At Risk | 643 | 14.8% | 9.0% |
| Lost | 1,065 | 24.6% | 5.8% |
| Need Attention | 351 | 8.1% | 1.8% |
| Recent Customers | 319 | 7.4% | 1.6% |

- **Champions** are about 26% of customers but generate **66.5% of revenue**.
- **Champions + Loyal Customers** together make up about 45% of customers and about 82% of revenue.
- **At Risk** customers (643) bought about 3.4 times on average but have not returned in about 153 days, representing roughly 798K in past revenue.
- **Lost** customers are about 25% of the base but only 5.8% of revenue.

## Recommendations
- **Champions:** reward with loyalty perks and early access, since they drive about two-thirds of revenue.
- **Loyal Customers:** offer upsell and cross-sell deals to move them toward Champion status.
- **At Risk:** run a win-back campaign (discount or reminder email), as they have strong purchase history and the most revenue to recover.
- **Recent Customers:** send a follow-up to encourage a second purchase.
- **Lost:** use low-cost reactivation only, as expected returns are small.

## Charts
<!-- Add 2 or 3 screenshots here, e.g. monthly revenue chart and the segment comparison chart -->
![Monthly Revenue](images/monthly_revenue.png)
![Customers vs Revenue by Segment](images/segment_comparison.png)

## How to Run
1. Download the dataset from the UCI link above and place `Online Retail.xlsx` in the same folder as the notebook.
2. Open `online_retail_rfm.ipynb` in Google Colab or Jupyter Notebook.
3. Run all cells from top to bottom.

## Next Steps
- Try K-Means clustering on the RFM values and compare with the rule-based segments.
- Build a dashboard of the segments in Power BI.

## Author
Ayushi Thakur | [LinkedIn](https://www.linkedin.com/in/ayushi-thakur2165) | [GitHub](https://github.com/ayushi2165)
