# Mercantail — Pet Merge & Economy Prototype

A mobile-first merge-2 game prototype exploring item evolution trees, resource-constrained economies, and the "Merge-to-Sell" core loop.

🕹️ **[Play the prototype →](https://ds30mins.github.io/mercantail-pet-merge-prototype/)**

---

## 🎯 Product Vision

Mercantail started as a market research project before becoming a prototype.

The Merge-2 genre generated $1.4B in revenue in 2025 — growing 80% YoY and earning $4.70 per download, nearly 3× Match-3. 
Yet despite that growth, the top titles (Gossip Harbor, Travel Town, Merge Mansion) share the same structural pattern: order fulfillment is a mechanism to fund something else — a renovation, a mystery narrative, a destination story. The orders are the means. The meta layer is the end.
The gap this prototype tests: no top Merge-2 title has made the merchant identity itself the emotional core. In Mercantail, pets don't evolve to unlock a story — they evolve as your shop companions, permanently visible in the park you're building. The commerce loop isn't a bridge to the meta. It is the meta.
The dominant Merge-2 retention model works — but it requires 50+ person teams and 500+ events per year to sustain. Mercantail is designed around a different philosophy: mechanic depth and emotional investment in pet evolution as the D30 retention driver, rather than content volume. 
This prototype is the validation step. The pet evolution and park-building meta layer is intentionally excluded — if players disengage during the core merge-and-fulfill loop, adding a meta layer might wouldn't fix it. The aimed sequencing is to validate the session mechanic first, then build the identity layer on top of a loop that already holds attention.

---

> 📸 *Screenshots — board mid-session with active orders*
>
> <img width="430" height="791" alt="Screenshot 2026-03-25 124311" src="https://github.com/user-attachments/assets/e2a0a9b1-177b-4661-ab80-9e7abbe430cc" />

> 📸 *Screenshots — Energy refill in shop*
>
><img width="412" height="790" alt="Screenshot 2026-03-25 124341" src="https://github.com/user-attachments/assets/d4c944ab-6fa0-40c5-9626-58fb50aad0d7" />


---

## ✨ Core Features

### Evolution Trees
Four distinct item paths — **Greens**, **Sprouts**, **Seafood**, and **Meats** — each with 5 levels of progression. Items evolve through merge actions, and players can inspect any item's full evolution path via an in-game modal. Max-level items carry the highest sell value and are required for top-tier orders.

### Resource Economy (Zaps & Gold)
- **Energy (Zaps):** Each spawn costs 1 Zap. When energy hits zero, the player is gated to the Shop, creating a natural soft-paywall moment — a mechanic directly relevant to F2P monetisation design.
- **Gold:** Earned through item sales and order fulfillment. Spent to refill energy (+10 Zaps for 100g), simulating a basic IAP loop.
- The balance between spawn cost and order reward is intentionally tunable — designed as a sandbox for testing economy levers.

### Orders System
Three rotating customer orders give the player a purpose-driven reason to keep merging. Orders specify a required item and a Gold reward, creating goal clarity and influencing which items are worth evolving vs. selling outright. Fulfilled orders refresh automatically, sustaining the loop.

### Mobile-First UX
- Max-width 430px shell, locked orientation, no drag-and-drop — built entirely around **tap-to-select / tap-to-merge** for one-handed play.
- Touch-optimised: `webkit-overflow-scrolling`, `safe-area-inset` padding, tap-highlight disabled.

### Feedback & Notification System
- **Toast notifications** for merge results, sell confirmations, energy warnings, and order deliveries — surfacing key game state changes without interrupting flow.
- **Particle burst animations** on successful merges and order completions to reinforce positive actions.
- **Floating coin indicators** on sell actions to make economy feedback feel immediate and satisfying.

---

## 🧠 Design Decisions & Trade-offs

| Decision | Rationale |
|---|---|
| Tap-only (no drag) | Reduces accidental moves on small screens; keeps the interaction model learnable in one session |
| 5×6 board (30 cells) | Small enough to feel constrainted, large enough to hold 2 producers + items-in-progress simultaneously |
| Energy as the primary constraint | Creates a clear monetisation hook without requiring a timer; aligns with session-length control |
| Rotating orders (not static) | Ensures replayability and prevents players from optimising to a single "solved" merge path |
| Sell button always available | Gives players an escape valve to manage board space; also teaches opportunity cost |

---

## 📊 Playtest Results & KPIs
n=9 sessions · 2,255 events logged · March 2026 · convenience sample · findings are directional

| Metric | Result | Implication | 
|---|---|---|
| Players fulfilling ≥1 order | 8/9 (89%) | Core loop engagement validated — well above ~60% benchmark | 
| Players opening shop | 8/9 (89%) | Energy gate working as designed | 
| Players reaching Tier 2+ item | 3/9 (33%) | Critical onboarding gap — primary v2 hypothesis | 
| Session length range | 25s – 899s | Bimodal — discovery threshold at ~3 minutes | 

Three players with no contact with each other independently raised the same gap: the game lacks escalating challenge or a sense of meaningful progression beyond gold accumulation. 

Primary hypothesis formed: Players who don't complete their first merge chain within 90 seconds disengage before reaching the commerce loop. The onboarding sequence should prioritise a guided first merge — not a free-play start.

Next test: Guided vs. free-play onboarding — targeting lift from 33% to 50%+ on Tier 2+ progression rate.
> → Full playtest brief with session-level data, funnel analysis, and A/B test design: [link coming soon]
>
> → Full portfolio brief with market research, competitor analysis, and roadmap: [link coming soon]

---

## 🛠️ Technical Stack

| Layer | Choice | Note |
|---|---|---|
| Core | Vanilla HTML/CSS/JS (no build step) | Deployed as a single `.html` file for maximum portability |
| Styling | Tailwind CSS (CDN) | Utility-first; rapid iteration on layout |
| Icons | Lucide React (CDN) | Lightweight icon set |
| Fonts | Google Fonts — Nunito / Nunito Sans | Warm, rounded type to match the cosy shop aesthetic |
| Deployment | GitHub Pages | Zero-config, shareable link |
| AI-assisted development | Claude (Anthropic) + Gemini (Google) | Used for code generation, iteration, and debugging during prototyping |

The no-build architecture was a deliberate choice: it keeps the prototype lightweight and shareable without requiring a dev environment to run it — useful for cross-functional review with designers, PMs, or playtesters.

---

## 🔮 What I'd Build Next

Given more time, the highest-priority additions would be:

1. **Progression / Meta-loop** — a level or "day" structure to give the session loop a sense of advancement (e.g. shop upgrades, new item trees unlocked).
2. **Configurable economy parameters** — an admin panel or URL params to tweak energy cost, refill price, and order rewards without code changes, enabling faster A/B testing iteration.
3. **Analytics instrumentation** — lightweight event tracking (e.g. Amplitude) to capture merge depth, shop opens, and order fulfillment data.
4. **Expanded item trees** — a third "Bakery" path and Tier 6 items to test whether added complexity improves retention or overwhelms new players.
5. **Onboarding flow** — a 3-step tutorial overlay for first-time players to reduce early churn.

---

---

## 🎮 Other Projects

- [Who's Smarter?](https://ds30mins.github.io/whos-smarter-prototype/) · [repo](https://github.com/ds30mins/whos-smarter-prototype)

---

> → Full playtest brief with session-level data, funnel analysis, and A/B test design: [link coming soon]
>
> → Full portfolio brief with market research, competitor analysis, and roadmap: [link coming soon]

*Built as a personal project to explore F2P merge mechanics and mobile UX design.*
