# SpaceX Opportunity — the $2T → $3T bet

An interactive one-page webapp that lays out the investment case for SpaceX (SPCX) in numbers your friends and family can actually play with. It answers one question: **is $2 trillion today a bubble, or the entry point?**

**Live demo:** https://vanmsft.github.io/spacex-opportunity/  
**Local preview:** just double-click `index.html`.

> **Oct 2026 update** (market data as of the **Oct 9, 2026 close: $162.57**). Refreshed every stale number against SpaceX's Q2'26 results, the 10-Q, and the Cursor 8-K. Added a **DCF fair-value section** with bear/base/bull and bank-approximation presets, fixed the places where static text disagreed with the live model, and tagged every single-source figure as **unverified** in the UI. Not investment advice.

## What's inside

Eighteen sections that together tell one story: SpaceX is four separate businesses stacked on a launch cost curve dropping ~95%. The page asks two questions: what the businesses are worth at Year 5 (sum-of-parts) and what that is worth **today** (DCF). Every number is editable. Market data lives in one `MARKET` constant.

### The pitch (top of the page)
- **Hero** — At ~$2.2T today. If SpaceX executes, this is a $3T company. Four segment tiles (Starlink · Space DCs · Launch · Defense), a live Year-5 sum-of-parts (≈$2.5T at defaults → buying at ≈87%), and the live DCF value (≈$127/share base). Every figure is computed from the sliders and the `MARKET` constant.
- **SPCX today** — Oct 9, 2026 close $162.57 × ≈13.57B shares (Q2 10-Q + Cursor merger shares) ≈ **$2.21T**. EV ≈$2.14T (≈$100B cash+securities, ≈$39.4B debt at 6/30). TTM revenue ≈$23.1B (≈96× P/S). TTM net income ≈−$8.2B. Analyst targets: MS $75/$300/$600, GS $220, JPM $225, BofA $235, DB $255, Damodaran ≈$100, Morningstar $62–63 (unverified). Segment cards show FY2025 (S-1) and Q2'26.
- **Bear thesis** — Nine reasons sober investors say $2T is a bubble: astronomical P/S (~96×), unprofitable consolidated, capex of $18.4B in one quarter, $28.5T TAM inflation, Ritter's -30.7% underperformance data on unprofitable IPOs, decelerating Starlink growth, bond selloff, key-person risk, regulatory tail.
- **Physics vs. execution** — Two-column list: what's solved (rocket equation, orbital mechanics, retro-propulsive landing, radiative cooling, laser mesh — all 50–120 years old) vs. what's open engineering (ship reuse, cadence, $60/kg cost, orbital refueling, V3 production). The honest framing: physics is solved, execution is the bet.

