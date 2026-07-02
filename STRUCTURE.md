# STRUCTURE.md — how the app is organized

This is the technical map of `index.html`. Useful if you (or Copilot / another AI) want to modify a section, add a new one, or debug something.

## File layout

```
spacex-opportunity/
├── index.html      # Everything — HTML, CSS (embedded), JS (embedded)
├── README.md       # Public-facing description
├── STRUCTURE.md    # This file
├── LICENSE         # MIT
└── .gitignore
```

**One file, on purpose.** No build step, no framework. Chart.js is the only external dependency and it loads from CDN. If a friend wants to open this on their phone or share it via email attachment, that's ~170 KB of HTML — nothing to install.

## The `index.html` layout

```
<html>
├── <head>
│   ├── Meta tags + Chart.js CDN
│   └── <style> — all CSS (~1,700 lines)
│       ├── :root — CSS variables (colors, radius, shadows)
│       ├── Base typography, layout, nav
│       ├── Section-specific styles (hero, calc-card, presets, etc.)
│       ├── Sliders (STACKED grid: label|value on top, slider full-width below)
│       ├── Charts (chart-box wrapper, chart-canvas-wrap)
│       └── Media queries (mobile responsive)
│
├── <body>
│   ├── <nav class="top"> — Sticky nav with 15 anchor links
│   └── <main>
│       ├── 16 <section> blocks (see section map below)
│       └── <footer> — Reset button + disclaimer
│
└── <script>  — all JS (~700 lines)
    ├── Formatters (fmt$M, fmt$B, fmtBig, kgToT, etc.)
    ├── DEFAULTS — single source of truth for every input value
    ├── State: STARSHIP_PRESETS, GROWTH_SCENARIOS, TAM constants
    ├── Chart builders (build*Chart functions)
    ├── Update functions (update*, one per interactive section)
    ├── Event bindings (bindInputs, preset click handlers)
    ├── resetDefaults() — invoked by the footer button
    └── DOMContentLoaded — force DEFAULTS on load, build charts, wire inputs, initial render
```

## Section map

Search HTML for the `<!-- SECTION NAME -->` comments to jump to each one. Approximate line ranges (current file is 4,128 lines).

| # | Section | Anchor | Interactive? | Approx. lines |
|---|---------|--------|:-:|---|
| 1 | Hero — investment thesis pitch | `#hero` | No | 1906–1970 |
| 2 | SPCX live market data | `#spcx` | No | 1971–2083 |
| 3 | Bear thesis (9 cards) | `#bear` | No | 2084–2155 |
| 4 | Physics vs. execution | `#physics` | No | 2156–2207 |
| 5 | Three eras timeline | `#timeline` | No | 2208–2249 |
| 6 | Interactive $/Mbps calculator | `#calculator` | ✅ 8 inputs + 4 presets | 2250–2357 |
| 7 | $/kg cost curves chart | `#cost-curves` | ✅ mode toggles | 2358–2408 |
| 8 | $/Gbps compounding | `#bandwidth` | Live scenario table | 2409–2449 |
| 9 | vs. Xfinity comparison | `#compare` | Deployment cost chart | 2522–2704 |
| 10 | Starlink valuation | `#valuation` | ✅ 4 scenarios + 7 sliders | 2450–2521, ...–2790 |
| 11 | Global TAM & underserved | `#tam` | ✅ 3 sliders + donut | 2705–2904 |
| 12 | Unit econ + One Plan Everywhere | `#unit-econ` | ✅ 9 sliders | 2791–3057 |
| 13 | Space data centers | `#compute` | ✅ 6 sliders | 2905–3057 |
| 14 | Bull thesis sum-of-parts | `#bull` | No (static table + 3 cases) | 3058–3190 |
| 15 | What $0.10/Mbps unlocks | `#unlocks` | No | 3191–3255 |
| 16 | Sources | `#sources` | No | 3256–end |

## Key JS entry points

All in one `<script>` block at the bottom.

### Formatters
```js
fmt$M(v)      // "$17.0M"
fmt$B(v)      // "$130B"
fmtBig(v)     // auto-picks K/M/B/T
fmtBigNum(v)  // 121M / 1.5B (no $)
fmtGbps(v)    // "2,838 Gbps"
kgToT(kg)     // "17 t" (adaptive precision)
```

