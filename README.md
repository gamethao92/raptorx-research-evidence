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
