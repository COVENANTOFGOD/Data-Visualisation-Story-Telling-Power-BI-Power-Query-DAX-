# Data Visualisation & Story Telling (Power-BI, Power-Query, DAX)

## Purpose

Turin Data into a model, defines the measures, and delivers an interactive report.

## Power Query: load and data type formatting

Applied steps (as shown in Power Query Editor):
Step	Action
Source	Connect to the Excel workbook
Navigation 1	Select the sheet / table
Promoted headers	First row becomes the column names
Changed column type	Set data types (e.g. InvoiceDate → Date)

<img width="1117" height="660" alt="image" src="https://github.com/user-attachments/assets/02185e13-ef73-44f9-9e75-bdf3bc5d94fd" />

## Data model
DAX measures

dax
Total Customer =
DISTINCTCOUNT ( Data[Customer_ID] )

Total Revenue =
SUM ( Data[Revenue] )

Churned Customers =
CALCULATE ( DISTINCTCOUNT ( Data[Customer_ID] ), Data[IsChurned] = TRUE () )

Churned % =
DIVIDE ( [Churned Customers], [Total Customer] )

Avg Customer Value =
DIVIDE ( [Total Revenue], [Total Customer] )

## Report design
Theme: navy / slate blue palette with grey accents

## Pages
## Landing page	"INO-VET Customer Analytics: Understand customers. Drive revenue." Two navigation cards (Business Overview, RFM Analysis) and a Key Metrics Glossary (Churned %, Recency, Frequency, Monetary, Customer Value)
<img width="996" height="540" alt="image" src="https://github.com/user-attachments/assets/0cfe78e7-63d0-4f5d-a264-04d9e2bd4a10" />

## Business Overview	KPIs plus revenue / customer trends with a Revenue ↔ Customer toggle
<img width="968" height="539" alt="image" src="https://github.com/user-attachments/assets/4df81724-9ed4-4c66-83db-20b6a33daf05" />
<img width="965" height="535" alt="image" src="https://github.com/user-attachments/assets/81a7f42f-e925-4c89-ada5-594bcf8c2b62" />

## RFM Analysis	Segment and Country performance tables plus churn trends with a Segment ↔ Country toggle
<img width="965" height="537" alt="image" src="https://github.com/user-attachments/assets/f7d6c1e7-4a26-470b-8b96-0cc9037027b7" />
<img width="967" height="537" alt="image" src="https://github.com/user-attachments/assets/550530b1-fba7-4752-9a30-a0b1f6756c50" />

## Shared controls on the analysis pages

## Six slicers: Month, Quarter, Year, Country, Segment, Is Churned
<img width="1200" height="72" alt="image" src="https://github.com/user-attachments/assets/a05df805-955d-4b77-9557-46a53c0314a7" />

## Clear all slicers button (bookmark that resets filters)
## Back arrow button (returns to the landing page)
<img width="480" height="42" alt="image" src="https://github.com/user-attachments/assets/fc258b2e-47a5-429d-9d58-b4cab1ed37bf" />

Toggle buttons implemented with bookmarks and the Selection Pane 

## Business Overview page

## KPI cards
Total Customer	Total Revenue	Churned %	Avg Customer Value
<img width="761" height="98" alt="image" src="https://github.com/user-attachments/assets/d1cd8058-1905-49d8-a14f-cb4558846617" />

## Revenue view
Column chart: Total Revenue by Segment	Revenue per segment	Champions $11.84M · Loyal $2.70M · At Risk $1.59M · Lost $0.65M · New $0.39M · Needs Attention $0.21M
Pie: Revenue % by Segment	Share of revenue	Champions 68.1% · Loyal 15.5% · At Risk 9.1% · Lost 3.8% · New 2.3%
Line: Total Revenue by Month	Seasonality with average line	Low of $0.95M (Feb), rises from Sep, peak $2.32M (Nov), $1.77M (Dec)
Area: Total Revenue by Quarter	Quarterly build-up	Qtr 1 $3.4M → Qtr 2 $3.6M → Qtr 3 $4.2M → Qtr 4 $6.2M
Line: Total Revenue by Year	Year trend	2009 $0.7M · 2010 $8.4M · 2011 $8.3M
<img width="968" height="539" alt="image" src="https://github.com/user-attachments/assets/6df0349b-a23d-4de0-ace4-93eb0f938750" />

