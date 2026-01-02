# Sovereign AI Radar
A decision-ready view of **where Sovereign AI money is flowing** — who is funding, buying, building, and partnering — powered by a continuously updated global news pipeline.

Sovereign AI Radar turns noisy announcements into a **structured, comparable, and searchable** stream of investment signals. It helps leaders track momentum by **country, region, vendor ecosystem, and spend** — and spot emerging patterns early.

![Sovereign AI Radar Dashboard](./assets/dashboard_overview.png)

---

## Why it matters
Sovereign AI is moving from ambition to execution: national programs, cloud capacity buildouts, strategic procurements, and public-private partnerships are accelerating globally. But signals are fragmented across outlets and formats.

Sovereign AI Radar provides:
- **Signal over noise**: filters generic AI chatter and isolates sovereign/government-backed investments.
- **Comparable data**: normalizes currencies and geography so trends can be measured consistently.
- **Confidence in insights**: reduces duplicates and “echo coverage” to avoid inflated narratives.
- **Executive visibility**: a live dashboard built for quick scanning and deeper drill-down.

---

## What you get
### 1) A structured stream of Sovereign AI investment signals
Each validated item is standardized into a consistent record (example fields):
- **Country / Region** (aligned to UN M49)
- **Buyer / Program** (where available)
- **Vendors / Partners** (where available)
- **Investment value (USD)** when disclosed or inferable
- **Category** of activity (e.g., infrastructure, model dev, applications)
- **Source link + timestamp** for traceability

### 2) Trend visibility that supports decisions
The dashboard and dataset make it easy to answer questions like:
- Where is **spend** concentrating—by region, country, and category?
- Which vendors are repeatedly present in sovereign deals?
- What’s new this week — and what’s re-reported news?

### 3) A live executive dashboard
A Looker Studio dashboard summarizes the latest validated signals with:
- KPI cards: **total spend (USD), news volume, countries active**
- Geographic views: distribution by **country/region**
- A searchable “Latest Announcements” table with direct links for fast verification
  
  ![Latest Announcements](./assets/news_summary.png)

---

## How it works (high level)
Sovereign AI Radar operates as a simple end-to-end loop:
1. **Monitor**: scans Google Alerts (Atom) and Google News (RSS) feeds for relevant coverage
2. **Extract**: uses **Google Gemini** to convert articles into structured “deal/program” fields
3. **Standardize**: uses a **Python (Pandas)** enrichment layer to normalize:
   - currencies → **USD**
   - country names → canonical formats
   - country → **UN M49 region/sub-region**
4. **De-duplicate**: reduces repeated coverage across outlets so metrics reflect unique events
5. **Visualize**: updates Looker Studio for real-time exploration

---

## Data quality principles
- **Traceable**: every record links back to a primary source.
- **Comparable**: monetary values are normalized to USD; geography is standardized.
- **Conservative**: duplicates are removed to prevent inflated counts and misleading narratives.
- **Repeatable**: the process runs on a schedule with consistent rules and audit-friendly outputs.

---

## Outputs
The system produces two main datasets:
- **Daily Updates**: newly detected items and extracted fields (raw structured signals)
- **Daily Enriched**: cleaned + standardized + de-duplicated records used for analysis and dashboarding

---

## Under the hood (technology, in brief)
- **Google Apps Script** for ingestion + daily automation
- **Google Gemini (`gemini-flash-latest`)** for classification and structured extraction
- **Python + Pandas** for enrichment and quality control (currency, geography, normalization)
- **RapidFuzz** for fuzzy duplicate detection across reworded reporting
- **Looker Studio** for executive visualization

---

## Setup (for operators)
If you want to run this pipeline privately:
1. **Google Sheet + script**: initialize the tracker and schedule daily pulls  
2. **API key**: configure the AI extraction key via script properties  
3. **Enrichment step**: run the enrichment script/notebook to standardize data  
4. **Dashboard**: connect Looker Studio to the enriched dataset

> Notes:
> - The system is designed to control cost via daily item limits.
> - Currency conversions depend on FX availability and the chosen conversion date policy.

---

## Roadmap (optional / future)
Potential expansions:
- **Vendor & partner graph** (repeat players, ecosystems, alliances)
- **Program maturity scoring** (intent → committed → contracted → delivered → scaled)
- **Asset mapping** (compute clusters, data centers, sovereign clouds, model hubs)
- **Alerting** (notify when new high-value signals appear in key regions)

---

## Contact / ownership
Built and maintained as part of the Sovereign AI Radar initiative by **[Ontopraxis LLC](https://www.ontopraxis.ai/)**
