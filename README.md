# Customer Segmentation & Campaign ROI Dashboard

**A 5-page interactive Power BI dashboard that shows which customers are most valuable and which marketing campaigns are worth repeating.**

Built with: Power BI · DAX · Power Query · Data Modeling

---

## Business Problem

A business ran six marketing campaigns and needed answers to two questions:

1. Which customer segments generate the most value?
2. Which campaigns actually converted, and who responded to them?

This dashboard answers both using a customer-level marketing dataset of **2,240 customers**.

## Dashboard Pages

| Page | Question it answers |
| --- | --- |
| **Overview** | Who are our customers and how is the business doing overall? |
| **Customer Segmentation** | Which segments (income, marital status, family structure) drive the most revenue? |
| **Product Performance** | Which product categories perform best, and for whom? |
| **Campaign Effectiveness** | Which campaigns worked, and who responded? |
| **Channel Behavior** | Do customers prefer Web, Store, or Catalogue? |

## Key Insights

- **Wine is the standout category**, contributing **50.45%** of total category revenue, with Meat second at 27.24%.
- **Married customers generate the most revenue** (0.47M) and make up 38.73% of the base, but **Widowed customers have the highest average spend per person (672)**, even though they are the smallest group. Segment size and segment value are not the same thing.
- **The final campaign ("Response") performed best at 15%** acceptance, roughly double the 6-7% of Campaigns 1, 3, 4 and 5. **Campaign 2 was the weakest at about 1%.**
- The **overall campaign acceptance rate is 7.51%**, and **10.70% of customers accepted more than one offer**, which is a useful signal for future targeting.
- **Store is the leading purchase channel (46.33%)**, followed by Web (32.62%) and Catalogue (21.05%).
- **Deal usage falls sharply as income rises**: 0.42 for the Under 25K band versus 0.06 for 75K+.

## Headline Metrics

| Metric | Value |
| --- | --- |
| Total Customers | 2,240 |
| Avg Spend per Customer | 562.76 |
| Overall Campaign Acceptance Rate | 7.51% |
| Repeat Responder Rate | 10.70% |
| Complaint Rate | 0.91% |
| Avg Recency (days) | 49.01 |
| Web Conversion Rate | 76.84% |

## Data Preparation (Power Query)

- Consolidated one-hot encoded **marital status** and **education** columns into single categorical columns using conditional logic.
- **Unpivoted the six campaign flags** (AcceptedCmp1-5, Response) into a dedicated Campaigns table with one row per customer per campaign.
- Created **Income Band** groupings to support segmentation without exposing raw income values.
- Built a relationship between the Customer table and the Campaigns table on **Customer ID**.

## DAX Highlights

20+ custom measures, including:

- `CALCULATE`, `FILTER`, `SWITCH`
- `RANKX`, `TOPN`
- `DIVIDE` for safe ratio calculations
- Iterators such as `AVERAGEX` and `SUMX`

## Challenges & Learnings

- **Measures vs calculated columns:** a measure used as a chart axis returned blanks everywhere. Categories need to be columns.
- **Incomplete unpivot:** the first attempt kept only one of six campaigns. I fixed it by re-selecting the columns to unpivot.
- **Blank measure behaviour:** Repeat Responder Rate correctly returns blank under a single-campaign filter. I handled it with an `ISBLANK` wrapper rather than treating it as a bug.
- **Consistent design:** custom navy/teal/gold theme, synced slicers, and sidebar navigation with active-page highlighting across all pages.

## Repository Contents

```
├── Customer.pbix                          # Power BI project file
├── marketing_campaign_data.csv            # Raw dataset (2,240 customers)
├── Customers_Analysis_Dashboard.pdf       # Exported dashboard (all pages)
├── Customer_Dashboard_Project_Report.docx # Full project report
└── images/                                # Page screenshots
```

> To open the `.pbix` file, download it and open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).

## About Me

I'm **Monicah Alek**, a data analytics student in the ARel Data Science Program, building skills in Power BI, DAX, Power Query, SQL and Excel, and looking for data analyst opportunities.

- LinkedIn: www.linkedin.com/in/monicah-majok
- Email: monicahalekmajok@gmaial.com

---

*Project completed as part of the ARel Data Science Program.*
