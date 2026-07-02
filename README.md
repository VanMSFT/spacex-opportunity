# SpaceX Opportunity — the $2T → $3T bet

An interactive one-page webapp that lays out the investment case for SpaceX (SPCX) in numbers your friends and family can actually play with. It answers one question: **is $2 trillion today a bubble, or the entry point?**

**Live demo:** https://vanmsft.github.io/spacex-opportunity/  
**Local preview:** just double-click `index.html`.

## What's inside

Sixteen sections that together tell one story: SpaceX is four separate businesses stacked on a launch cost curve dropping ~95%, and the public market is pricing them at an 18% discount to the base case. Every number is editable — nothing is baked in.

### The pitch (top of the page)
- **Hero** — At $2T today. If SpaceX executes, this is a $3T company. Four segment tiles (Starlink · Space DCs · Launch · Defense) with Y5 base-case EVs summing to $2.4T. Buying at 82% of base case.
- **SPCX today** — Real market data as of July 1, 2026: $157.54 / market cap $2.075T / trailing P/S 115.66× / $19.3B revenue / -$9.36B net income. Segment breakdown from the S-1 (Connectivity, Space, AI).
- **Bear thesis** — Nine reasons sober investors say $2T is a bubble: astronomical P/S, unprofitable consolidated, cash-burning AI segment, $28.5T TAM inflation, Ritter's -30.7% underperformance data on unprofitable IPOs, decelerating Starlink growth, bond selloff, key-person risk, regulatory tail.
- **Physics vs. execution** — Two-column list: what's solved (rocket equation, orbital mechanics, retro-propulsive landing, radiative cooling, laser mesh — all 50–120 years old) vs. what's open engineering (ship reuse, cadence, $60/kg cost, orbital refueling, V3 production). The honest framing: physics is solved, execution is the bet.

### The mechanism (middle of the page — interactive)
- **Three eras timeline** — Shuttle-era ($65/Mbps) → Falcon 9 + V2 Mini ($6.55/Mbps) → Starship + V3 ($0.30/Mbps). Flight 12 (May 2026) already deployed the first V3s.
- **Interactive $/Mbps calculator** — Edit payload, cost/kg, satellite mass, satellite bandwidth for both Falcon 9 and Starship. Four preset chips for Starship (Rob's headline · 33fg design · Long-run floor · Expendable). Live-updates cost/Mbps and improvement factor.
- **Cost curves chart** — Starship $/kg by flight count across three operating modes (expendable, booster reuse, fully reusable). Chart.js line chart with mode toggles.
- **$/Gbps compounding** — Horizontal log-scale bar comparing Falcon 9+V2 Mini vs four Starship+V3 scenarios. Live scenario table.

### The comparisons
- **vs. Xfinity** — How does 1 Gbps in space compare to Comcast? Four cards: Xfinity Gigabit ($120/mo, $1500-3000 last-mile) vs Starlink Standard vs Starlink V3 vs Starship+V3 wholesale. Head-to-head deployment-cost bar chart.

### The valuation
- **Starlink at scale** — 5-year projection with growth scenario chips (Conservative / Base / Aggressive / Hyper). Six sliders for the assumptions. Year-by-year table with subs, revenue, EBITDA, EV. Dual multiples: EV/EBITDA and P/S. ARPU tier mix breakdown showing consumer / mobility / enterprise / defense contributions.
- **Global TAM & underserved** — Donut chart of world internet population (8B people): 3.9B connected, 1.5B underserved, 2.6B unconnected. Capture-rate sliders → subs, revenue, EBITDA, implied EV. Scenario table.
- **Unit economics & One Plan Everywhere** — Break the $90 ARPU into its constituent costs (launch amortization, satellites, ground, hardware subsidy, support). Then the "SpaceX Everywhere" thesis: what if broadband + cellular + roaming were one $100/mo global plan? Live output shows revenue vs. global telco market share.
- **Space data centers — the second act** — Starcloud-1 (H100 in orbit, Nov 2025), Google Project Suncatcher (Nov 2025), Starship Flight 12 (May 2026, first V3s), and Starlink AI1 (2027 in development). Four "why space works" cards. Compute-per-Starship calculator: how many H100s per launch, EFLOPS deployed, GPU capex vs launch cost.

### The bull case
- **Sum-of-parts** — The math table: Starlink $1.5T + Space $180B + AI compute $600B + Starshield $75B + Grok $38B + Mars/options $100B = **$2.469T** total EV at Year 5. Three case scenarios: Bear ($650B), Base ($2.5T), Bull ($4.5T).
- **What $0.10/Mbps unlocks** — Six opportunity cards: rural markets, mobility, enterprise SLA, space AI, Starshield, cislunar. KPI tiles: launches to double capacity, cost to double, ratio vs today.

### Sources
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

- **Assumption defaults** — search for `const DEFAULTS = {` near the top of the `<script>` block. That's the single source of truth for every slider and number input.
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
4. **ARPU** — $90 is consumer-focused. Blended (including mobility + defense) is more like $146.
5. **Multiples** — 18× EBITDA / 8× P/S is aggressive-but-defendable. Bear case: 8× / 3×. Bull case: 25× / 15×.
6. **Growth decay** — Doubling annually can't last. Model decays 15%/yr with a 10% floor. Adjust to taste.

## Disclaimer

This is a **first-principles visualization**, not a stock recommendation. All numbers are illustrative and derived from public sources. Nothing here is investment advice. Play with the inputs and form your own view.

## License

MIT — see [LICENSE](LICENSE).
