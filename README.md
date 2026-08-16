# US Flight Delay Analysis (2025) — Power BI

Analysis of **7.7M U.S. domestic flights in 2025** using real Bureau of Transportation Statistics (BTS) data, built to identify where airline delays concentrate, what drives them, and what a business would prioritize to reduce them.

** .** — static page-by-page view of the full report
PBIX file available on request 

---

## The problem

Airline delays are expensive and disruptive — for passengers, for airport operations, and for airline scheduling downstream. But "delays happen" isn't actionable on its own. This project asks three concrete questions a business would actually need answered:

1. **When** do delays get worse, and is it predictable?
2. **Why** do they happen — is it weather, or something airlines control?
3. **Who** is most exposed — which airlines carry the most operational and business risk?

## The data

- **Source:** [U.S. Bureau of Transportation Statistics](https://www.transtats.bts.gov/) — Marketing Carrier On-Time Performance dataset
- **Scope:** All 12 months of 2025, ~7,736,770 flight records
- **Fields used:** ~43 columns covering flight timing, route, airline, delay-cause breakdowns (Carrier, Weather, NAS, Security, Late Aircraft), cancellations, and diversions, pared down from BTS's original ~120-column raw files

## Method

Built entirely in **Power BI Desktop**:

- **Power Query** — cleaned and reshaped 12 monthly CSVs into a single fact table, engineered features including time-of-day buckets, delay severity categories, flight status, and a delay-propagation flag (did a departure delay reach arrival, or recover en route)
- **Star schema** — a dedicated `DimDate` table joined to the flight fact table on a 1-to-many relationship, enabling clean time-based slicing
- **DAX** — ~15 measures covering delay rate, cancellation rate, on-time rate, diversion rate, average delay, and total delay minutes by cause
- **Custom color theme** — a hand-built maroon palette applied consistently across every visual

## What's in the report

| Page | What it answers |
|---|---|
| **Executive Overview** | Headline KPIs and the overall seasonal delay trend |
| **Delay Trends & Seasonality** | When delays spike — by month, time of day, and a month × weekday heatmap |
| **Delay Causes** | What's actually driving delays, and whether the cause mix shifts across the year |
| **Airline Performance** | Which airlines underperform, and whether that's a scale problem or a rate problem |
| **Insights & Recommendations** | Four findings, each tied to evidence and a specific recommendation |

## Key findings

**1. Summer delays aren't a blip — they're structural.**
July hit a 28.6% delay rate and 24.6-minute average delay; September dropped to 16.3% and 11.8 minutes. This isn't noise, it's a repeatable seasonal pattern worth planning capacity around.

**2. Delays are mostly within airlines' own control.**
Carrier Delay and Late Aircraft Delay together account for ~75% of total delay minutes across the year. Weather — the cause most people assume dominates — accounts for under 10%. The bigger lever is turnaround efficiency and scheduling, not weather contingency.

**3. Delay rate climbs through the day.**
Early-morning departures see a ~9% delay rate; by evening it's over 30% — more than 3x higher. Consistent with delays compounding as the day's schedule falls behind and doesn't fully recover.

**4. Scale changes what "bad" means.**
F9 has the single worst delay rate (27.4%), but American Airlines — the largest carrier in the dataset by nearly 2M flights — sits at 23.8%, the second-worst rate among major carriers. AA's issues, even at a lower *rate* than F9's, affect a far larger *absolute* number of passengers. Rate alone understates business impact; volume matters just as much.

## A note on causation

This analysis surfaces **associations and patterns**, not proven causes. BTS data can show that Late Aircraft Delay correlates with time of day, for example, but confirming a causal mechanism (vs. a confound like traffic volume) would need further analysis beyond what's shown here. Findings are framed accordingly throughout the report.

## Tools

Power BI Desktop · Power Query (M) · DAX · BTS public flight data

## Related

This is the second project in a small portfolio series — the first, a Chicago Airbnb pricing analysis, was built in Excel and is available [here](#).
