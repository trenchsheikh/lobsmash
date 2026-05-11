# LobSmash

> The home for your padel league — codes, sessions, standings, and a global skill rating that follows you everywhere.

This repository contains the **public marketing site** for [LobSmash](https://app.lobsmash.com). The live application (auth, leagues, sessions, profiles) is a separate Next.js project hosted at `app.lobsmash.com`; this site is the front door — hero, formats explainer, how-it-works, pricing, and CTAs that hand users off to the app.

---

## What is LobSmash?

LobSmash is a league-management platform purpose-built for **padel** — designed for the realities of doubles play, court rotations, partner shuffles, and the formats clubs actually run on a Tuesday night.

Organisers today juggle WhatsApp groups, spreadsheets, and improvised rules. Players lose track of who is ahead, how Americano differs from Summit, and whether last night's results matter anywhere official. LobSmash replaces that with a single source of truth:

- **Shareable join codes and invite links** — 8-character codes plus public preview pages so players can verify a league before requesting to join.
- **Role-based access** — owners and admins approve members and gate result entry; nobody is silently added.
- **Format-aware leaderboards** — ranking rules match how your night actually runs (Summit, Americano, Round Robin, Mexicano).
- **A global skill rating** — one Elo-style number per player, reliability-weighted, that travels across every league they play in.
- **Friends, profiles, and history** — play style, preferred side, strengths and growth areas, plus a skill timeline.

For the full product narrative (audience, journeys, copy, roadmap), see [`lobsmash.md`](./lobsmash.md).

---

## Who it's for

| Audience | What they get |
| --- | --- |
| **Club and league organisers** | Create leagues, approve members, share codes, run sessions across courts. |
| **Admins** | Help manage rosters and results alongside the owner. |
| **Players** | Join leagues, play sessions, track standings and a portable skill rating, connect with friends. |

---

## Supported league formats

| Format | How it works |
| --- | --- |
| **Summit** | Players move up or down courts based on results. Standings emphasise wins and championship-court performance. |
| **Americano** | Partners rotate each game. Points from every game add up to crown the session leader. |
| **Round Robin** | Fair rotations against different opponents. Full scores across all courts feed the standings. |
| **Mexicano** | Mixer-style shuffles for partners and courts. Points across the session decide the ranking. |

---

## About this repository

This is the **marketing site only** — a static-rendered Next.js App Router project. It contains no authentication, no database, and no user-facing app state. Its sole job is to explain LobSmash and convert visitors into signed-up users on the main application.

### Tech stack

- **[Next.js 16](https://nextjs.org)** (App Router) with **React 19**
- **TypeScript 5**
- **Tailwind CSS v4** with **shadcn/ui** patterns and **Radix UI** primitives
- **Framer Motion** for scroll reveals and section transitions
- **Lucide** icons
- Deployed on **Vercel**

### Project structure

```
.
├── app/                    # Next.js App Router entry
│   ├── layout.tsx          # Root layout, fonts, metadata
│   ├── page.tsx            # Landing page composition
│   └── globals.css         # Tailwind layer + design tokens
├── components/             # Page sections
│   ├── navbar.tsx
│   ├── hero.tsx
│   ├── hero-highlights.tsx
│   ├── demo-section.tsx
│   ├── audience-section.tsx
│   ├── formats-section.tsx
│   ├── how-it-works-section.tsx
│   ├── pricing-section.tsx
│   ├── final-cta.tsx
│   ├── footer.tsx
│   ├── marketing-carousel.tsx
│   ├── motion-reveal.tsx
│   ├── padel-hero-decoration.tsx
│   └── ui/                 # shadcn/ui primitives (button, card, progress, switch)
├── lib/
│   ├── app-url.ts          # Resolves the target app URL for CTAs
│   └── utils.ts            # cn() helper
├── public/                 # Static assets, OG images, icons
└── lobsmash.md             # Source-of-truth product copy
```

---

## Getting started

### Prerequisites

- **Node.js 20+**
- **npm** (or pnpm / yarn / bun — lockfile is npm)

### Install and run

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Available scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the local development server with hot reload. |
| `npm run build` | Production build. |
| `npm start` | Serve the production build locally. |
| `npm run lint` | Run ESLint with `eslint-config-next`. |

---

## Environment variables

Copy `.env.example` to `.env.local` and fill in the values for your environment.

| Variable | Required | Description |
| --- | --- | --- |
| `NEXT_PUBLIC_APP_URL` | Yes (production) | Base URL of the LobSmash application that CTAs link to (e.g. `https://app.lobsmash.com`). Falls back gracefully in development. |

---

## Editing content

- **Hero, sections, and copy** — edit the matching component in [`components/`](./components). The page composition lives in [`app/page.tsx`](./app/page.tsx).
- **Design tokens (brand colors, surfaces, typography)** — `app/globals.css`.
- **Product copy reference** — [`lobsmash.md`](./lobsmash.md) is the canonical source for messaging; keep it in sync when shipping new features.
- **shadcn/ui components** — managed via `components.json`; re-add or update primitives with `npx shadcn@latest add <component>`.

---

## Deployment

The site is deployed to **Vercel**. `vercel.json` pins the framework; pushes to the production branch trigger automatic builds. Preview deployments are created for every pull request.

To deploy a fork or fresh instance:

1. Import the repository in Vercel.
2. Set `NEXT_PUBLIC_APP_URL` in the project's environment variables.
3. Deploy — no further configuration is required.

---

## Contributing

This is a product marketing site, so changes typically fall into three buckets:

1. **Copy updates** — keep [`lobsmash.md`](./lobsmash.md) and the relevant component in lockstep.
2. **Visual or structural changes** — edit the section components in [`components/`](./components); follow the existing Tailwind token conventions.
3. **New sections** — add a component, then mount it in [`app/page.tsx`](./app/page.tsx) in the order described at the bottom of `lobsmash.md`.

Run `npm run lint` before opening a pull request.

---

## License

Proprietary — © LobSmash. All rights reserved.
