# On-chain verification of the instrument behind the SOL 15m report
Captured 2026-10-28T14:08Z. Independent of RaptorX: raw `eth_call` on two Base RPCs plus a DexScreener snapshot.

## 1. What `0x3119…cf82` actually is

The report flagged that the contract address is Ethereum-style "while this is labeled Solana/SOL" and listed a ~$28.6M market cap as inconsistent with SOL's supply. Both facts resolve with two reads:

| Call | Selector | Raw result | Decoded |
|---|---|---|---|
| `name()` | `0x06fdde03` | `0x…0020 0x0006 536f6c616e61…` | `Solana` |
| `symbol()` | `0x95d89b41` | `0x…0020 0x0003 534f4c…` | `SOL` |
| `decimals()` | `0x313ce567` | `0x09` | `9` |
| `totalSupply()` | `0x18160ddd` | `0x010105e984c34c` | `282,599.880966988` |

Identical on `base-rpc.publicnode.com` and `1rpc.io/base`.

So the instrument is a **Base chainId-8453 ERC-20 named "Solana", symbol "SOL", 9 decimals, with a total supply of 282,599.88 tokens**. At the report's own price of $101.09 that is **$28,567,421 — the exact ~$28.6M the report called inconsistent**. The figure was never a data error: it is this token's float × price. The report's "possible wrapped/bridged asset" caveat is confirmed — the feed is a Base representation of SOL (9-decimal, name/symbol matching), not native Solana spot.

## 2. How much depth the "thin volume" claim really describes

DexScreener snapshot (`data/dexscreener_token_pairs_2026-10-28T1408Z.json`): the token is base in **25 pools on Base** across Aerodrome/Aero, PancakeSwap, Uniswap, Equalizer and Hydrex, plus 5 pools where it is the quote asset.

| Measure | Value |
|---|---|
| Aggregate liquidity, 25 SOL-base pools | **$2,804,652** |
| Aggregate 24h volume, same pools | **$12,651,695** |
| Aggregate 1h volume, same pools | **$1,018,508** |

Largest venues:

| Pool | Liquidity | 24h volume |
|---|---|---|
| PancakeSwap SOL/cbBTC `0x8Df6dd38D7` | $725,924 | $473,626 |
| Aero SOL/cbBTC `0xc01c280018` | $548,696 | $5,753,068 |
| PancakeSwap SOL/WETH `0xab07dE353E` | $495,159 | $826,686 |
| Aero SOL/USDC `0x868Eed6BAD` | $489,866 | $4,170,655 |
| Aerodrome SOL/USDC `0x1131DB5977` | $129,693 | $358,242 |

The report's **~$425K** matches a single Aerodrome SOL/USDC pool (~$358K/24h on $130K of liquidity), not the token. Market-wide the same asset does ~$12.7M/24h with ~$1.02M in the last hour — about **30× the volume the report used for its "thin book" verdict**.

## 3. Which Aerodrome pool cannot be the one charted

Calling the Aerodrome v1 factory `0x420DD381b31aEf6683db6B902084cB0FFECe40Da`:

- `getPool(SOL, USDC, stable=false)` → `0xb98Fb80d89d9cF33C3726843fcBF68E6a7D64c00`, reserves **0.000754938 SOL / 0.077352 USDC** (dust, $0 liquidity); pool `totalSupply` 2.36e-13.
- `getPool(SOL, USDC, stable=true)` → `0x0` (no stable pool).

A chart labelled "Aerodrome SOL/USDC" therefore cannot be the canonical factory pool — the venue actually carrying the flow is the Aero `0x868E…` SOL/USDC pool ($490K liquidity, $4.17M/24h).

## 4. What this does to the technical read

- **Distinct supplies, distinct meaning.** 282,599 tokens of a Base representation vs native SOL: the 15m MACD/RSI describe flow in this token's pools, not Solana validator-side spot. Anyone trading the "SOL" chart should know the float is ~283K, not hundreds of millions.
- **The noise-floor threshold is venue-specific.** The model's $1–2M/day floor is cleared ~12× market-wide, but the pool the report charted (~$358K/24h) sits below it. Same asset, opposite conclusion — the threshold must be applied to the pool, not the ticker.
- **Splitting the answer.** The report could not say whether the momentum was genuine or a low-float artifact. Data says both layers exist: real aggregate depth, thin per-pool depth. A cross-venue check (do the five largest pools agree on the 15m bar?) separates them; diverging pool-level MACD is flow, agreeing pool-level MACD is (bridged) spot.

## Reproduce

```bash
# metadata
curl -s -H 'content-type: application/json' --data \
 '{"jsonrpc":"2.0","id":1,"method":"eth_call","params":[{"to":"0x311935Cd80B76769bF2ecC9D8Ab7635b2139cf82","data":"0x18160ddd"},"latest"]}' \
 https://base-rpc.publicnode.com

# pools
curl -s https://api.dexscreener.com/latest/dex/tokens/0x311935Cd80B76769bF2ecC9D8Ab7635b2139cf82
```

Third-party caveat: DexScreener figures are an indexer snapshot at 14:08Z, and the exact pool RaptorX charts is inferred from volume/liquidity agreement, not read from the platform's internals.