### The mechanism (middle of the page — interactive)
- **Three eras timeline** — Shuttle-era ($65/Mbps) → Falcon 9 + V2 Mini ($6.55/Mbps) → Starship + V3 ($0.30/Mbps). Flight 14 (Sep 28, 2026) reached orbit and deployed the first 26 operational V3s.
- **Interactive $/Mbps calculator** — Edit payload, cost/kg, satellite mass, satellite bandwidth for both Falcon 9 and Starship. Four preset chips for Starship (Rob's headline · 33fg design · Long-run floor · Expendable). Live-updates cost/Mbps and improvement factor.
- **Cost curves chart** — Starship $/kg by flight count across three operating modes (expendable, booster reuse, fully reusable). Chart.js line chart with mode toggles.
- **$/Gbps compounding** — Horizontal log-scale bar comparing Falcon 9+V2 Mini vs four Starship+V3 scenarios. Live scenario table.

### The comparisons
- **vs. Xfinity** — How does 1 Gbps in space compare to Comcast? Four cards: Xfinity Gigabit ($120/mo, $1500-3000 last-mile) vs Starlink Standard vs Starlink V3 vs Starship+V3 wholesale. Head-to-head deployment-cost bar chart.

### The valuation
- **Starlink at scale** — 5-year projection with growth scenario chips (Conservative / Base / Aggressive / Hyper). Defaults are Q2'26 actuals: 12.0M subs, **$66 consumer ARPU** (with an ARPU-drift slider, −5%/yr default), a separate **Enterprise & Government line** ($7.2B run-rate, +108% y/y), and a 61% margin (Q2 60.5%, H1 62.1%). Year-by-year table with EV/EBITDA and P/S. Revenue split uses reported Consumer vs E&G figures, replacing the illustrative tier mix.
- **Global TAM & underserved** — Donut chart of world internet population (8B people): 3.9B connected, 1.5B underserved, 2.6B unconnected. Capture-rate sliders → subs, revenue, EBITDA, implied EV. EBITDA and EV now use the valuation section's margin and multiple sliders instead of hard-coded 63% / 18×.
- **Unit economics & One Plan Everywhere** — Break the $90 ARPU into its constituent costs (launch amortization, satellites, ground, hardware subsidy, support). Then the "SpaceX Everywhere" thesis: what if broadband + cellular + roaming were one $100/mo global plan? Live output shows revenue vs. global telco market share.
- **Space data centers — the second act** — Starcloud-1 (H100 in orbit, Nov 2025), Google Project Suncatcher (Nov 2025), Starship Flight 14 (Sep 2026, first orbit + 26 V3s), and Starlink AI1 (2027 in development). A new callout covers the compute business that exists **today**, on the ground: $14.1B of contracted Colossus rentals (Anthropic $1.25B/mo, Google $920M/mo (unverified), Reflection $150M/mo). Four "why space works" cards. Compute-per-Starship calculator: how many H100s per launch, EFLOPS deployed, GPU capex vs launch cost.

### The bull case
- **Sum-of-parts** — Starlink (live) + orbital compute (live) + editable rows for Launch, **terrestrial AI compute rentals**, Starshield, Grok/xAI/Cursor and options. Each default carries a source note or an "assumption" tag. The total is ≈$2.5T at defaults and feeds the hero, the base-case card and the KPIs, so they can't drift apart. Bear ($650B) and bull ($4.5T) percentages are computed against the live market cap; this fixes the old "7×" KPI, which is really ≈2.0×.
- **V3 constellation scale-up (new)**: links Starship cadence and loading to Starlink capacity. Inputs:
  - Starship Starlink flights per year (2026, 2027, 2028, 2029+), V3s per flight (26 as on Flight 14, up to 60 at design), Gbps per V3.
  - Falcon V2 Mini launches and their phase-out.
  - Satellite lifetime (attrition) and the FCC-authorized constellation cap.
  - Usable share of nameplate capacity, E&G capacity reservation, plan speed, oversubscription, per-sub demand growth and ARPU.

  Cadence presets set all four Starship flight sliders, and moving any flight slider clears the active preset:
  - **Conservative** (default): 1 / 30 / 80 / 150.
  - **Musk targets** × 80% Starlink share: 1 / 62 / 292 / 800. Based on "weekly or twice weekly" in 2027, "a flight a day" from ~Aug 2027, and "thousands per year" after that.
  - **FAA-limited** × 80%: 1 / 55 / 116 / 116. Uses the approved launch envelopes: Starbase 25, LC-39A 44 and SLC-37 76, for 145 total.

  Outputs cover 2026–2035: capacity (Tbps) and satellite count, supportable subscribers against the valuation section's demand curve, and a consumer revenue ceiling. A toggle feeds the capacity-constrained subscriber path into the DCF's Starlink consumer and E&G segments. The section shows DCF $/share at 26 vs 60 V3s per flight, plus a "what 60-V3 flights mean" callout. The starting capacity (~800 Tbps, Jun 30 2026, Q2 call) is sourced and editable. It replaces the old hard-coded 700 Tbps in the "Unlocks" KPIs, which also had a Gbps/Tbps unit slip in the "bandwidth per $1B" ratio.
- **DCF fair value (new)** — Six segments (Starlink consumer, Starlink enterprise & government, launch, AI infrastructure, AI software, Starlink Mobile), projected 2027–2036 from 2026E. Inputs cover margins, capex intensity, D&A, working capital, cash tax ramp, WACC, net cash and dilution. Terminal value uses **perpetual growth** or **exit multiple**, with the terminal value's share of EV shown. Connectivity can be driven by the Starlink sliders, and the orbital-compute calculator can be added as an extra segment. Presets: Bear / Base / Bull, plus approximations of **MS $75/$300/$600, Goldman $220, JPMorgan $225, Damodaran ≈$100**. Base ≈ $127/share (perpetual growth) / $303 (18× exit). Bank presets are calibrations of this model, not the banks' own models. The section also includes an FCFF chart, a year table and a WACC × g sensitivity grid.
- **What $0.10/Mbps unlocks** — Six opportunity cards: rural markets, mobility, enterprise SLA, space AI, Starshield, cislunar. KPI tiles: launches to double capacity, cost to double, ratio vs today.

### Sources
- SpaceX Q2 2026 results, 10-Q, Cursor 8-K (Aug 2026); Q2 earnings call transcript
- Bank initiations/raises (Benzinga, ii.co.uk, Yahoo Finance AU, secondary summaries of GS/JPM notes); Damodaran (Jun 4, 2026)
- Compute deals (DCD, CNBC, x.ai; Crypto Briefing — unverified), Grain 800 MHz (Oct 8, 2026), Starship Flight 14 (SpaceX, Reuters)
- Full link list in the page's Sources section
- Rob Maurer / First Principles Group (X post, June 2026)
- Mach33 Financial Group ("Starship Will Reduce Bandwidth Launch Cost by up to 50×", Aug 2025)
- Mach33 "SpaceX AI Revenue to 2030"
- Mach33 "SpaceX's Compute Supply: The Option to Be a Hyperscaler"
- Yahoo Finance — SPCX quote & S-1 segment data
- Starcloud, Google Project Suncatcher, SpaceX Starship page

## Tech stack

Deliberately minimal:
- **One HTML file.** No framework, no build step, no dependencies to install
- **Chart.js** — loaded from CDN for the six chart types (line, bar, doughnut, horizontal bar, log-scale)
- **Vanilla JS + CSS** — everything interactive is done with `input` event listeners
- **Dark space-themed design system** — CSS custom properties for the color palette (Falcon blue, Starship orange, Starlink purple, gain green, warn amber, danger red)

## How to run

**Locally:** double-click `index.html`. No server needed. Chart.js loads from CDN — works offline once cached.

**On GitHub Pages:** enable Pages in repo settings (Settings → Pages → Source: main branch → root). Live URL will be `https://vanmsft.github.io/spacex-opportunity/`.

## How to modify

Everything you might want to change is in one file:

- **Market data** — `const MARKET = { price, asOf, sharesM, cashB, debtB, ttmRevB }`. Change it once and the hero, SPCX block, SoP, KPIs and DCF all follow (elements with `.mkt-cap` / `.mkt-price` / `.mkt-date`).
- **Assumption defaults** — search for `const DEFAULTS = {` near the top of the `<script>` block. That's the single source of truth for the pre-existing sliders and the editable sum-of-parts rows.
- **DCF** — `DCF_SEGS` (terminal growth and starting margin per segment), `DCF_BASE` (default inputs) and `DCF_PRESETS` (bear/base/bull + bank approximations). `dcfRun()` mirrors the reference model `dcf_prototype.py` (kept outside the repo, in the research folder).
- **Starship scenario presets** — `const STARSHIP_PRESETS` (Rob's headline, 33fg design, Long-run floor, Expendable).
- **Growth scenarios** — `const GROWTH_SCENARIOS` (Conservative, Base, Aggressive, Hyper-growth).
- **TAM constants** — `const TAM = { connectedAdequate: 3.9e9, connectedUnderserved: 1.5e9, unconnected: 2.6e9, ... }`.
- **Global smartphone / telco numbers** — `const GLOBAL_SMARTPHONES = 3.6e9; const GLOBAL_TELCO_REV = 1.5e12;`.
- **Colors** — CSS custom properties in `:root { }` at the top of the `<style>` block.
- **Section copy** — search HTML for the `<!-- SECTION NAME -->` comments to jump to any section.

## Places reasonable people disagree

1. **Starship $/kg** — The $60/kg floor assumes Raptor unit-cost decline + high-cadence learning. Real-world could land at $150–250/kg for years.
2. **V3 bandwidth per sat** — 1,000 Gbps is SpaceX's target. Real-world could be 600–1,200.
3. **Payload utilization** — Starship may fly at ~60% envelope for the first years (33fg's 1.67× loading discount).
4. **ARPU** — Reported Starlink ARPU is $66 (Q2'26, down from $85) and falling with geographic mix. Enterprise & Government (42% of Connectivity revenue) is modeled separately.
5. **Multiples** — 18× EBITDA / 8× P/S is aggressive-but-defendable. Bear case: 8× / 3×. Bull case: 25× / 15×.
6. **Growth decay** — Doubling annually can't last. Model decays 15%/yr with a 10% floor. Adjust to taste.
7. **Discount rate & terminal value** — Damodaran uses ~8.4%, Goldman 12%. Over 75% of DCF value sits in the terminal year in every preset, and that is where the Street and intrinsic-value camps split.
8. **Compute rentals** — Contracted Colossus revenue is real, but the Anthropic deal can be terminated on 90 days' notice, and the customers are AI competitors.
9. **Constellation capacity**: V3's 1 Tbps and 60 per Starship are design figures. Usable capacity is roughly 21% of nameplate (ABI). The cap is 15,000 Gen2 plus 4,408 Gen1 satellites unless the FCC approves more. Busy-hour demand per subscriber grows every year. Together these decide whether launch cadence or authorization is the binding limit.

## Disclaimer

This is a **first-principles visualization**, not a stock recommendation. Numbers come from public sources (tagged **unverified** in the UI when they rest on a single secondary source) or are labeled author assumptions. Bank presets approximate published price targets with this model's mechanics; they are not the banks' models. Nothing here is investment advice. Play with the inputs and form your own view.

## License

MIT — see [LICENSE](LICENSE).
