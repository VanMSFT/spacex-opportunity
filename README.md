# SpaceX Opportunity — the $2T → $3T bet

An interactive one-page webapp that lays out the investment case for SpaceX (SPCX) in numbers your friends and family can actually play with. It answers one question: **is $2 trillion today a bubble, or the entry point?**

**Live demo:** https://vanmsft.github.io/spacex-opportunity/  
**Local preview:** just double-click `index.html`.

> **Oct 22, 2026 update** — New bank presets: BofA $275, Wells Fargo $274, Clear Street $248, Susquehanna $176; Morningstar FV $70 noted. Lock-up slider's ~328M tranche moved to Oct 24 (DefiLlama). Merger note: Reuters says timing may slip past Tesla's Dec 3 meeting (no terms; toggle stays off). FCC AWS-3 uplink spectrum approval added as a risk/catalyst note. Default price unchanged.
>
> **Q3 2026 update** (market data as of the **Oct 21, 2026 close: $159.31**, +7.79% the day after Q3 results; bank presets updated for the Oct 21–22 post-Q3 target revisions). Base year re-based on the Q3'26 release (revenue $14.6B, net income $4.4B, Q1'27 revenue guide $33–37B). The update adds a compute-driven AI segment (GW × $/W), six more bank presets, informational financing presets, a dated lock-up calendar, a Tesla–SpaceX merger scenario (off by default), a Pending-FAA cadence preset with an optional Starbase Louisiana slider, and a Q3 risk/catalyst card.
>
> **Earlier Oct 2026 update** (market data then as of the Oct 9 close, $162.57). Refreshed every stale number against SpaceX's Q2'26 results, the 10-Q, and the Cursor 8-K. Added a **DCF fair-value section** with bear/base/bull and bank-approximation presets, fixed the places where static text disagreed with the live model, and tagged every single-source figure as **unverified** in the UI. Not investment advice.

## What's inside

Eighteen sections that together tell one story: SpaceX is four separate businesses stacked on a launch cost curve dropping ~95%. The page asks two questions: what the businesses are worth at Year 5 (sum-of-parts) and what that is worth **today** (DCF). Every number is editable. Market data lives in one `MARKET` constant.

