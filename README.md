# FinGuard AI

Financial risk monitoring dashboard. Built to simulate what an internal compliance tool at a bank might look like - real-time risk scores, transaction monitoring, alerts, and intervention tracking.

## Why I built this

Most "fintech projects" on GitHub are just a single ML model predicting stock prices. I wanted to build something closer to what an actual risk team uses day-to-day: a dashboard where you can see flagged customers, drill into their behavior, track interventions, and monitor portfolio-level risk metrics. The goal was to understand the full stack behind financial compliance software, not just the ML part.

## What it does

- **Risk scoring dashboard** - overview of portfolio health with risk distribution charts, trend lines, and alert counts
- **Customer risk profiles** - click into any customer to see transaction history, risk factors, behavioral patterns, and an explainability breakdown of why they were flagged
- **Alert management** - risk alerts with severity levels (Low/Medium/High/Critical), filterable and sortable
- **Intervention tracking** - when a customer gets flagged, you can create interventions (account freeze, enhanced monitoring, etc.) and track their lifecycle
- **Governance view** - compliance metrics and audit-ready summaries

## Tech stack

| Layer | What | Why |
|:------|:-----|:----|
| Frontend | Next.js 16, React 19, TypeScript | Server components + fast hydration |
| UI | shadcn/ui + Radix primitives + Tailwind 4 | Clean component library, accessible out of the box |
| Charts | Recharts | Works well with React, handles the risk distribution and trend visualizations |
| State | Zustand | Lightweight, no boilerplate compared to Redux |
| Data | Prisma ORM | Type-safe queries, nice migration workflow |
| Auth | NextAuth | Session management with role-based access |
| Animations | Framer Motion | Smooth transitions between dashboard views |

## Project structure

```
src/
├── app/           # Next.js app router pages
├── components/    # UI components (dashboard panels, charts, tables)
├── data/          # Mock data and seed scripts
├── hooks/         # Custom React hooks
├── lib/           # Utility functions, API helpers
├── styles/        # Global styles and theme config
└── types/         # TypeScript type definitions
```

## Running it

```bash
# install
npm install

# set up the database
npx prisma migrate dev

# start dev server
npm run dev
# → http://localhost:3000
```

## What I learned

Building this taught me more about financial compliance than any course could. Things like - why banks use ensemble risk scores instead of single models, how intervention workflows need audit trails, and why explainability matters when regulators ask "why did you flag this customer?"

The hardest part was the data modeling. A customer's risk profile isn't just a number - it's a function of their transaction velocity, geographic patterns, counterparty risk, historical behavior, and a dozen other factors. Getting the Prisma schema right to support all these relationships took multiple iterations.