## Customer view (toggle)
Column chart: Total Customer by Segment	Lost 1,525 · Loyal 1,416 · Champions 1,292 · At Risk 820 · New 440 · Needs Attention 388
Pie: Customer % by Segment	Lost 25.9% · Loyal 24.1% · Champions 22.0% · At Risk 13.9% · New 7.5% · Needs Attention 6.6%
Line: Total Customer by Month	Climbs from 1,500 (Aug) to a peak of 2,584 (Nov)
Area: Total Customer by Quarter	2,747 → 3,039 → 3,160 → 4,101
Line: Total Customer by Year	2009 ≈ 1.0K · 2010 ≈ 4.2K · 2011 ≈ 4.2K
<img width="965" height="535" alt="image" src="https://github.com/user-attachments/assets/5e39373e-fb87-491a-a1b0-a3a5d7ef8e5a" />

## RFM Analysis page
## Segment view
Segment	Customers	Revenue	Avg R	Avg F	Avg M
Champions	1,292	$11,839,150	4.71	4.87	4.84
Loyal	1,416	$2,699,251	3.48	4.00	3.90
At Risk	820	$1,585,460	1.72	3.92	3.85
Lost	1,525	$654,784	1.45	1.56	2.10
New	440	$391,023	4.42	1.78	2.47
Needs Attention	388	$205,137	3.00	1.59	2.56
Segment by Avg Customer Value: Champions $9.2K · At Risk $1.9K · Loyal $1.9K · New $0.9K · Needs Attention $0.5K · Lost $0.4K.
<img width="965" height="537" alt="image" src="https://github.com/user-attachments/assets/f1f36161-cdb4-4e5a-a5c7-d050f72516ec" />

## Country view (toggle). The table uses conditional formatting (colour scales) on the R and F score columns.
Country	Customers	Revenue	Avg R	Avg F	Avg M
United Kingdom	5,353	$14,389,235	3.97	4.35	4.31
Netherlands	22	$554,038	4.49	4.60	4.70
Germany	107	$425,020	4.13	4.63	4.63
France	95	$348,769	4.41	4.37	4.57
Spain	41	$108,332	4.07	3.90	4.23
Switzerland	22	$100,062	3.54	3.36	4.74
Sweden	19	$91,516	2.93	3.58	4.15
Belgium	29	$65,388	4.04	3.99	4.46
Portugal	24	$55,555	4.04	3.92	4.37
Italy	17	$32,108	3.61	3.17	4.13
Top 5 Countries by Avg Customer Value (Top N filter = 5 on [Avg Customer Value]): EIRE $123K · Singapore $25K · Netherlands $25K · Australia $11K · Denmark $6K.
<img width="967" height="537" alt="image" src="https://github.com/user-attachments/assets/8e78d41a-9846-4d33-9f84-7b05156f7c18" />

## Churn trend visuals (shared by both toggles)
Churned % by Month	39.7% (Jan) · 40.1% · 42.1% (Mar, peak) · 39.7% · 37.9% · 37.0% · 35.7% · 35.9% · 24.8% (Sep) · 25.3% · 23.4% (Nov, low) · 32.6% (Dec)
Churned % by Quarter	Qtr 1 48.0% → Qtr 2 45.5% → Qtr 3 38.0% → Qtr 4 34.1%
Churned % by Year	2009 40.2% · 2010 56.3% · 2011 31.5%
<img width="1163" height="244" alt="image" src="https://github.com/user-attachments/assets/e590b0ca-0ca8-41b0-9edb-39a6cc739fef" />

## Key Findings
Revenue is highly concentrated. Champions are 22% of customers but generate 68.1% of revenue ($11.84M). Their average value ($9.2K) is more than 20× that of Lost customers ($0.4K).
Lost is the largest group but the smallest revenue contributor. It holds 25.9% of customers and only 3.8% of revenue.
At Risk is the best win-back target. 820 customers with a high Frequency (3.92) and Monetary (3.85) score, but very low Recency (1.72). Their average value ($1.9K) matches Loyal customers.
Strong Q4 seasonality. Qtr 4 revenue ($6.2M) is almost double Qtr 1 ($3.4M), driven by a September to November ramp with a November peak of $2.32M.
Revenue is flat year on year. 2010 ($8.4M) and 2011 ($8.3M) are nearly identical, although 2011 ends on 9 December. 2009 holds only December.
The business is UK-centred. 5,353 of 5,881 customers (91%) and about $14.4M (≈ 83%) of revenue are from the UK.
Export markets have small but high-quality customer bases. Netherlands, Germany and France post Avg R/F/M scores above 4.3 on the monetary scale.
EIRE's $123K average customer value is an outlier. It appears in the Top 5 but not in the Top 10 by revenue, which suggests very few customers (possibly one or two large accounts). 
Churn is high at 50.9% under the 90-day rule which needs attention.

Dashboard designed by Irogementi Covenant.
