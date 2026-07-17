# Build on Bento - Hackathon Submission

Your **open pull request** is part of the submission. Organizers review and label PRs; they are **not merged** into `main`. `main` stays the blank template for the next team.

**Your PR will not be accepted until you also submit the official form:**  
[Build on Bento - BLR Edition form](https://forms.gle/UiJB7fVNCpwvnVLa7)

---

## How to submit (participants)

1. **Submit the form:** [forms.gle/UiJB7fVNCpwvnVLa7](https://forms.gle/UiJB7fVNCpwvnVLa7) (required - PR alone is not enough).
2. **Fork** this repo: [Bentodotfun/build-on-bento](https://github.com/Bentodotfun/build-on-bento)
3. In your fork, **fill in this README** (project, links, Bento integration, how to run).
4. Open a **Pull Request** into `Bentodotfun/build-on-bento` → `main`.
5. PR title: `[TeamName] ProjectName` (example: `[Alpha] MarketBot`).
6. Leave the PR **open**. Do not ask for a merge - acceptance is a label / comment from organizers, not a merge.

Judges use both the form and your PR (demo / video / source links inside).

---

## Project

| Field | Your answer |
|-------|-------------|
| **Project name** | `<!-- e.g. MarketBot -->` |
| **Tagline** | `<!-- one sentence -->` |
| **Team name** | `<!-- -->` |
| **Team members** | `<!-- name · GitHub · wallet (optional) -->` |
| **Contact email** | `<!-- -->` |
| **Track** (if applicable) | `<!-- Agents / Markets / Social / Open -->` |

### Links

| | URL |
|---|-----|
| **Live demo** | |
| **Demo video** (≤2 min) or slide deck | |
| **Pitch deck** (optional) | |

---

## What you built

Describe the product in 3-6 sentences: who it is for, what problem it solves, and how it uses Bento.

```
<!-- Write here -->
```

### Screenshots

Add 2-4 screenshots or GIFs under `./assets/` and embed them here.

```
<!-- ![Home](./assets/home.png) -->
```

---

## Bento integration

For each surface: put **Yes** or **No**. If Yes, briefly describe how (SDK methods, feature, etc.).

| Surface | Yes / No | Describe (if Yes) |
|---------|----------|-------------------|
| Markets / duels (browse, bet, create) | | e.g. `sdk.public.listDuels`, `sdk.user.placeBet` |
| Multi-outcome / parent markets | | |
| Parlays | | |
| Tournaments / F1 / fantasy | | |
| Packs | | |
| Polymarket bridge | | |
| Agents | | |
| Realtime / social | | |
| Credits (testnet) / USDC | | |

**Builder API key:** minted from [docs.bento.fun - Builder API key](https://docs.bento.fun/concepts/builder-api-key) (testnet). Do **not** commit keys.

---

## How to run

```bash
git clone <your-fork-or-source-url>
cd <project>
cp .env.example .env   # fill env vars below
npm install            # or pnpm / yarn
npm run dev
```

### Required env vars

| Env var | SDK option | Required | Description |
|---------|------------|----------|-------------|
| `BENTO_BUILDER_API_KEY` | `apiKey` | yes | Testnet builder key (`x-builder-api-key`) |
| `BENTO_URL` | `baseUrl` | yes | Markets host |
| `PARLAY_TOURNMENT_URL` | `tournamentsBaseUrl` | if using parlays / tournaments / F1 | Tournaments host (note the spelling: `TOURNMENT`) |

Testnet defaults (or use the hosts organizers give you):

```bash
export BENTO_BUILDER_API_KEY='bnt_…'   # from docs form
export BENTO_URL='https://internal-server.bento.fun'
export PARLAY_TOURNMENT_URL='https://bento-fun-tournaments-backend-3nku.onrender.com'  # only if you need sdk.tournaments
```

```ts
import { createBentoSdk, walletAuthProvider } from '@bento.fun/sdk';

const sdk = createBentoSdk({
  baseUrl: process.env.BENTO_URL!,
  apiKey: process.env.BENTO_BUILDER_API_KEY!,
  tournamentsBaseUrl: process.env.PARLAY_TOURNMENT_URL, // optional
  auth: walletAuthProvider(() => ({ Authorization: `Bearer ${userJwt}` })),
});
```

Omit `PARLAY_TOURNMENT_URL` if you only use markets (`sdk.public` / `sdk.user`).

---

## Architecture (short)

- **Stack:** `<!-- e.g. Next.js + @bento.fun/sdk -->`
- **Repo layout:** `<!-- apps/, packages/, bot/, … -->`
- **Auth:** `<!-- EOA login / weblink / agent -->`
- **What's on-chain vs off-chain:** `<!-- -->`

Optional: drop a simple diagram in `./assets/architecture.png`.

---

## Submission checklist

Before you open the PR:

- [ ] Submitted the [BLR Edition form](https://forms.gle/UiJB7fVNCpwvnVLa7) - **PR will not be accepted without this**
- [ ] Forked this repo and filled in this README
- [ ] PR title is `[TeamName] ProjectName`
- [ ] Project name, team, and contact filled in
- [ ] Live demo **or** clear local run instructions
- [ ] Demo video (≤2 min) **or** slide deck
- [ ] Bento integration table completed
- [ ] No secrets in the repo (`.env` gitignored)
- [ ] You understand: **PR stays open / gets closed - it will not be merged**

---

## Resources

| Resource | Link |
|----------|------|
| App | Mainnet: [app.bento.fun](https://app.bento.fun) · Testnet: [testnet.bento.fun](https://testnet.bento.fun) |
| Docs | [docs.bento.fun](https://docs.bento.fun) |
| Quickstart | [docs.bento.fun/quickstart](https://docs.bento.fun/quickstart) |
| Builder API key (testnet) | [docs.bento.fun/concepts/builder-api-key](https://docs.bento.fun/concepts/builder-api-key) |
| SDK (npm) | [`@bento.fun/sdk`](https://www.npmjs.com/package/@bento.fun/sdk) |

```bash
npm install @bento.fun/sdk
```

---

## License

Unless you specify otherwise in your fork, keep your submission code under a license of your choice. This template repo is provided by Bento for hackathon submissions only.