### The pitch (top of the page)
- **Hero** — At ~$2.0T today. If SpaceX executes, this is a $3T company. Four segment tiles (Starlink · Space DCs · Launch · Defense), a live Year-5 sum-of-parts (≈$2.8T at defaults → buying at ≈71%), and the live DCF value (≈$164/share base). Every figure is computed from the sliders and the `MARKET` constant.
- **SPCX today** — Oct 21, 2026 close $159.31 × 13,579M shares (Q3 release) ≈ **$2.16T**. EV ≈$2.11T ($89.9B cash+securities, $38.8B debt at 9/30). TTM revenue ≈$32.1B (≈63× P/S). Q3 net income $4.4B (GAAP diluted EPS $0.35; the "adjusted $0.45" in coverage is an IBES-basis comparison, not in the release). Analyst targets after the Oct 21 revisions: JPM $500, Cantor $345, MS $75/$300/$600, Barclays $300, Evercore $275, Pivotal $260, Needham $250, GS $245, Citi $240, DB $235, TD Cowen $224, Mizuho $205, Stifel $190, Piper Sandler $140, Damodaran ≈$100. Segment cards show FY2025 (S-1) and Q3'26. The section adds a Q3 results table, a lock-up calendar slider (Oct 9 / Oct 22 derived / Oct 26 / Dec 8 / Musk Jun 12 2027), Musk's one-share-per-kid pledge (a transfer of ~72M existing shares), a Tesla–SpaceX merger scenario (off by default; never changes the DCF headline) and a risks/catalysts card.
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
- **Starlink at scale** — 5-year projection with growth scenario chips (Conservative / Base / Aggressive / Hyper). Defaults are Q3'26 actuals: 13.6M subs, **$69 consumer ARPU** (with an ARPU-drift slider, −5%/yr default), a separate **Enterprise & Government line** ($8.5B run-rate), and a 64% margin (Q3 66.7% incl. a ~3-pt one-time benefit). Year-by-year table with EV/EBITDA and P/S. Revenue split uses reported Consumer vs E&G figures, replacing the illustrative tier mix.
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

  **Satellite production constraint:**
  - Sliders: 2026 output (default 3,640/yr = Redmond's ~70/week per the S-1), annual growth (17%, the 2020–2026 compound rate) and inventory carry-over (3 months).
  - Each year, deployed satellites = min(launch capacity, production + inventory, FCC room). FCC room is headroom under the cap plus V2s that V3s can replace.
  - The binding constraint (Launch / Production / FCC) is shown per year in a chip row and the year table.
  - At default settings the Musk-targets preset becomes production-limited from 2028.

  **FCC authorization presets** set today's cap plus an extra approval that steps the cap up in a chosen year. Moving any cap slider clears the active preset.
  - **Current:** 19,400.
  - **Best estimate** (default): +7,500 in 2028, for 26,900. Based on the FCC's 7,500-satellite tranche pattern and a probability-weighted view of the 14,988 deferred satellites.
  - **Full Gen2:** +14,988 in 2028, for ~34,400.
  - **Gen3 filing** (unverified): +114,988 in 2029, including the 100,000-satellite Gen3 application from Jul 2026.

  Outputs cover 2026–2035: capacity (Tbps) and satellite count, supportable subscribers against the valuation section's demand curve, and a consumer revenue ceiling. A toggle feeds the capacity-constrained subscriber path into the DCF's Starlink consumer and E&G segments. The section shows DCF $/share at 26 vs 60 V3s per flight, plus a "what 60-V3 flights mean" callout. The starting capacity (~800 Tbps, Jun 30 2026, Q2 call) is sourced and editable. It replaces the old hard-coded 700 Tbps in the "Unlocks" KPIs, which also had a Gbps/Tbps unit slip in the "bandwidth per $1B" ratio.
- **DCF fair value (new)** — Six segments (Starlink consumer, Starlink enterprise & government, launch, AI infrastructure, AI software, Starlink Mobile), projected 2027–2036 from the Q3'26 annualized run-rate. In compute mode (on by default) 2027 AI-infrastructure revenue = average GW online × $/W (default 4.9 GW × $30/W, matching MS's FY27 GW), with a +1 GW check against Morgan Stanley's ~$27/share rule of thumb. Inputs cover margins, capex intensity, D&A, working capital, cash tax ramp, WACC, net cash and dilution. Terminal value uses **perpetual growth** or **exit multiple**, with the terminal value's share of EV shown. Connectivity can be driven by the Starlink sliders, and the orbital-compute calculator can be added as an extra segment. Presets: Bear / Base / Bull, plus approximations of **MS $75/$300/$600 (at MS's 11.2% WACC; MS's $300 is a 2040 sum-of-parts, not a DCF), JPMorgan $500, Cantor $345, Barclays $300, BofA $275, Evercore $275, Wells Fargo $274, Pivotal $260, Needham $250, Clear Street $248, Goldman $245, Citi $240, Deutsche Bank $235, TD Cowen $224, Mizuho $205, Stifel $190, Susquehanna $176, Damodaran ≈$100** (post-Q3 targets as of Oct 22). Targets held after Q3: Morgan Stanley $300, Raymond James $800, Stifel $190, Piper Sandler $140, Wedbush $225, Macquarie $250. Morningstar fair value $70 (from $62, Oct 22) is shown as context only. Compute-path presets set the 2027 GW (Evercore 4.4, Goldman 4.7, MS 4.9, JPM bull ~13 GW by YE27 ≈ 7 GW average). Each one solves a single named knob to hit its target, within 0.5% (most within 0.3%). Financing presets (MS $60B/$80B/$90B, Goldman ~$270B, Nvidia-chip ~$40B in talks, unverified; Pivotal's $225B 2027 raise against $320B capex) only show coverage of the funding gap. Base ≈ $164/share (perpetual growth) / $363 (18× exit). Bank presets are calibrations of this model, not the banks' own models. The section also includes an FCFF chart, a year table and a WACC × g sensitivity grid.
- **What $0.10/Mbps unlocks** — Six opportunity cards: rural markets, mobility, enterprise SLA, space AI, Starshield, cislunar. KPI tiles: launches to double capacity, cost to double, ratio vs today.

### Sources
- SpaceX Q3 2026 earnings release (SEC 8-K, Oct 20 2026) and Q3 call
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

- **Market data** — `const MARKET = { price, asOf, afterHours, sharesM, cashB, debtB, ttmRevB }` (`.mkt-ah` shows the after-hours move; it is never used in calculations). Change it once and the hero, SPCX block, SoP, KPIs and DCF all follow (elements with `.mkt-cap` / `.mkt-price` / `.mkt-date`).
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
4. **ARPU** — Reported Starlink ARPU is $69 (Q3'26; $66 in Q2, $85 a year earlier). Q3's uptick was mix-driven. Enterprise & Government (~41% of Connectivity revenue) is modeled separately.
5. **Multiples** — 18× EBITDA / 8× P/S is aggressive-but-defendable. Bear case: 8× / 3×. Bull case: 25× / 15×.
6. **Growth decay** — Doubling annually can't last. Model decays 15%/yr with a 10% floor. Adjust to taste.
7. **Discount rate & terminal value** — Damodaran uses ~8.4%, Goldman 12%. Over 75% of DCF value sits in the terminal year in every preset, and that is where the Street and intrinsic-value camps split.
8. **Compute rentals** — Contracted Colossus revenue is real, but the Anthropic deal can be terminated on 90 days' notice, and the customers are AI competitors.
9. **Constellation capacity**: V3's 1 Tbps and 60 per Starship are design figures. Usable capacity is roughly 21% of nameplate (ABI). The cap is 15,000 Gen2 plus 4,408 Gen1 satellites unless the FCC approves more. Busy-hour demand per subscriber grows every year. Together these decide whether launch cadence or authorization is the binding limit.

## Disclaimer

This is a **first-principles visualization**, not a stock recommendation. Numbers come from public sources (tagged **unverified** in the UI when they rest on a single secondary source) or are labeled author assumptions. Bank presets approximate published price targets with this model's mechanics; they are not the banks' models. Nothing here is investment advice. Play with the inputs and form your own view.

## License

MIT — see [LICENSE](LICENSE).
