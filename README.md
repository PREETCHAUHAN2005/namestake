# 📛 NameStake

> **Minimal. Permanent. On-Chain.**  
> The simplest way to register short, memorable names on the Stellar blockchain. Claim your identity for a flat one-time fee of 0.5 XLM and hold it forever—no renewals, no subscriptions.

[![Network: Stellar Testnet](https://img.shields.io/badge/Network-Stellar_Testnet-121D33?logo=stellar)](https://stellar.expert/explorer/testnet/contract/CDT57UR5LL6BMSM6YYZLGHSMJQ4KG27VQ2SU6RJOOXHW6XJU5XZ4J5S5)
[![Framework: Soroban](https://img.shields.io/badge/Smart_Contract-Soroban_v22-FF9200)](https://soroban.stellar.org/)
[![Frontend: React](https://img.shields.io/badge/Frontend-React_18_%2B_Vite-61DAFB?logo=react)](https://namestake.vercel.app)

---

## 📖 Table of Contents
- [The Vision](#-the-vision)
- [Live Environment](#-live-environment)
- [Rules & Economics](#-rules--economics)
- [Architecture](#-architecture)
- [Smart Contract Reference](#-smart-contract-reference)
- [Developer Quickstart](#-developer-quickstart)

---

## 🌌 The Vision

**NameStake** turns a familiar real-world workflow (domain registration) into a verifiable on-chain primitive on Stellar. Instead of relying on centralized registrars or complex subscription models like ENS, NameStake provides a raw, deterministic naming layer. 

By leveraging Soroban, it guarantees **transparent state transitions, user-authenticated actions, and immutable ownership.**

---

## 🔗 Live Environment

Test out the application on the Stellar Testnet right now:

- **🌐 Web Interface:** [namestake.vercel.app](https://namestake.vercel.app)
- **📜 Verified Contract:** [Stellar Expert Explorer](https://stellar.expert/explorer/testnet/contract/CDT57UR5LL6BMSM6YYZLGHSMJQ4KG27VQ2SU6RJOOXHW6XJU5XZ4J5S5)

---

## ⚖️ Rules & Economics

We designed the rules to be as frictionless and fair as possible:

### Registration Constraints
* **Length:** `3` to `20` characters.
* **Character Set:** Lowercase `a–z`, digits `0–9`, and hyphens `-`.
* **Formatting:** No leading or trailing hyphens permitted.
* **Availability:** Strictly first-come, first-served. 

### Protocol Fees
| Action | Fee | Details |
| :--- | :--- | :--- |
| **Claim** | `0.5 XLM` | One-time payment. No expiry. |
| **Transfer** | `0.2 XLM` | Send your name to any other Stellar address. |
| **Release** | `Free` | Burn the record and free the name (No refunds). |

---

## 🏗️ Architecture

NameStake is built across four distinct layers to ensure speed, security, and a seamless UX.

```text
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│                 │       │                 │       │                 │
│  React + Vite   │ ◄───► │ Freighter Wallet│ ◄───► │ Soroban RPC Node│
│  (Vercel Edge)  │       │ (Signer & Auth) │       │ (Stellar Test)  │
│                 │       │                 │       │                 │
└─────────────────┘       └─────────────────┘       └────────┬────────┘
                                                             │
                                                    ┌────────▼────────┐
                                                    │                 │
                                                    │  Rust Contract  │
                                                    │  (Core Logic)   │
                                                    │                 │
                                                    └─────────────────┘