### State constants
```js
const DEFAULTS = { ... }         // every input's default value
const STARSHIP_PRESETS = { ... } // Rob's / 33fg / Long-run / Expendable
const GROWTH_SCENARIOS = { ... } // Conservative / Base / Aggressive / Hyper
const TAM = { ... }              // world internet population buckets
const GLOBAL_SMARTPHONES = 3.6e9
const GLOBAL_TELCO_REV   = 1.5e12
```

### Interactive update functions (all wired via `bindInputs()`)
```js
updateCalculator()          // $/Mbps calc for F9 + Starship
updateValuation()           // 5-year projection + year table + P/S
updateTam()                 // Capture rate → subs → revenue → EV
updateUnitEcon()            // Cost breakdown → margin
updateOnePlan()             // Global bundled plan revenue
updateComputePerLaunch()    // GPUs per Starship + FLOPS + $ per launch
```

### Preset handlers
```js
applyStarshipPreset(key)  // Rob's, 33fg, Long-run, Expendable
applyGrowthScenario(key)  // Conservative, Base, Aggressive, Hyper
```

### Chart builders (Chart.js instances kept as module-level variables)
```js
buildCostKgChart()   // 3 modes × 30 flights (line)
buildGbpsChart()     // 5 scenarios log-scale (horizontal bar)
buildRevenueChart()  // Revenue + EBITDA over years (line)
buildDeployChart()   // Terrestrial vs satellite deployment (log-scale h-bar)
buildTamDonut()      // World internet population (doughnut)
```

### Init
`DOMContentLoaded` handler:
1. Force all inputs to `DEFAULTS` (browsers persist range/number state across refresh — we override)
2. Build all 5 chart instances
3. Call `bindInputs()` to wire up all `input` event listeners
4. Run every `update*` function once to render initial state

## CSS design system

Colors are all CSS custom properties in `:root`:

```css
--bg-0: #05060a       /* base background */
--bg-1: #0b0e17       /* card background */
--bg-2: #131829       /* input background */
--bg-3: #1c2340       /* elevated input */
--line: #2a3358       /* borders */
--text: #eef2ff       /* primary text */
--muted: #9aa3c7      /* secondary text */
--dim: #6b739a        /* tertiary text */

--falcon:   #4fc3f7   /* Falcon 9 / Starlink blue */
--starship: #ff7a4a   /* Starship / Launch orange */
--starlink: #b39dff   /* Starlink brand / AI compute purple */
--gain:     #34d399   /* positive / green */
--warn:     #fbbf24   /* caution / amber */
--danger:   #f87171   /* negative / red */

--font-mono: "SF Mono", "JetBrains Mono", "Fira Code", ui-monospace, Consolas, monospace
```

Segment color mapping (used throughout):
- 🔵 Falcon 9 + Starlink Connectivity = `--falcon`
- 🟠 Starship + Launch = `--starship`
- 🟣 Space DCs + Starlink brand accents = `--starlink`
- 🟢 Defense + gain/positive = `--gain`
- 🟡 Warnings = `--warn`
- 🔴 Bear thesis / negative = `--danger`

## How to add a new section

1. Add an anchor link to the nav: `<a href="#new-section">New</a>`
2. Add a new `<section id="new-section">` — copy any existing section as a template
3. If it's interactive, add new IDs to `DEFAULTS`, write an `update*()` function, and add the IDs to `bindInputs()`
4. If it needs a chart, write a `build*Chart()` function and call it from `DOMContentLoaded`
5. If it has a preset row, follow the `.presets` pattern from the Starship calculator or growth scenarios

## How to update market data

The SPCX section (`#spcx`) has real numbers from Yahoo Finance as of 2026-07-01. When market data becomes stale:

1. Search for `ticker-header` in the HTML — update price, change, market cap, EV
2. Search for `ticker-stats` — update the 8 stat cards (revenue, P/S, cash, targets, ratings)
3. Search for the S-1 segment table (Connectivity / Space / AI) — update if a new fiscal year lands

## How to update Starship flight state

Search for "Flight 12" in the HTML — appears in:
- Timeline card (Era 3)
- Physics section (both "solved" and "open" columns)
- Space data centers milestones

Bump to the latest flight number and update the details.

## Testing

There isn't a test suite — this is a one-file HTML app. To verify changes:

1. Open `index.html` in a browser
2. Open DevTools console — should show no errors on load
3. Interact with each section's inputs, verify live-updates work
4. Click the reset button in the footer — verify all sliders and inputs snap back to `DEFAULTS`
5. Resize the window — layout should be responsive (breakpoints at 900px and 700px)
