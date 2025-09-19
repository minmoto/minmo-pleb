# Minmo Escrow & Dispute System

## Executive Summary

Minmo is building an **open, censorship-resistant agent exchange layer** that allows communities in Africa and the Global South to swap between Bitcoin and local fiat with fairness, safety, and transparency.
Our goal is to solve the hardest problem in Bitcoin adoption: **reliable liquidity access for everyday users**, without relying on centralized exchanges.

We provide:

- A **common solution layer** for swaps that any community or app can embed.
- A flexible **escrow + dispute resolution system** that ensures trust between users and agents.
- Open standards designed to **interoperate with other projects** in this space.

## The Problem Space

In the Global South, users face unique challenges when trying to swap between fiat and Bitcoin:

- **Liquidity gaps** – Centralized exchanges often ignore smaller markets, leaving communities dependent on informal P2P trades.
- **Unreliable agents** – Local money changers operate without escrow, leading to disputes and loss of funds.
- **Payment fragmentation** – QR banking codes, mobile money, and bank transfers coexist, but no single system supports them all.
- **High risk of fraud** – With fiat moving outside the blockchain, disputes are common and hard to resolve.

Without reliable swap infrastructure, adoption stalls even if people want to hold or use Bitcoin.

## Common Solution Layer

Minmo provides a **layer for safe swaps**:

- **Escrow first**: BTC is locked before fiat moves.
- **Timeouts everywhere**: no funds can remain locked forever.
- **Evidence-based disputes**: both sides can submit proof, system resolves fairly.
- **Multi-rail support**: QR codes, mobile money, and bank transfers all supported.

This layer can be embedded into apps, integrated with federations, or run by independent agents.

## High-Level Components

- **Agent Network** – individuals who provide liquidity, either on-ramp or off-ramp.
- **Escrow Service** – holds BTC until swap conditions are met.
- **Dispute Engine** – resolves disputes using timeouts + evidence rules.
- **Swap Lifecycle** – standard state machine for both on-ramp and off-ramp swaps.

For detailed specs see:

- [Escrow Flows](./escrow-flows.md)
- [Dispute Flows](./dispute-flows.md)

## Solution Deep Dive

### Parties Involved

- **Maker** – provides liquidity (BTC or fiat).
- **Taker** – initiates a swap.

### Flows

- **Off-Ramp (BTC → Fiat)**: user deposits BTC, agent sends fiat, BTC released after confirmation.
- **On-Ramp (Fiat → BTC)**: agent locks BTC, user sends fiat, BTC released after confirmation.

### Dispute Resolution

- **Payment disputes** → evidence from both sides, auto-resolved after timeout.
- **Unresponsiveness** → timeouts decide in favor of the responsive party.
- **Partial payments / invalid details** → proportional split or refund.

See [Dispute Flows](./dispute-flows.md) for details.

## Similar Efforts

We are not alone in this mission. Projects like **OpenPleb** are building censorship-resistant off-ramp systems.

- **OpenPleb GitHub Repo**: [gandlafbtc/open-pleb](https://github.com/gandlafbtc/open-pleb)

### Comparison


| Aspect           | OpenPleb          | Minmo                                               |
| ---------------- | ------------------- | ------------------------------------------------- |
| Swap direction   | Off-ramp only     | Both on-ramp & off-ramp                             |
| Fiat Channels    | Bank QR codes     | QR, mobile money, bank transfers                    |
| Escrow mechanism | Cashu token bonds | Fedimint ecash + evidence disputesTime-locked       |
| Dispute coverage | Payment disputes  | Payment, unresponsiveness, partial, invalid details |

See [Comparison with OpenPleb](./comparison-open-pleb.md).

## Possible Collaboration

We believe the ecosystem grows stronger when projects work together.Opportunities for collaboration include:

- **Open source alignment** – publish and evolve specs together.
- **Shared escrow tech** – align on state machine and auto-release rules.
- **Shared dispute resolution logic** – open standards for evidence and outcomes.

## Next Steps

This repo provides the foundation for Minmo’s escrow and dispute system.Please see the following documents for more details:

- [Escrow Flows](./escrow-flows.md)
- [Dispute Flows](./dispute-flows.md)
- [Comparison with OpenPleb](./comparison-openpleb.md)
