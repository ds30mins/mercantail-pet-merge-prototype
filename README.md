# Mercantail — Pet & Merge Prototype

A mobile-first Merge-2 prototype exploring whether a commerce loop — 
order targets, energy pacing, reward timing — can hold attention before 
a meta layer gives players a reason to return.

## 🔗 Portfolio Artifacts

| Artifact | What it is |
|---|---|
| [▶ Play the prototype](https://ds30mins.github.io/mercantail-pet-merge-prototype/) | Playable in browser — no install needed |
| [📊 SQL data analysis](https://ds30mins.github.io/mercantail-pet-merge-prototype/mercantail_data_analysis.html) | 6 SQL queries, 5,393 events, interactive charts |
| [📄 Playtest brief](https://ds30mins.github.io/mercantail-pet-merge-prototype/Mercantail_Playtest_Brief_ProductAnalyst_version.pdf) | n=10 sessions, 7 findings, A/B test designs |
| [📋 Portfolio brief](https://ds30mins.github.io/mercantail-pet-merge-prototype/Mercantail_Portfolio.pdf) | Market research, concept, prototype scope, roadmap |


---

> 📸 *Screenshots — board mid-session with active orders*
>
> <img width="430" height="791" alt="Screenshot 2026-03-25 124311" src="https://github.com/user-attachments/assets/e2a0a9b1-177b-4661-ab80-9e7abbe430cc" />

> 📸 *Screenshots — Energy refill in shop*
>
><img width="412" height="790" alt="Screenshot 2026-03-25 124341" src="https://github.com/user-attachments/assets/d4c944ab-6fa0-40c5-9626-58fb50aad0d7" />

> 📸 *Embedded event logger active during session — real-time event capture with full economy state*
>
> <img width="430" height="932" alt="Embedded event logger active during session" src="https://github.com/user-attachments/assets/e53e8501-eb01-4d5d-a9c4-de3281814732" />


---

## What Is Mercantail

Mercantail is a playable product hypothesis. 
The merge-economy genre has seen sustained breakout growth — Gossip Harbor, Travel Town, and Merge Mansion have demonstrated that strong D30 retention is achievable in casual mobile when the session loop and meta layer work together. 
> *The specific design question this prototype tests: does the merge-and-fulfill session loop hold attention on its own, before the meta layer is built?*

The prototype deliberately excludes pet evolution and park building. If players disengage during the core loop, adding a meta layer won't fix it. The playtest validates the session mechanic first.

---


## Core Loop

**Session loop:** Spawn item → Merge → Fulfill order → Earn Gold → 
Manage energy → Repeat

**Meta loop (next build phase):** Fulfill orders → Earn meta rewards → 
Pet evolves *or* story progresses (A/B test) → Deepens identity 
investment → Drives D7/D30 return

The tension in each session: do you evolve an item for a high-value 
order, or sell lower-tier items to refill energy now?


---


## What's Built in the Prototype

| Feature | Description |
|---|---|
| Merge board | 5×6 grid (30 cells). Tap-to-select, tap-to-merge. No drag-and-drop — designed for one-handed mobile play. |
| 4 item evolution trees | Greens, Sprouts, Seafood, Meats — each with 5 tiers. Players can inspect full evolution path via in-game modal. |
| Order system | 3 rotating customer orders. Specifies required item and Gold reward. Fulfilled orders refresh automatically. |
| Energy system | Each spawn costs 1 Energy. When energy hits zero, player is gated to the Shop — the natural soft-paywall moment. |
| Gold economy | Earned by fulfilling orders. Spent to refill energy (100 Gold → +10 Energy). |
| Shop | Triggered at energy = 0. Energy refill and Gold purchase simulation. Pearl (hard currency) IAP layer is designed but not yet implemented. |
| In-game event logger | Embedded dev logger used in S08 and S10 (P08). Captures 8 event types — item spawns, merges, orders, shop opens, energy refills — with before/after state for tier, energy, and gold at every event. Output to CSV. Primary data source for SQL analysis. |
| Mobile-first UX | Max-width 430px, locked orientation, safe-area insets, toast notifications, particle animations on merge/order events. |

---

## Playtest Results

**n=10 sessions · 5,393 events · ~114 minutes total play · March 2026**

| Finding | Signal | Disposition |
|---|---|---|
| Order fulfillment — 100% of sessions | Every session included at least one fulfilled order. Commerce loop is intrinsically motivating once players understand it. | Core loop validated. Green light to build the meta layer. |
| Session length is bimodal | Under 3 min or over 8 min — no middle ground. P08's two sessions ran 27 and 30 minutes, placing them in the top 1% of mobile session lengths (GameAnalytics 2025). | Onboarding is the lever. Test next. |
| Tier 5 has no purpose | 6 of 10 sessions reached max tier — but there are no Tier 5 orders. Players who invested found no reward. | Unambiguous design gap. Implement next. |
| Four players independently raised the same gap | No escalating challenge, no progression structure, no win condition. Convergent unprompted feedback across four players. | Which meta layer earns stronger retention? A/B test next. |
| Energy gate reliably triggers shop | 9 of 10 sessions hit the energy gate and opened the shop — but almost always in a friction context, never aspirational. | Economy calibration and delayed first gate. Implement next. |
| Tutorial gap | Three players independently requested guided onboarding. One session under 1 minute had zero merges completed. | Guided vs. free-play onboarding. A/B test next. |

→ Full methodology, session-level event log, complete findings, and 
A/B test design in the **[Playtest Brief](https://docs.google.com/document/d/1XzXsajKMO2cU8iQv9WPIos2yKFVTmwE4/edit?usp=sharing&ouid=111557979061720829115&rtpof=true&sd=true)**

---

## 📈 Data Analysis

Playtest data from 10 sessions and 5,393 logged events was imported into SQLite 
and analysed using SQL queries covering session engagement, event breakdown, 
player funnel, gold economy, energy patterns, and session quality classification.

**[→ View the full SQL analysis](https://ds30mins.github.io/mercantail-pet-merge-prototype/mercantail_data_analysis.html)**

### Data Collection

Two logging methods were used across sessions:

| Method | Sessions | What it captures |
|---|---|---|
| Manual event logging | S01–S07, S09 | Spawn, merge, order, shop, energy events |
| Embedded in-game logger | S08, S10 (P08) | All of the above + item paths, decimal timestamps, full economy state (gold & energy before/after every event) — output to CSV |

### SQL Queries Written

| Query | What it answers |
|---|---|
| Session summary | Duration, orders, merge ratio per session |
| Event breakdown | COUNT(CASE WHEN) pivot of all event types by session |
| Player funnel | UNION ALL across 7 funnel stages from raw event log |
| Gold economy | Time-series gold tracking for P08 (Rich Data only) |
| Energy pattern | Energy drain & refill cycle across P08's two sessions |
| Session quality | JOIN between summary + events tables with CASE WHEN classification |

### Key Findings

| Finding | Signal | Disposition |
|---|---|---|
| 100% order fulfillment | Core loop is intrinsically motivating | ✅ Green light for meta layer |
| Tier 5 has no purpose | Players who reach max tier find no reward | 🔨 Implement next |
| Bimodal session distribution | Under 3 min or over 8 min — no middle ground | 🧪 Test (onboarding) |
| Energy gate is friction-only | Shop always reactive, never aspirational | 🔨 Implement next |
| 4 players independently flagged missing progression | Strongest convergent signal in dataset | 🧪 Test (meta layer) |
| 3 players independently requested tutorial | Confirmed by S03 early churn data | 🧪 Test (onboarding) |

📄 **[Full playtest brief →](https://ds30mins.github.io/mercantail-pet-merge-prototype/Mercantail_Playtest_Brief_ProductAnalyst_version.pdf)**  
🗃️ **[Raw event log (XLSX, Google Drive) →](https://docs.google.com/spreadsheets/d/1u-zIol2KSGmu2L1KLi3ek9RgXd81DIkw/edit?usp=sharing&ouid=111557979061720829115&rtpof=true&sd=true)**

---

<details>
<summary><strong>Design Decisions & Trade-offs</strong></summary>

<br>

| Decision | Rationale |
|---|---|
| Tap-only (no drag) | Reduces accidental moves on small screens. Keeps the interaction model learnable in one session. |
| 5×6 board (30 cells) | Small enough to feel constrained, large enough to hold 2 producers and items-in-progress simultaneously. |
| Energy as the primary constraint | Creates a clear monetisation hook without requiring a timer. Aligns with session-length control and natural soft-paywall moment. |
| Rotating orders (not static) | Ensures replayability and prevents players from optimising to a single solved merge path. |
| Sell button always available | Gives players an escape valve to manage board space. Also teaches opportunity cost — selling a high-tier item early has a real cost. |
| No meta layer in prototype | If players disengage during the core loop, adding pet evolution won't fix it. Validate the session mechanic before committing to full production scope. |

</details>

---

<details>
<summary><strong>Technical Stack</strong></summary>

<br>

| Layer | Choice | Note |
|---|---|---|
| Core | Vanilla HTML/CSS/JS (no build step) | Deployed as a single `.html` file for maximum portability |
| Styling | Tailwind CSS (CDN) | Utility-first; rapid iteration on layout |
| Icons | Lucide React (CDN) | Lightweight icon set |
| Fonts | Google Fonts — Nunito / Nunito Sans | Warm, rounded type to match the cosy shop aesthetic |
| Deployment | GitHub Pages | Zero-config, shareable link |
| AI-assisted development | Claude (Anthropic) | Used for code generation, iteration, and debugging during prototyping |

The no-build architecture was a deliberate choice: lightweight, 
shareable, and runnable without a dev environment — useful for 
cross-functional review with designers, PMs, or playtesters.

</details>

---

<details>
<summary><strong>What's Next</strong></summary>

<br>

**Implement next** — signal is clear enough that testing would be 
procrastinating behind data:
- Tier 5 orders — closes the motivation dead end, creates a natural 
  premium spend moment
- Sell price calibration — increase by 25–50% to align Gold economy 
  with energy refill cost
- Delayed first energy gate — allow players to experience the commerce 
  loop before hitting a monetisation moment
- UI legibility — increase icon size and level number visibility 
  within item tiles

**Test next** — A/B experiments before committing to build:
- Guided 3-step onboarding vs. free-play start — primary metric: 
  % players reaching Tier 2+ in first session
- Meta layer direction: pet evolution arc vs. story progression — 
  primary metric: D7 and D30 retention

**Build next** — pending A/B test results:
- Meta layer v1 — pet evolution arc or story progression based on 
  retention signal
- Park building, async social layer (friend visits, gifting)
- Egg gacha, seasonal LiveOps events

→ Full roadmap and KPI framework in the **[Portfolio Brief](https://ds30mins.github.io/mercantail-pet-merge-prototype/Mercantail_Portfolio.pdf)**

</details>

---

## 🎮 Other Projects

- [Who's Smarter?](https://ds30mins.github.io/whos-smarter-prototype/) · [repo](https://github.com/ds30mins/whos-smarter-prototype)

---

*Built by Diana Sinohardjo · diana.sinohardjo@gmail.com · [LinkedIn](https://www.linkedin.com/in/diana-sinohardjo/) · March 2026*
