# RaptorX Research Challenge — Entry Evidence

**Challenge:** Ask Better Questions. Find Better Alpha.
**Chosen asset:** SOL (Solana) — native Solana token, legitimate / established.
**Participant wallet (Base, self-owned):** `0xB6E8A315CA639bcA70BeD7ff8c391b0cEbdC0c58`
**Platform:** https://www.raptorx.trade — logged in via wallet SIWE (Privy embedded wallet).

This entry contains (1) a genuine AI research report generated on RaptorX and (2) the original, report-grounded questions asked to RaptorX's Claw AI 5.0 model. All artifacts were produced inside the live RaptorX UI; screenshots are in `screenshots/`.

---

## 1. AI Research Report generated on RaptorX

Generated via **RexScreener → Solana → Intelligence Report → "Generate all technical indicators at once"** (MACD + RSI + Cup & Handle), "AI-powered analysis using TradingView data".

- Screenshot: `screenshots/01_report_generation_panel.png` (shows the Solana Technical Analysis panel, "Generated!", RSI Indicator, Cup & Handle, TradingView data source, and the live SOL/USDC Aerodrome chart).
- Full extracted report text: `report_solana_15m.txt` (verbatim Claw AI output for "SOL Technical Analysis — 15-Minute Timeframe", 8 sections, confidence 5/10).

**Key findings I built my questions on:**
- MACD histogram just flipped −0.001 → +0.002; bullish cross at position 5 after a bearish cross at position 2; **values compressed near zero**.
- RSI **dead-neutral at 50**, sequence 45→48→52→58→62→65→60→55→50; **bearish divergence at position 6** vs bullish at position 2.
- Volume only ~$425K (thin); Cup & Handle confidence **22.32%** with a mechanical target ~$105.92.
- The instrument's contract address `0x311935Cd80B76769bF2ecC9D8Ab7635b2139cf82` is **Ethereum-style**, inconsistent with native Solana — the report itself flags this as a possible wrapped/bridged asset or data mismatch.
- Overall conviction **5/10**.

---

## 2. Questions asked to RaptorX Claw AI 5.0 (Solana data source)

Screenshots: `screenshots/02_claw_question_1.png`, `screenshots/03_claw_questions_2_3.png` (questions rendered in the Claw AI 5.0 chat, Solana mode, logged-in wallet visible).

**Q1 — conflicting momentum vs divergence (the central tension in the report):**
> Your SOL 15m technical report shows a fresh bullish MACD crossover (histogram flipping +0.001 to +0.002, MACD line above signal) yet at the same time a bearish RSI divergence at position 6 and RSI sitting dead-neutral at 50, with MACD values compressed near zero and only ~$425K volume. When a new momentum cross and a divergence conflict like this on an intraday timeframe, which signal should I actually weight for directional edge, and what concrete volume or market-depth threshold would move your read from 'range-bound with upward bias' to a real breakout rather than noise?

