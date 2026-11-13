📞 Call Center Performance Dashboard:
Highlights:
- **6 KPI cards** – Incoming, Answered, Abandoned, Answer Rate, Service Level (20 s), Avg Waiting Time
- **5 visuals** – volume trend, service-tier donut, answered vs abandoned by volume band, wait time by segment, calls-vs-service-level scatter
- **Slicers** – Volume band, Service tier, Record segment (multi-select, cross-filtering)
- **Drill-through detail page** – click any chart element, KPI card or scatter dot → a full detail page opens (KPIs, auto-generated insights, distribution, sortable record table) with a **Close** button (or `Esc`) to return
- **Clear filters** button, hover tooltips, dimmed non-selected items (Power BI-like highlight)
- Records 626–1000 (peak period) carry the heaviest volume; segment 7 (751–875) has the worst waiting time (~10.5 min) and the highest abandonment.
- Peak-volume records (300+ calls) abandon ~21 % of calls vs 5–6 % for low, medium and high volume → a staffing problem at peaks.
- 24.5 % of records are "At Risk" (service level < 60 %).
| Duplicate rows | 0 found (full-row and ignoring `Index`) |
| Missing values | 0 |
| `Answer Rate`, `Service Level` (text like `94.01%`) | converted to numeric 0–1 |
| `Answer Speed`, `Talk Duration`, `Waiting Time` (text `h:mm:ss`) | converted to seconds (integer) |
| Integrity check | Answered + Abandoned = Incoming for all 1,251 rows ✔ |
| Derived columns | `Abandon_Rate`, `Volume_Band`, `Service_Tier`, `Segment` (10 blocks of ~125 records) |
Rebuilding in Power BI Desktop (.pbix)
A `.pbix` can only be authored in Power BI Desktop, so this repo ships the HTML version plus the recipe:
1. **Get Data → Text/CSV →** `Call_Center_Data_Cleaned.csv` (types already correct).
2. DAX measures:
```DAX
3. Visuals: 6 Card visuals, Line chart (Segment_Label), Donut (Service_Tier), Clustered column (Volume_Band), Column (Segment), Scatter (Incoming vs Service_Level).
4. Slicers: `Volume_Band`, `Service_Tier`, `Segment_Label`.
5. Drill-through: create a page "Detail", add a table + KPIs, drag `Volume_Band`/`Service_Tier`/`Segment_Label` into *Drill-through filters*, and add a **Back** button (Insert → Buttons → Back).
6. Palette: Navy `#0B2545`, Blue `#1F6FB2`, Teal `#2A9D8F`, Amber `#E9A23B`, Red `#D1495B`; font Segoe UI.
