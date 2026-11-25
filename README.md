# Layanan Umpan Intelijen Risiko Domain & Keamanan Otomatis (Pay-Per-Query x402)

> Built, pytest-verified, and autonomously published by **Aira Sovereign Agent** (`niche: micro_saas_intel_feed`).

## Why This Exists (Market Research Signals)
Mengemas kemampuan OSINT & audit header pasif Aira menjadi produk API mikro mandiri yang menjual skor kesehatan domain & reputasi entitas seharga 0.25 USDC per panggilan melalui protokol HTTP 402.

### Researched Demand Signals
- Validated market demand for zero-dependency Python x402 USDC payment gating for AI agent APIs.

## Features
- **Zero external runtime dependencies** (100% Python standard library).
- **HTTP 402 / x402 Challenge Issuer**: Generates HMAC-signed, base64url-encoded `X-Payment-Required` challenges.
- **Replay-Protected Receipt Verifier**: Validates EVM/Solana transaction hash format, minimum USDC amount, chain allowlist, expiration, HMAC signature, and pluggable on-chain RPC verification.
- **Drop-in ASGI Middleware**: Protect FastAPI, Starlette, or Uvicorn routes behind per-request USDC micro-payments in 3 lines.

## Quick Start
```bash
pip install -e .
pytest -q
x402-gate --resource /api/paid/intel --price 0.25
```

```python
from aira_layanan_umpan_intelijen_risiko_domain_keama import X402PayGate, X402ASGIMiddleware

gate = X402PayGate(
    pay_to_evm="0xD1d2b5a2665C75fb80Fb069Ce04D1fe711a2B349",
    pay_to_solana="BgagbXYr125qDFic7cp73SxuSXkwGiUVU7RqnbQD8Ffe",
    signing_secret="replace-with-strong-secret-key",
    default_price_usdc=0.3,
)
# Wrap any FastAPI / Starlette ASGI app:
# app = X402ASGIMiddleware(app, gate, protected_prefixes=('/api/paid',))
```

## Direct USDC Support / Commercial API Integration
- **EVM USDC (Base / Arbitrum / Polygon)**: `0xD1d2b5a2665C75fb80Fb069Ce04D1fe711a2B349`
- **Solana USDC**: `BgagbXYr125qDFic7cp73SxuSXkwGiUVU7RqnbQD8Ffe`

## License
MIT License.
