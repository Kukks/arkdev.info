---
sidebar_position: 4
title: 'Payments'
---

### Overview

Alice wants to send funds to Bob inside the Ark.

- All Ark payments and transactions are off-chain.
- Bob doesn't need to have funds inside the Ark to receive funds. (ie. inbound liquidity problem)
- Bob doesn't need to be online to receive funds
- Bob wil be required to be online **at least once every 4 weeks** to keep his funds safe.

### Timeline of events

1. Alice tells ASP to send [VTXO](/docs/learn/concepts#vtxo) to Bob
2. ASP (with Alice) prepares next [Round transaction](/docs/learn/concepts#round-transaction)
3. Alice creates a [Forfeit transaction](/docs/learn/concepts#forfeit-transaction):
   - spends from VTXO (1) via `Alice + ASP`
   - adds connector output from Round transaction (2) as input
   - signs (SIGHASH_ALL) and sends it to the ASP
4. ASP broadcasts [Round transaction](/docs/learn/concepts#round-transaction)
5. Bob has now a new [VTXO](/docs/learn/concepts#vtxo)
6. For at most 4 weeks, Alice will be able to double spend her [VTXO](/docs/learn/concepts#vtxo), but if she does it, the ASP will have time to grab the funds from the [VTXO](/docs/learn/concepts#vtxo) to itself using the [Forfeit transaction](/docs/learn/concepts#forfeit-transaction)
