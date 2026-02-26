## PHASE 7 — DASHBOARD

### Sheet: Dashboard

---

### Design Rules Applied
- Slight vertical scroll allowed — prioritised chart quality over one-page constraint
- Top = most important (KPI cards), Middle = trends, Bottom = risk
- KPI number is the largest text on each card, label is smaller
- Chart titles state the insight not the topic
- Color meaning system — Gold = Revenue metrics, Navy = Customer/Retention metrics
- Maximum 4 colours — Navy `#1F3864`, Gold `#C9A84C`, White `#FFFFFF`, Muted Blue-Grey `#A9B4C2`
- No gridlines, no 3D effects
- Data period and last updated date shown in subtitle

---

### Color Palette
| Element | Color | Hex Code |
|---|---|---|
| Dashboard Background | White | `#FFFFFF` |
| Title Bar | Dark Navy | `#1F3864` |
| Subtitle Bar | Medium Navy | `#2F5496` |
| KPI Card Background | Dark Navy | `#1F3864` |
| KPI Numbers | Gold | `#C9A84C` |
| KPI Labels | White | `#FFFFFF` |
| Context Text | Muted Blue-Grey | `#A9B4C2` |
| Revenue Chart Line | Gold | `#C9A84C` |
| Retention Chart Line | Dark Navy | `#1F3864` |
| UK Bar | Gold | `#C9A84C` |
| Other Country Bars | Light Grey | `#D9D9D9` |
| New Customers Bars | Dark Navy | `#1F3864` |
| Returning Customers Bars | Gold | `#C9A84C` |
| Summary Box Background | Dark Navy | `#1F3864` |
| Summary Box Footer | Medium Navy | `#2F5496` |

---

### Header Section

#### Title Bar (Rows 1–4)
- Shape: Rectangle — Dark Navy `#1F3864`
- Text: **£3.8M Revenue in 2010–2011 with High Volatility and 84% Market Concentration**
- Font: 20pt, Bold, White, Centred

#### Subtitle Bar (Row 5)
- Shape: Rectangle — Medium Navy `#2F5496`
- Text: E-Commerce Analysis | UK | 2010–2011 | 166,381 Transactions | 2,997 Customers | Updated Feb 2026
- Font: 9pt, Regular, White, Centred

---

### Spacing Rhythm
- Subtitle → KPI cards: 2 rows
- KPI cards → Trend charts: 1 row
- Trend charts → Bottom charts: 1 row
- Bottom charts → Summary box: 1 row
- Summary box → Footer: 0 rows (connected)

---

### Top Section — Executive KPI Cards

Five KPI cards side by side across full dashboard width (A to P):

| # | KPI | Value | Context Label |
|---|---|---|---|
| 1 | Total Revenue | £3.86M | *(blank)* |
| 2 | Total Customers | 2,997 | unique customers |
| 3 | Avg Retention Rate | 21.27% | excl. Jan 2011 anomaly |
| 4 | Revenue Volatility (CV) | 78.60% | coefficient of variation |
| 5 | UK Concentration | 84.42% | of total revenue |

Card structure:
- **Top** → KPI label — White, 9pt, Regular, Centred
- **Middle** → KPI value — Gold `#C9A84C`, 22pt, Bold, Centred
- **Bottom** → Context label — Muted Blue-Grey `#A9B4C2`, 8pt, Regular, Centred

---

### Middle Section — Trend Charts

#### Chart 1 — Monthly Revenue Line Chart
- **Title:** Revenue Surged 8x in Jan 2011 — Volatile Across All Months
- **Data:** tbl_Revenue_Stability — Month vs Monthly_Revenue
- **Type:** Line Chart — no markers
- **Color:** Gold `#C9A84C`, line width 2.5pt
- **Position:** Columns A to H
- **Y-axis:** £0K to £500K in £100K intervals
- **Note:** No annotation needed — spike visually obvious

#### Chart 2 — Retention Rate Line Chart
- **Title:** Retention Grew Steadily in 2011 — Peaked at 47.89% in Nov
- **Data:** tbl_Retention — Month vs Retention_Rate
- **Type:** Line Chart — no markers
- **Color:** Dark Navy `#1F3864`, line width 2.5pt
- **Position:** Columns I to P
- **Y-axis:** 0% to 200% in 20% intervals
- **Annotation:** Text box + arrow pointing to 2011-01 spike — "Jan 2011 anomaly — customer surge, not true retention"

---

### Bottom Section — Risk View

#### Chart 3 — Revenue by Country Horizontal Bar Chart
- **Title:** 84% of Revenue from UK — Top 5 Markets + Others
- **Data:** tbl_Top5_Countries — Country vs Revenue
- **Type:** Horizontal Bar Chart
- **Color:** Gold `#C9A84C` for UK, Light Grey `#D9D9D9` for all others
- **Position:** Columns A to H
- **X-axis:** £0.0M to £3.5M in £0.5M intervals
- **Sort:** Descending — UK at top
- **Note:** Original 33-country chart replaced with Top 5 + All Others grouping for clarity

#### Chart 4 — New vs Returning Stacked Column Chart
- **Title:** Returning Customers Growing — But New Customers Still Dominate
- **Data:** PT_New_vs_Returning — Month vs New vs Returning
- **Type:** Stacked Column Chart
- **Colors:** Navy `#1F3864` for New, Gold `#C9A84C` for Returning
- **Position:** Columns I to P
- **Legend:** Top — Navy = New, Gold = Returning

---

### Summary Insight Box
- Shape: Rectangle — Dark Navy `#1F3864`, full width A to P
- Structure:
  - **KEY FINDINGS** → Gold `#C9A84C`, 13pt, Bold
  - Section headers → White, 10pt, Bold
  - Bullet points → Muted Blue-Grey `#A9B4C2`, 9pt, Regular
  - Conclusion → White, 9pt, Italic

#### Content:
**1. Revenue Stability**
- Although revenue grew 8x from 2010 to 2011, a CV of 78.60% indicates high volatility and instability
- Revenue peaked in September 2011 (£421K), suggesting a possible seasonal effect that requires further validation

**2. Customer Behavior**
- With an average retention rate of 21.27%, overall growth appears largely acquisition-driven
- Returning customers increased steadily throughout 2011, suggesting early signs of improving customer loyalty

**3. Market Risk**
- 84.42% of total revenue comes from the UK, exposing the business to significant single-market concentration risk

*Overall, the business experienced rapid growth in 2011 but remains highly volatile, heavily acquisition-driven, and geographically concentrated. Strategic focus should shift toward retention improvement and revenue diversification.*

---

### Footer
- Shape: Rectangle — Medium Navy `#2F5496`, full width A to P, connected directly below Summary Box
- Text: Data Source: E-Commerce Analysis - UK | Kaggle | Analysis by [Your Name] | Tools: Microsoft Excel
- Font: 8pt, White, Regular, Centred

---

### Design Checklist
- [x] Gridlines removed
- [x] All chart titles state an insight
- [x] Consistent colour meaning system throughout
- [x] No 3D effects
- [x] KPI numbers are the largest text on each card
- [x] Footer and data source included
- [x] Date period visible in subtitle
- [x] Anomaly annotated on Retention chart
- [x] Top 5 + Others grouping applied to Country chart
- [x] Key metrics bolded in Summary Insight Box