**Q2 — data-integrity / genuine-vs-bridged exposure (challenges the report's own caveat):**
> The report flags that the instrument's contract address is an Ethereum-style (0x3119...) address while this is labeled Solana/SOL. If this is wrapped/bridged SOL on Aerodrome, how much of the momentum and volume signal I'm reading is genuine Solana exposure versus a bridged-asset liquidity artifact, and which on-chain metric would you check to separate the two?

**Q3 — curve-fitting vs resolution (interrogates the low-confidence pattern target):**
> You rated conviction 5/10 partly because the pattern confidence is only 22% and the target ~$105.9 is a mechanical output. If I treat the conflicting MACD/RSI as the central question, is a higher-timeframe (1h/4h) re-run the right way to resolve it, or would that just be curve-fitting? What would you look for in the order book or funding to confirm which of the two diverging signals is the real one?

**Q4 — liquidity/holder concentration risk (grounded in the pair's ~45 LPs, ~30K holders, thin volume):**
> The report leans on thin ~$425K volume, and this pair shows only ~45 liquidity providers and ~30K holders. How exposed is the bullish MACD read to a single large LP pulling depth or a top-holder sell — is the 'upward bias' actually robust, or an artifact of a shallow book? What LP-depth or holder-concentration level would make you discount the signal entirely?

**Q5 — beta vs idiosyncratic strength (grounded in the live BTC ~$80.5K readout):**
> SOL's intraday momentum here is read in isolation, but the terminal shows BTC around $80.5K. If SOL's bullish MACD cross is mostly beta to a broader large-cap bounce rather than idiosyncratic strength, how would I separate correlation-driven movement from genuine SOL-specific accumulation, and does that change how much weight the MACD/RSI divergence conflict deserves?

Screenshots: `02_claw_question_1.png`, `03_claw_questions_2_3.png`, `04_claw_question_4_liquidity_concentration.png`, `05_claw_question_5_beta_vs_idiosyncratic.png`.

Each question connects a specific report/on-page finding to a market hypothesis, contradiction, or risk — rather than asking for a price prediction.

> Note on AI responses: at the time of capture, RaptorX's Claw AI 5.0 answers were not returning because the platform's Helius Solana RPC key was rate-limited (HTTP 429 "max usage reached") on the backend. The questions above were submitted and recorded in the Claw AI 5.0 chat (visible in the screenshots and the platform's chat history).

---

## 3. Second Solana report (fresh snapshot) + Q6 — deepening the analysis on the same eligible asset

The challenge rewards a small number of *exceptional* questions and permits any number of reports, provided the asset is on **Solana**. Rather than straying off-asset, I generated a **second, independent SOL Intelligence Report on the same Solana asset at a later live snapshot** (SOL ~$101.09, +0.74%) and used the new data to ask a sharper question.

- Full extracted report text: `report_solana_15m_v2.txt` (verbatim Claw AI output — overall conviction **4/10**, vs the first report's 5/10).
- Screenshot: `screenshots/06_solana_report_v2_fresh.png`.

**The new report surfaced a contradiction worth interrogating:** the model explicitly disowned its own pattern layer — cup-and-handle "detection parameters are mismatched to the actual price scale," the ~$117 target "should be disregarded," and the reported market cap (~$28.6M) is "inconsistent with SOL's actual supply" (likely exchange-specific / low-float).

**Q6 — data provenance of the entire technical layer (challenges whether the momentum signal is independent confirmation or inherits the same flaw):**
> Your fresh SOL report explicitly distrusts its own pattern layer — it says the cup-and-handle detection is "mismatched to the actual price scale," the ~$117 target "should be disregarded," and the market cap (~$28.6M) is "inconsistent with SOL's actual supply." Yet you still returned a mildly bullish MACD/RSI momentum read at only 4/10. If mcap, pattern, and volume are all flagged unreliable, what is the actual provenance and integrity of the OHLCV series feeding MACD and RSI themselves? Are those exact price/volume bars drawn from the same mislabeled, exchange-specific low-float pair — meaning the 4/10 momentum read inherits the same data flaw you flagged in the pattern layer, rather than being an independent confirmation of it?

Screenshot: `screenshots/07_claw_question_6_provenance.png` (Q6 rendered in the Claw AI 5.0 chat, Solana mode, logged-in wallet visible).

This question goes a level deeper than Q1–Q5: instead of asking the AI to weigh conflicting signals, it attacks the **input integrity** the signals are built on — the model's momentum "confirmation" may be the same low-float artifact it already dismissed in the pattern layer.

---

## Method / reproducibility
Headless Chrome (puppeteer-core) driving the live raptorx.trade UI; wallet login via Privy SIWE with the self-owned Base key; report generated through the Intelligence Report panel; questions typed into Claw AI 5.0 in Solana mode. Screenshots captured directly from the rendered pages.

---

## 4. 2026-10-28 update — Claw AI 5.0 answers now return, and they answer Q7

The earlier captures were blocked by a backend RPC rate limit, so they show questions only. On **2026-10-28** the same logged-in wallet (same account, same chat history) got a full model response, so this section records a genuine question → answer exchange rather than a bare prompt.

**Q7 — the strongest version of the Q1 tension, made falsifiable (bridged-feed + thin-book + noise floor in one question):**
> Your SOL 15m report shows a fresh bullish MACD crossover (histogram -0.001 -> +0.002) while RSI sits at a dead-neutral 50 and prints a bearish divergence at position 6, on only ~$425K daily volume - and the instrument's contract address is an Ethereum-style 0x3119... rather than a Solana mint. If that means this feed is bridged/wrapped SOL traded on a Base DEX pool rather than native Solana spot, then part of what the report labels 'SOL momentum' is really pool flow. Which on-chain series - pool TVL delta, net LP adds, or top-holder net transfer - would you pull first to decide whether the MACD flip is genuine spot demand or thin-book noise, and at what dollar volume does a 15m indicator stop being informative?

**Answer (verbatim, 3.2 KB, full text in `transcript/claw_q1_answer_net_lp_adds.txt`):** the model accepted the bridged-feed premise ("likely a wrapped SOL variant like cbSOL or axlSOL") and answered with a decision rule instead of a price call:

- **Ranked metric:** net LP adds/removals first — "thin-book noise: MACD flips bullish, but Net LP is negative"; "genuine demand: MACD flips bullish, and Net LP is positive".
- **Why not holders:** top holders of a bridged Base asset are usually bridge contracts (Across, Stargate) or the DEX router, so holder concentration is "misleading for bridged assets".
- **Noise floor:** "indicators typically lose predictive power when daily volume drops below $1M–$2M", with the arithmetic spelled out (at ~$425K/day a single $2,000 buy is ~50% of a 15m candle).
- **Falsification tests:** disregard the MACD if ±2% depth < $10,000; cross-check Polymarket SOL odds; require a $15k–$20k spike in one 15m candle before trusting the crossover.

That reply is the kind of reasoning the brief asks for — it took the report's own internal contradiction (Ethereum-style contract on a "Solana" asset), turned it into a hypothesis about pool flow, and returned measurable thresholds that can be checked later rather than a direction call.

- Screenshots: `screenshots/08_claw_q1_sol_momentum_question.png` (question + 15m MACD report in the chat, logged-in avatar), `screenshots/09_claw_q1_answer_report_body.png`, `screenshots/10_claw_q1_answer_key_levels.png`, `screenshots/11_claw_q1_answer_sources.png`.
- Raw page dumps: `transcript/claw_q1_page_dump.txt` (chat DOM text at capture time).

> Honest note on the UI: RaptorX's own ad unit renders a third-party "new airdrop" string into the chart header and the exchange widget in these captures (visible above the MACD chart). It is the platform's UI, not part of the report text or the model's answer.

---

## 5. Independent on-chain check of the report's own data caveat (2026-10-28T14:08Z)

The model answered Q1 but Q6 (provenance of the OHLCV feed) stayed unanswered, so I verified the instrument directly instead of asking again. Full write-up: `onchain_verification.md`; raw reads: `data/token_metadata.json`; pool snapshot: `data/dexscreener_token_pairs_2026-10-28T1408Z.json`.

**The address is a real Base ERC-20, and the "wrong" market cap is not a bug.** `eth_call` on two independent RPCs (`base-rpc.publicnode.com`, `1rpc.io/base`) returns `name()="Solana"`, `symbol()="SOL"`, `decimals()=9`, `totalSupply()=282,599.880966988`. At the report's $101.09 that is **$28,567,421 — the exact ~$28.6M** the v2 report called "inconsistent with SOL's actual supply". It was this token's float all along, which confirms the report's wrapped/bridged-asset caveat rather than a data mismatch.

**The "thin $425K" verdict describes one pool, not the asset.** The token is base in 25 Base pools (Aerodrome/Aero, PancakeSwap, Uniswap, Equalizer, Hydrex): aggregate liquidity **$2.80M**, 24h volume **$12.65M**, last-hour volume **$1.02M**. The ~$425K matches a single Aerodrome SOL/USDC pool ($129,693 liquidity, $358,242/24h) — ~30× below the asset's actual turnover. The deepest SOL/USDC venue is Aero `0x868Eed6BAD…` ($489,866 liquidity, $4.17M/24h).

**The canonical Aerodrome pool is empty.** Aerodrome v1 factory `0x420D…40Da`: `getPool(SOL,USDC,false)` = `0xb98Fb80d…` with reserves 0.000754938 SOL / 0.077352 USDC; no stable pool exists. A chart labelled "Aerodrome SOL/USDC" cannot be that pool.

**Why it matters for the question:** the model's $1–2M/day noise floor is cleared ~12× market-wide but *not* in the pool the report charted — so the threshold has to be applied per venue, and the 15m MACD/RSI describe bridged-pool flow, not native Solana spot. That is the answer to Q6 obtained from data rather than from the model.

---

## 6. Executed falsification test: can the report's indicators be reproduced from public data? (2026-10-28T14:12Z)

Full write-up `cross_venue_test.md`; computed series `data/rsi_replication_2026-10-28.json`. The v2 report is timestamped `2026-10-27T21:07Z`, inside every feed's window, so this is like-for-like.

RSI(14) is scale-free and therefore the clean target. The report prints `45 → 48 → 52 → 58 → 62 → 65 → 60 → 55 → 50`. Recomputed on 15m closes at that bar for **8 Base SOL pools** (Aerodrome/Aero, PancakeSwap, Uniswap; USDC/WETH/cbBTC) plus **Binance** and **OKX**:

- No series matches: best case is still **7.6 RSI points** off (Aero SOL/WETH), worst **16.1**, and the *shape* is wrong everywhere — real series stay inside a 48–62 band instead of climbing to 65 and decaying to 50.
- The MACD sign is inverted: the report says the histogram "just flipped positive (+0.002)"; on all ten series that bar reads **−0.019 to −0.084**.
- It is not a quote-asset mix-up — WETH, USDC, cbBTC pools and two CEX feeds all disagree the same way.

Honest limit: TradingView may aggregate venues in a way none of these sources does, so this proves **non-reproducibility from public data**, not fabrication. Together with the same report's self-disclaimed pattern layer ("parameters mismatched", confidence 9.78%), the conclusion is that the technical layer's provenance is unverified and its momentum and pattern layers are not independent confirmations of each other — which is Q6, answered with a test instead of a re-ask.
