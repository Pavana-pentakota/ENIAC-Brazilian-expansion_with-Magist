# ENIAC Brazilian expansion with Magist (Phase 1)
Business analysis for Eniac's Brazil expansion via Magist — Tableau dashboards on product fit, seller performance, and delivery

**Full project documentation:** [View on Confluence] https://pentakotapavanakumari.atlassian.net/wiki/spaces/MBC1/overview?homepageId=4292803

## Business Context
- Eniac wants to expand into Brazil and is considering partnering with Magist, a local fulfillment platform, to test the market. Two concerns drove this analysis:
- 1. Is Magist a good fit for high-end tech products?
- 2. Are deliveries fast and reliable enough for premium customers?

## Business Questions Answered
- What tech categories does Magist carry, and what share of sales do they represent?
- Are expensive tech products popular on the platform?
- How do tech sellers perform vs non-tech sellers (count, revenue, income)?
- How fast and reliable is delivery, and does it affect customer satisfaction?

## Dataset & Sources
- Source: Magist Brazilian E-Commerce Dataset, provided by WBS Coding School as part of the Eniac–Magist business case (originally sourced via MySQL, exported to CSV)
- Size: 9 relational CSV files, ~99,441 orders as the core fact table
- Tables used: orders, order_items, order_payments, order_reviews, customers, products, sellers, geolocation, product category translation
- Key Features: order timestamps (purchase, estimated delivery, delivered date), product category, price, freight value, seller ID, customer location, review score
- Notes: Delivery/date fields required conversion to proper date type before use in Tableau.
-- An order_id data type mismatch (string vs. numeric) between orders and order_items had to be corrected to enable table relationships.
-- A Tech / Non-Tech classification column was manually added to the products data (via MySQL, before export) to categorize each product for this analysis.

## Key Findings & Results
- Market readiness: Demand and sellers are both concentrated in São Paulo and the Southeast region, pointing to an established, functioning ecosystem rather than a thin or untested market.
- Product fit: Tech products make up 21.45% of units sold and carry a real price premium — R$130.43 average vs. R$118.09 for non-tech.
- Tech sellers: Tech sellers are only 26.5% of the seller base but generate 53% of total revenue and earn ~3x more per month on average than non-tech sellers.
- Delivery reliability: 89% of orders are delivered on time. Late orders see review scores drop sharply, from 4.3 (on-time) to 2.3 (late). No clear link was found between product weight and delay — a positive signal for Eniac's lightweight accessories.
- Delivery risk: Orders consistently arrive before the estimated delivery date, but the estimate itself carries an unusually long buffer (~11.8-11.9 days) for both tech and non-tech orders — a potential source of lost sales at checkout, not an actual performance problem.
- Recommendation: Proceed with a conditional 3-year partnership with Magist, contingent on tightening the delivery estimate algorithm to better reflect actual (faster) delivery performance.

## Visualisations
- ![Product Fit](screenshots/product_fit.png) 
- ![Seller Performance](screenshots/seller_performance.png) 
- ![Delivery Performance](screenshots/delivery_performance.png)
- ![Delivery Risk](screenshots/delivery_disk.jpg)
- ![geographic_expansion](screenshots/geographic_expansion.png)

## Tools Used
- Tableau Desktop — data modeling (relationships), calculated fields, dashboards, and story
- MySQL — initial data exploration and creation of the Tech/Non-Tech classification column
- CSV — final data export format used for the Tableau workbook

## Project Structure
- magist-eniac-tableau-analysis/
 - ├── README.md
 - ├── data/
   -   │   ├── orders.csv
   -   │   ├── customers.csv
   -   │   ├── order_items.csv
   -   │   ├── order_payments.csv
   -   │   ├── order_reviews.csv
   -   │   ├── geo.csv
   -   │   ├── products.csv
   -   │   ├── sellers.csv
   -   │   └── product_categories.csv
 - ├── tableau/
   -   │   └── magist_eniac_analysis.twbx
 - └── screenshots/
   -   ├── product_fit.png
   -   ├── seller_performance.png
   -   ├── delivery_performance.png
   -   ├── geographic_expansion.png
   -   └── delivery_risk.png

## How to Use This Project
- Download this repository.
- To explore interactively: open tableau/magist_eniac_analysis.twbx.
- Raw data files are available in the data/ folder if you'd like to explore the source CSVs directly.

## ## Next Steps: Phase 2 - ENIAC Discount Strategy
- Phase 1 evaluated whether Magist is the right partner for Eniac's Brazil expansion. 
- Phase 2 builds on it by looking at pricing and promotions in Eniac's own data.
1. How many products are discounted?
2. How big are the discounts as a % of price?
3. How do seasonality and special dates (Black Friday, Christmas) affect sales?
4. How can products be categorized for reporting?
5. How are prices distributed across categories?
6. How could data collection be improved?

**Repo:** [link] | 
**Documentation:** [Confluence link]
