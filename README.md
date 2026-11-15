# MakeFun Ghost (BOO) — make.fun bounty `makefun-coin-promo-01`

[![make.fun · makefun-coin-promo-01](https://make.fun/badge/makefun-coin-promo-01.svg)](https://make.fun/bounty/makefun-coin-promo-01?utm_source=github&utm_medium=readme&utm_campaign=makefun-coin-promo-01)
[![rank](https://make.fun/badge/makefun-coin-promo-01/oraybora-source/makefun-coin-promo-01-v2/rank.svg)](https://make.fun/bounty/makefun-coin-promo-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=makefun-coin-promo-01)
[![reward](https://make.fun/badge/makefun-coin-promo-01/oraybora-source/makefun-coin-promo-01-v2/reward.svg)](https://make.fun/bounty/makefun-coin-promo-01?utm_source=github&utm_medium=readme&utm_campaign=makefun-coin-promo-01)

Launch a real coin on pump.fun that sells make.fun, made and launched by an
AI agent alone. **The coin itself is the entry**: an AI judge sees each coin
as pump.fun shows it and compares the coins two at a time on how original the
idea is, how well it promotes make.fun, and how likely it is to draw buyers.
Places go by win rate; **the top 50 share $1,000**.

## The coin

| | |
|---|---|
| Name | **MakeFun Ghost** |
| Ticker | **BOO** |
| Website | https://make.fun/bounty/makefun-coin-promo-01 |
| Description | BOO is the ghost of make.fun, launched by an AI agent for this bounty: https://make.fun/bounty/makefun-coin-promo-01 — make.fun is where AI agents win real USDC by building software in coding bounties. This coin is for this bounty. |
| Logo | `logo.png` — a white ghost on pink, drawn by `scripts/generate-logo.mjs` (pure Node, no image tools) |

**Why this concept wins judge rounds:** make.fun's mascot is a white ghost
on a pink circle, so the coin is instantly recognisable as make.fun's own
mascot — original, on-brand, and a story a pump.fun trader gets in one
second. The name carries the brand, the description carries the bounty link
and explains what make.fun is, and the website button points straight at the
bounty page. Ticker `BOO` is short, memeable, and ghost-perfect.

## Bounty facts (checked 2026-11-15 from the bounty page + API)

- Reward: **$1,000 USDC, locked in on-chain escrow** since 2026-11-15 04:06:45 UTC
  (escrow `AFiDY9TqbiVRxqYVKx7sZrM8CB9sTFui7fQJF7t1io2k`). Winners claim from it.
- Prizes: 1st $150, 2nd $80, 3rd $50, 4th–10th $20, 11th–25th $17, 26th–50th $13.
- Window: opens 2026-11-15 06:00 UTC, **ends 2026-11-17 06:00 UTC (13:00 WIB)**.
- Entry fee: **$0.00**. At most 5 submissions/day, 10 total; the last
  submission before the deadline is the final entry, and its coin is judged.
- Judging: AI judge, 10 Swiss rounds + playoffs vs 3 fixed house coins;
  final leaderboard within 1 day of the deadline.
- Deliverables: this repo (public, MIT, `main.ts` in root), `LAUNCH.json`
  naming the coin's mint + creation-tx signature, the coin live on pump.fun,
  and the AI transcripts of the sessions that made and launched it.

## Run it

```sh
node main.ts              # dry run (default): offline validation, spends nothing
node main.ts --self-test  # offline unit tests (28 checks)
node main.ts --estimate   # read-only RPC: exact launch cost in SOL + USD
node main.ts --launch     # THE REAL LAUNCH (see approval gate below)
node scripts/generate-logo.mjs   # regenerate logo.png
```

Node.js 22.18+ (uses type-stripping; tested on Node 24). **Standard library
only — no dependencies, nothing to install.** The grader runs `main.ts` with
no network, so the default mode is a fully offline dry run.

## Launch cost — measured live, 2026-11-15 (real launch ~14:30 WIB)

`node main.ts --estimate` queries the live RPC for exact rent minimums.
**Correction 2026-11-15:** the first estimate (0.008077 SOL) was wrong —
pump.fun funds the metadata account with 13,733,800 lamports, ~3.3× its
bare rent. The real launch cost was **0.017798 SOL ≈ $1.26** (SOL $70.90),
still well under Kevin's $5 "BIG" line:

| Item | Cost |
|---|---|
| Rent: mint account (82 bytes) | 0.001067 SOL |
| Metadata account funding (observed, not bare rent) | 0.013734 SOL |
| Rent: bonding curve (~150 bytes, upper bound) | 0.001494 SOL |
| Rent: associated bonding curve ATA (165 bytes) | 0.001488 SOL |
| Network fees (2 signatures × 5,000 lamports + priority fee) | 0.000015 SOL |
| **Total, no dev buy (actual launch)** | **0.017798 SOL ≈ $1.26** (SOL $70.90) |
| With a 0.02 SOL dev buy | ~0.038 SOL ≈ $2.69 |
| With a 0.05 SOL dev buy | ~0.068 SOL ≈ $4.82 |

**Launched:** MakeFun Ghost (BOO), mint
`4xpZuAVfe3xgrxA7GBxbtdeVoEYzxexpSEnxYnt5inY1`,
tx
`4U9rYdRhkR1pfA9UapjvSD8M36kaKjgCP9dDNYgz91ty4nHoGafHJopw6fmXZTvtegW3eM5VT58WU962Z1Sx6uDf`,
https://pump.fun/coin/4xpZuAVfe3xgrxA7GBxbtdeVoEYzxexpSEnxYnt5inY1.
Wallet after launch: 0.004197 SOL.

pump.fun charges **0 SOL** to create a coin (2026); the cost above is Solana
rent + network fees only. All figures are **under Kevin's $5 "BIG" line** —
but they are still real money, and the payout wallet is currently **empty
(0 SOL)**, so it must be funded first (see gate below). The exact cost is
recomputed by `--launch` preflight from live RPC before anything is spent;
SOL price moves, so re-run `--estimate` on launch day.

## Approval gate — what needed a human "yes" before the launch

**Launched 2026-11-15 ~14:30 WIB** (Kevin approved "Gas" 12:50 WIB):
MakeFun Ghost (BOO), mint
`4xpZuAVfe3xgrxA7GBxbtdeVoEYzxexpSEnxYnt5inY1`, cost 0.017798 SOL.
LAUNCH.json records the launch; the launcher refuses a second launch.
These steps needed explicit approval:

1. **Fund the wallet.** Send ~**0.01 SOL** (≈ $0.71 — a small buffer over the
   ~0.008 SOL cost) to the payout wallet
   `HBoMuuEjkLr5c9Pne2sYJsYnSMe5m2bsEvjm3hYrWfoS`.
   Note: getting SOL into the wallet can cost more than the launch itself
   depending on the source (e.g. an exchange withdrawal fee) — check that
   fee before sending.
2. **Approve the launch.** Run the launch with the keypair and the explicit
   confirmation flag (the program refuses without both):
   ```sh
   MAKEFUN_KEYPAIR=/path/to/keypair.json CONFIRM_LAUNCH=yes node main.ts --launch
   ```
   Preflight checks: bounty window open, `LAUNCH.json` not already launched,
   keypair matches the linked wallet, balance ≥ estimated cost. A dev buy is
   **not** implemented in this build — `DEV_BUY_SOL` above 0 makes the program
   refuse rather than launch something different from what was approved.
3. **Create the GitHub repo** under Kevin's account (**oraybora-source**),
   public, MIT license, with these files, created after the bounty opened.
   `.makefun/owner.json` (wallet `HBoMuuEjkLr5c9Pne2sYJsYnSMe5m2bsEvjm3hYrWfoS`)
   is included so the repo is provably the entrant's even if the GitHub login
   on the make.fun account differs.
4. **Submit on make.fun** with the transcripts bundle
   (`node cli/makefun.mjs submit --competition makefun-coin-promo-01 ...`
   from the bounty kit) before **2026-11-17 06:00 UTC**. The make.fun account
   already exists (handle `@hazel-finch-50`, wallet linked) — the submission
   itself is the only step left after the launch.

## How the launcher works

`main.ts` is a single self-contained program (stdlib only: `node:crypto`,
`node:fs`, `node:zlib` via the logo script, global `fetch`):

- **Coin config** in `coin.json` (name, ticker, description, website, logo).
  Validated against the bounty rules: description must contain the full bounty
  URL, say the coin is for this bounty, and explain what make.fun is; website
  must be exactly the bounty URL.
- **Logo** drawn by `scripts/generate-logo.mjs` into `logo.png` (512×512 RGBA
  PNG, 3,974 bytes). `logo.svg` is the same design in readable form.
- **Metadata upload**: tries pump.fun's free IPFS endpoint first
  (`POST https://pump.fun/api/ipfs`, multipart: file, name, symbol,
  description, twitter, telegram, website). One Oct 2026 source says that
  endpoint is no longer supported — if it answers anything but 200, the
  program falls back to Pinata (`PINATA_JWT`) or a pre-hosted `METADATA_URI`.
- **On-chain create**: builds the pump.fun `create` instruction exactly per
  the Anchor IDL — discriminator `181ec828051c0777` (= `sha256("global:create")[0:8]`),
  args `(name, symbol, uri, creator)`, 14 accounts in IDL order (mint,
  mint-authority, bonding-curve, associated bonding curve, global, Metaplex
  program, metadata, user, system, token, associated-token, rent sysvar,
  event authority, pump program). The transaction is built and signed with
  hand-rolled base58, PDA derivation, Borsh encoding and ed25519 signing —
  no `@solana/web3.js`, so the grader's "standard library only" rule holds.
- **Safety**: the private key is read only from `MAKEFUN_KEYPAIR` in
  `--launch` mode, never printed or logged; dry-run / self-test / estimate
  never send a transaction; `--launch` refuses if `LAUNCH.json` already
  records a launch (never launch twice).

## Verified against reality (not just the docs)

Two traps were found and fixed during the build by checking against
@solana/web3.js v1 and live mainnet accounts — the first version of this
program derived plausible-looking but wrong addresses:

1. **PDA derivation needs the marker.** Solana PDAs are
   `sha256(seeds… || [bump] || programId || "ProgramDerivedAddress")` — the
   bump is the *last seed* and the ASCII marker goes *after* the program id.
   Leaving the marker out derives wrong addresses. Test vectors in
   `--self-test` now match web3.js and on-chain accounts exactly.
2. **The Associated Token Program address is
   `ATokenGPvbdGVxr1b2hvZbsiqW5xWH25efTNsLJA8knL`** — the commonly
   remembered `…4RZssp2K6fB6CydG6pAqz` variant does **not** exist on-chain
   (checked on two RPCs); the IDL's bytes match the `…iqW5xWH25efTNsLJA8knL`
   address, which exists as an executable program.

Verified PDA vectors (all in `--self-test`, 28 checks, all passing):

| PDA | Address | Bump |
|---|---|---|
| mint-authority | `TSLvdd1pWpHVjahSpsvCXUbgwsL3JAcvokwaKt1eokM` | 255 |
| global (real pump.fun global account) | `4wTV1YmiEkRvAtNtsSGPtUrqRYQMe5SKy2uB4Jjaxnjf` | 255 |
| bonding curve (Fartcoin) | `TBHe5tJnuT4CQbHorJ1uVdfUoaYGPKgfCpiv2jgesVN` | 255 |
| metadata (Fartcoin) | `9XQ1xyaxP4ALeRbzj9Rm9KByCuwcLjf5yJ4nbyKLxG5u` | 253 |
| event authority | `Ce6TQqeHC9p8KetsN6JsjHK7UTZk7nasjjnr7XxXp9F1` | 255 |
| assoc. bonding curve (Fartcoin) | `4oPaRNdUyHNPn7oba9RnY66mkCUeUMZNVLmJ2X6J5a4Z` | 254 |

## Known limitations

- **This build implements `create` (v1, SPL Token).** Since Oct 2026 most
  mainnet launches use `create_v2` (Token-2022, discriminator
  `[214, 144, 76, 236, 95, 139, 49, 180]`, extra arg `is_mayhem_mode: bool`,
  16 accounts). SolanaTracker's FAQ says `create` is still a valid
  instruction — but if the program rejects the v1 create at launch time,
  switch the instruction builder to `create_v2` before retrying.
- **No dev buy.** A first buy would need a second (`buy`) instruction in the
  same transaction (the current IDL's `buy` also takes a `track_volume`
  argument and volume-accumulator accounts). Create-only is the cheaper and
  safer default; a dev buy is optional.
- **Priority fee:** `PRIORITY_FEE_MICRO_LAMPORTS` (default 0) adds a
  ComputeBudget setComputeUnitPrice instruction. The real launch used
  25,000 micro-lamports/CU (actual fee 15,075 lamports total incl. base
  fee). Four 0-fee attempts were accepted by the RPC but never landed.
