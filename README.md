# NameStake

Register short names on the Stellar blockchain and link them to your wallet address. Like ENS but minimal — pay 0.5 XLM, get a permanent on-chain identity. Transfer it, release it, or hold it forever.

## Live Links

| | |
|---|---|
| **Frontend** | `https://namestake.vercel.app` |
| **Contract** | `https://stellar.expert/explorer/testnet/contract/CDT57UR5LL6BMSM6YYZLGHSMJQ4KG27VQ2SU6RJOOXHW6XJU5XZ4J5S5` |

## Rules

- Names: 3–20 characters, lowercase `a–z`, digits `0–9`, hyphens
- No leading or trailing hyphens
- First-come, first-served — no expiry
- Claim fee: **0.5 XLM** · Transfer fee: **0.2 XLM** · Release: free

## Why This Project Matters

This project turns a familiar real-world workflow into a verifiable on-chain primitive on Stellar: transparent state transitions, user-authenticated actions, and deterministic outcomes.

## Architecture

- **Smart Contract Layer**: Soroban contract enforces business rules, authorization, and state transitions.
- **Client Layer**: React + Vite frontend handles wallet UX, transaction composition, and real-time status views.
- **Wallet/Auth Layer**: Freighter signs every state-changing action so operations are attributable and non-repudiable.
- **Infra Layer**: Stellar Testnet + Soroban RPC for execution; Vercel for frontend hosting.
## Contract Functions

```rust
claim(claimer, name, xlm_token)
transfer(from, to, name, xlm_token)
release(owner, name)                   // no refund
lookup(name) -> Option<NameRecord>
reverse_lookup(owner) -> Vec<String>
is_available(name) -> bool
total_names() -> u32
```

## Stack

| Layer | Tech |
|---|---|
| Contract | Rust + Soroban SDK v22 |
| Network | Stellar Testnet |
| Frontend | React 18 + Vite |
| Wallet | Freighter v1.7.1 |
| Hosting | Vercel |

## Run Locally

```bash
chmod +x scripts/deploy.sh && ./scripts/deploy.sh
cd frontend && npm install && npm run dev
```


