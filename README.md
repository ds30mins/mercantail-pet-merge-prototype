# Mercantail — Pet Merge & Economy Prototype

A mobile-first merge-2 game prototype exploring item evolution trees, resource-constrained economies, and the "Merge-to-Sell" core loop.

🕹️ **[Play the prototype →](https://ds30mins.github.io/mercantail-pet-merge-prototype/)**

---

## 🎯 Product Vision

Mercantail started as a **market research project** before becoming a prototype.

The merge-economy genre has seen sustained breakout growth since 2023 — titles like *Merge Mansion* and *Merge County* have demonstrated strong retention and monetisation in the casual mobile space. Yet the specific "Merge-to-Sell" loop — where merging feeds a shop or order economy rather than just a board — remains a relatively underexplored design space with room for a distinctive entry.

The prototype is the product recommendation made tangible: a playable hypothesis about what a compelling, character-driven take on this loop could look like. The core design question it answers is *how do you make a merge loop feel purposeful beyond just filling a board?*

The answer explored here is a **Shop Economy** — players manage limited energy (⚡ Zaps) to evolve items up an evolution tree, then fulfill character-driven orders for Gold. Every merge decision has weight: do you evolve for a high-value order, or sell lower-tier items to refill energy now?

This creates a short but meaningful **tension loop**: Spawn → Merge → Fulfill Orders → Manage Resources → Repeat.

---

> 📸 *Screenshots — board mid-session with active orders, Energy refill in shop*
>
> <img width="430" height="791" alt="Screenshot 2026-03-25 124311" src="https://github.com/user-attachments/assets/e2a0a9b1-177b-4661-ab80-9e7abbe430cc" />,<img width="412" height="790" alt="Screenshot 2026-03-25 124341" src="https://github.com/user-attachments/assets/d4c944ab-6fa0-40c5-9626-58fb50aad0d7" />


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
- Inspired by Tripledot's "thumb play" UX philosophy.
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

## 📊 KPIs This Prototype Is Designed to Measure

If this prototype were taken to soft-launch or live ops, the metrics I'd instrument first:

- **Session length & merge depth** — are players reaching Tier 3+ items before churning?
- **Energy depletion rate** — how quickly does the average session hit the energy gate?
- **Shop conversion rate** — of players who hit 0 energy, what % open the Shop? What % convert?
- **Order fulfillment rate** — are orders too hard (under-fulfilled) or too easy (fulfilled instantly)?
- **Gold economy balance** — is the 100g refill cost calibrated correctly relative to average order rewards?

These metrics would directly inform A/B test hypotheses around energy costs, board size, and order reward scaling.

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

📄 *A full product brief — including market research, competitor analysis, and success metrics — is available upon request.*

*Built as a personal project to explore F2P merge mechanics and mobile UX design.*
