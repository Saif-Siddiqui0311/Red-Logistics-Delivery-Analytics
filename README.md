# Red-Logistics-Delivery-Analytics
**Excel | Power Pivot | DAX | Dashboard design**

I analysed 6 months of shipment operations data (11,399 inbound shipments to 239 cities) to find out how reliably a courier closes shipments within its city-level SLA, and where it falls short.

<img width="1909" height="1018" alt="image" src="https://github.com/user-attachments/assets/32ed6bb4-ad93-4969-af6c-79f4f3c1a5e3" />


*Two slicers (Mode, Month) control every card and the top row of charts. The bottom row shows fixed monthly trends.*

### 🎯 Headline Results
| | |
|---|---|
| ✅ Closure SLA | 84.6% of 11,002 closed shipments closed within their city SLA |
| 📦 Delivered | 93.3% (90.7% door delivery + 2.6% broker / self-clearance) |
| ⏱️ Delivery speed | 2.9 days on average after hub arrival; 75% within 3 days |
| 📉 SLA trend | 89.6% in May → 82.1% in July, flat at about 83% since |
| ⚠️ Weakest cities | Sialkot, Gujranwala, Gujrat: 5% of volume, 18% of SLA failures |
| 💰 Value at risk | PKR 16.5M closed without delivery; PKR 18.0M still open |

### ❓ Questions I Answered
- How reliably are shipments closed within their SLA, and how did that change month by month?
- Which cities miss SLA most, and why?
- How fast are shipments delivered after arriving at the hub?
- How much declared value and COD is lost or still at risk?
- Do payment mode and delivery channel change performance?

### 🛠️ Tools
- Excel Tables with structured references
- Power Pivot data model and a DAX measure (COD Realisation)
- PivotTables, PivotCharts, and 2 slicers controlling 10 pivots at once
- IFS, VLOOKUP, COUNTIFS, SUMIFS, combo charts with a secondary axis

### 🔍 The Analysis

**1. SLA Logic (Raw Data sheet)**
Each city has a maximum number of days allowed. The SLA clock starts when a shipment arrives at the destination hub and stops when it reaches a final status.
- Closed within the allowed days = Pass. Closed late = Fail.
- Still open = not scored yet, so it is kept out of the rate.

**2. Monthly Trend (KPI Cal sheet)**
- Closure SLA fell from 89.6% in May to 82.1% in July, then held at 83.1% to 83.6%.
- Average delivery time rose from 2.6 to 3.1 days. Deliveries within 3 days fell from 83% to 70%.
- October still has 394 open shipments, so its rate covers closed shipments only.

**3. Destinations (Dashboard)**
- Karachi is 34% of volume and closes 95.7% within SLA, averaging 2.2 days against 3 allowed.
- Sialkot, Gujranwala, and Gujrat average 4.7 to 4.9 days against 4 allowed, so only 40% to 49% meet SLA.
- The 229 smaller cities outside the top 10 reach 72%.

**4. Delivery Speed (Dashboard)**
- 75% of door deliveries arrive within 3 days of hub arrival; 3% take 8 to 15 days.

**5. Value and COD (KPI Cal sheet)**
- PKR 510.4M declared value in total, of which PKR 476.0M was delivered.
- PKR 16.5M closed without delivery: returns PKR 9.8M, customs confiscations PKR 4.4M, disposals PKR 2.3M.
- PKR 15.3M COD in total. 78.7% was realised through door delivery, rising to 93.7% with broker shipments.

**6. Payment Mode and Channel (Dashboard)**
- Collect (COD) shipments meet SLA 92.9% of the time, against 83.9% for Pre-Paid.
- All 293 broker / self-clearance shipments closed within SLA, in 0.8 days on average.

### 💡 What I Learned
- 🧭 **Metric definition:** deciding what "on time" means (closure SLA, open shipments excluded) changed the answer more than any formula.
- 🔢 **Consistent denominators:** one SLA definition used on every card, chart, and table.
- 🎛️ **Dashboard design:** slicers drive the detail, while monthly trends stay fixed so they always show the full picture.
- 🔒 **Data anonymisation:** masked shippers, consignees, and IDs before publishing.

### ✅ Conclusions (C-suite Summary)
- **Service slipped and has not recovered:** closure SLA dropped 7 points from May to July and stayed there.
- **The problem is concentrated:** three secondary cities carry 5% of volume but 18% of failures. Their average delivery time already exceeds the 4 days allowed, so either the route needs fixing or the target needs resetting.
- **The big cities are healthy:** Karachi and Lahore run at 95.7% and 89.3%.
- **Returns are the biggest value leak:** PKR 9.8M of the PKR 16.5M closed without delivery, and worth investigating by reason.
- **Clear the October backlog:** 394 open shipments worth PKR 17.8M will turn into SLA failures if they keep ageing.
