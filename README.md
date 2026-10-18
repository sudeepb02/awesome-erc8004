<div align="center">
  <img src="./assets/logo.png" alt="ERC-8004 Logo" width="300"/>

  # Awesome ERC-8004

  <p><strong>A curated list of awesome resources for ERC-8004: Trustless Agents</strong></p>
</div>

---

## Table of Contents

- [What is ERC-8004?](#what-is-erc-8004)
- [Official Resources](#official-resources)
- [Specification](#specification)
- [Community Calls & Content](#community-calls--content)
- [Builder Projects](#builder-projects)
- [Discussions & Forums](#discussions--forums)
- [Research & Papers](#research--papers)
- [Explorer & Scanner Tools](#explorer--scanner-tools)
- [Development Resources](#development-resources)
- [Smart Contract Interfaces](#smart-contract-interfaces)
- [Standards & References](#standards--references)
- [Related Standards](#related-standards)
- [FAQ](#faq)

---

## What is ERC-8004?

ERC-8004 is an Ethereum standard that extends the Agent-to-Agent (A2A) Protocol with a trust layer, enabling participants to discover, choose, and interact with agents across organizational boundaries without pre-existing trust. It introduces three lightweight, on-chain registries:

### Core Components

| Registry                | Purpose                                | Details                                  |
| ----------------------- | -------------------------------------- | ---------------------------------------- |
| **Identity Registry**   | Agent discovery & portable identifiers | ERC-721 with URIStorage                  |
| **Reputation Registry** | Feedback & attestation system          | Standard interface for scores & metadata |
| **Validation Registry** | Independent verification hooks         | Generic validation framework             |

### Key Properties

- **Cross-organizational Discovery** - Agents can be found without pre-existing relationships
- **Flexible Endpoints** - Support for A2A, MCP, ENS, DIDs, and wallet addresses
- **Modular Trust** - Pluggable trust models from low-stake to high-stake interactions
- **On-chain Composability** - Smart contracts can read reputation and validation data
- **Gas Efficiency** - Off-chain data storage with on-chain integrity
- **ERC-721 Compatibility** - Full compatibility for NFT marketplace integration

### Trust Models

1. **Reputation-based** - Client feedback using signed fixed-point values, tags, and metadata
2. **Crypto-economic** - Stake-secured validation with economic incentives
3. **Crypto-verification** - TEE attestations and zkML proofs for cryptographic trust

## Official Resources

- **[ERC-8004 Official Website](http://8004.org)** - Official website for ERC-8004: Trustless Agents
- **[EIP-8004 Specification](https://eips.ethereum.org/EIPS/eip-8004)** - Official Ethereum Improvement Proposal
- **[ERC8004SPEC.md](https://github.com/erc-8004/erc-8004-contracts/blob/master/ERC8004SPEC.md)** - Specification file in the contracts repository
- **[ERC-8004 Best Practices](https://github.com/erc-8004/best-practices)** - Official guides covering agent registration (`Registration.md`) and reputation usage (`Reputation.md`)
- **[8004.org/build](https://www.8004.org/build)** - Developer hub with tools, SDKs, and integration resources
- **[8004.org Blog](https://www.8004.org/blog)** - Official blog
- **[A2A Protocol Specification](https://a2a-protocol.org/latest/specification/)** - Agent-to-Agent Protocol that ERC-8004 extends

## Specification

### Current Status

- **Status**: Draft (EIP process), contracts are audited and final
- **Registries**: Identity and Reputation final contracts deployed; Validation Registry under active revision
- **Specification**: [ERC8004SPEC.md](https://github.com/erc-8004/erc-8004-contracts/blob/master/ERC8004SPEC.md) in the contracts repository

### Architecture Overview

```
┌─────────────────┐
│ Agent           │
│ Discovery       │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Identity        │
│ Registry        │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Agent           │
│ Registration    │
└────┬───────┬────┘
     │       │
     ▼       ▼
┌─────────┐ ┌─────────────┐
│ Rep.    │ │ Validation  │
│ Registry│ │ Registry    │
└────┬────┘ └──────┬──────┘
     │             │
     └──────┬──────┘
            ▼
    ┌─────────────────┐
    │ Trust           │
    │ Assessment      │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │ Agent           │
    │ Interaction     │
    └─────────────────┘
```

### Agent Registration Schema

```json
{
  "type": "https://eips.ethereum.org/EIPS/eip-8004#registration-v1",
  "name": "myAgentName",
  "description": "A natural language description of the Agent...",
  "image": "https://example.com/agentimage.png",
  "services": [
    {
      "name": "web",
      "endpoint": "https://web.agentxyz.com/"
    },
    {
      "name": "A2A",
      "endpoint": "https://agent.example/.well-known/agent-card.json",
      "version": "0.3.0"
    },
    {
      "name": "MCP",
      "endpoint": "https://mcp.agent.eth/",
      "version": "2025-06-18"
    },
    {
      "name": "OASF",
      "endpoint": "ipfs://{cid}",
      "version": "0.8",
      "skills": [],
      "domains": []
    },
    {
      "name": "ENS",
      "endpoint": "agent.eth",
      "version": "v1"
    },
    {
      "name": "DID",
      "endpoint": "did:method:foobar",
      "version": "v1"
    },
    {
      "name": "email",
      "endpoint": "mail@myagent.com"
    }
  ],
  "x402Support": false,
  "active": true,
  "registrations": [
    {
      "agentId": 22,
      "agentRegistry": "{namespace}:{chainId}:{identityRegistry}"
    }
  ],
  "supportedTrust": ["reputation", "crypto-economic", "tee-attestation"]
}
```

The `type`, `name`, `description`, and `image` fields ensure compatibility with ERC-721 apps. The `services` list is fully customizable. The `supportedTrust` field is optional; if absent, the registration is used for discovery only.

## Community Calls & Content

### Recorded Sessions

- **[Trustless Agents Call #1 - September 23, 2025](https://youtu.be/kooO3DGzYek)** - First community call with demos and roadmap updates
- **[Community Call #1 Slides](https://docs.google.com/presentation/d/1DUAl2MxHw0J5jSr7Ap5eCCzNLMSbCQ3LcCZyFMNm3Y4/edit?usp=sharing)** - Presentation slides from September 23, 2025 call
- **[Trustless Agents Call #2](https://www.youtube.com/watch?v=J3PkdQEZWK0)** - Second community call recording

### Events & Conferences

- **[Trustless Agents Day - Devconnect](https://devconnect.org/calendar?event=trustlessagentsday)** - Full-day summit at Devconnect exploring Ethereum as coordination layer for AI economy (November 21, 2025)
- **[8004 Community Call #3](https://lu.ma/2kvxberc)** - Third community call (November 12, 2025)
- **[Builder Nights Denver](https://lu.ma/bndenver)** - In-person builder event in Denver (February 17, 2026)
- **[Agentic Brunch - ERC-8004](https://lu.ma/j57z0k64)** - Community brunch event (February 25, 2026)
- **[8004 Launch Day](https://lu.ma/658en7zs)** - Official mainnet launch event (March 17, 2026)

---

## Builder Projects

### Infrastructure & SDKs

**[DYOE — Know Your Agent](https://agents.dyoeway.org)**

The human-verified trust layer for the agent economy. Before an AI agent pays, DYOE runs the Know Your Agent check (`/transaction`, $0.25): counterparty + payee wallet (OFAC + on-chain footprint) + policy → **proceed / caution / stop**, with a signed, independently verifiable EIP-191 attestation. Automated tiers from $0.01; a **named human reviews and signs** the high-stakes calls at $25 — the human validation tier no algorithm provides. x402-native on Base, every verdict verifiable against a published authority. [Agent Card](https://agents.dyoeway.org/.well-known/agent-card.json) · [x402 manifest](https://agents.dyoeway.org/.well-known/x402.json).

**[agent-reputation-sdk](https://github.com/hanjoonchoe/agent-reputation-sdk)**

ERC-8004 extensions for each ecosystem's canonical Ethereum SDK — viem actions (TypeScript), a web3.py external module (Python), and an alloy provider trait (Rust): typed registry reads plus a policy-driven reputation calculator (Beta Reputation System, Jøsang & Ismail 2002). No built-in score by design — results are expectation ± uncertainty with witness statistics, caveats, and the echoed policy, and shared golden test vectors (raw Base mainnet snapshots) keep all three implementations numerically identical. `npm install agent-reputation` · `pip install web3-agent-reputation` · `cargo add alloy-agent-reputation`. MIT licensed.

**[Veylux](https://github.com/kenjimoto999/veylux)**

Sybil-resistant reputation reference implementation combining stake-weighted bonding with dual graph-structural signals (local conductance + SybilRank-style propagation). Adversarially tested against a bridge-attack construction and a whitewashing attack. Open, MIT-licensed, no token.

**[Kuberna Labs](https://github.com/kawacukennedy/kuberna-labs)**

Cross-chain intent execution SDK for ERC-8004 agents. Registered agents create and settle typed intents across NEAR, Base, and Mantle, with required/forbidden field enforcement per identity. Execution proofs are attested via zkTLS and TEE and attributed back to the agent's ERC-8004 identity, so cross-chain action trails link to the on-chain agent ID. MIT licensed.

**[OmniClaw](https://github.com/OmniClaw/OmniClaw)**

Python CLI + policy engine for agent payments. Combines ERC-8004 (trust gates), EIP-3009 (gasless USDC signing), and x402 (payment requests) behind a single authority layer, so agents never hold raw wallet keys. Multi-rail routing across Circle Gateway, x402 Exact, and a self-hosted facilitator. MIT, pip install omniclaw.

**[mcp8004](https://github.com/jordanlyall/mcp8004)**

- Drop-in MCP auth middleware using ERC-8004 onchain agent identity. Agents authenticate to MCP servers by signing a challenge with their wallet; the server verifies against the ERC-8004 Identity Registry on Base and issues a scoped JWT session token. Includes x402 payment fallback for unregistered agents. `npm install mcp8004`. MIT licensed.

**[UFX Agentic Commerce](https://github.com/ufosearchspace-create/ERC8183)**

- [ERC-8183 Hook & Reputation Middleware](https://github.com/ufosearchspace-create/ERC8183) - First `IACPHook` implementations and ERC-8004 reputation bridge for ERC-8183 (Agentic Commerce Protocol). Includes ReputationHook (auto-writes job outcomes to ReputationRegistry), ReputationGateHook (reputation-based funding gate), SLAHook (deadline enforcement), AI evaluators, and Python SDK. 208 Solidity tests (incl. 9 fuzz). Live on Base Mainnet with [Iamalive Agent #1734](https://basescan.org/address/0x3F41E8699D774Eb738967A6506B3A9E919aA1c8B). MIT licensed.

**[Automata Network](https://www.ata.network/)**

- [Automata DCAP Attestation](https://github.com/automata-network/automata-dcap-attestation) - Solidity library for onchain Intel SGX and TDX attestation verification, supporting RISC Zero and Succinct
- [Intel TDX Attestation SDK](https://github.com/automata-network/tdx-attestation-sdk) - SDK for generating Intel TDX quotes across cloud providers with ZK proof generation
- [AMD SEV-SNP Attestation SDK](https://github.com/automata-network/amd-sev-snp-attestation-sdk) - SDK for AMD SEV-SNP attestation reports with ZK proof support
- [AWS Nitro Enclave Attestation](https://github.com/automata-network/aws-nitro-enclave-attestation) - CLI for AWS Nitro Enclave attestation
- [Automata SGX SDK](https://github.com/automata-network/automata-sgx-sdk) - Rust-native SDK for Intel SGX secure enclave development

**[Praxis Protocol](https://twitter.com/Praxis_Protocol)**

- [Praxis Python SDK](https://github.com/prxs-ai/praxis-py-sdk)
- [Praxis Go SDK](https://github.com/prxs-ai/praxis-go-sdk)

**[Ch40s Chain](https://twitter.com/Ch40sChain)**

- [Reference Implementation for ERC-8004](https://github.com/ChaosChain/trustless-agents-erc-ri)
- [Chaos Chain SDK for building autonomous agents](https://docs.chaoscha.in/sdk/installation)
- [Genesis Studio - Commercial prototype for ERC8004](https://github.com/ChaosChain/chaoschain-genesis-studio)

**[Vistara Labs](https://x.com/vistaralabs)**

- [Vistara Agent Arena SDK](https://github.com/vistara-apps/agent-arena-v1)
- [ERC-8004 Example](https://github.com/vistara-apps/erc-8004-example)
- **[Verity Protocol](https://verity.tenpound.xyz)** — On-chain reliability scoring for ERC-8004 agents. Indexes `NewFeedback` events from the `ReputationRegistry`, computes Brier Skill Scores across Economic, Solver, and Governance verticals, submits reputation back via `giveFeedback` after each scoring cycle, and anchors every score as an EAS attestation on Base. SDK: [`@veritynpm/sdk`](https://www.npmjs.com/package/@veritynpm/sdk).

**[MainStreet Trust Oracle](https://avisradar.app/mainstreet.html)** — Reputation oracle for Base wallets and AI agents. Returns SAFE / CAUTION / BLOCK + 0-100 score + EIP-712 signed attestation in <100ms for any wallet, agent, or token deployer, callable by any agent before routing USDC. Folds ERC-8004 ReputationRegistry feedback into the score. Registered as ERC-8004 agentId 53953 on Base. Onchain verifier at `0x7397adb9713934c36d22aa54b4dbbcd70263592b` (Base), `requireMinScore()` callable from any contract for ~$0.00003 gas. Free 1000 reads/day, paid `/check` via x402 ($0.005 instant / $0.025 full) or pre-paid credit bundles. Indexed on CDP x402 Bazaar. MCP: `https://avisradar.app/mcp` (17 tools). npm: [`@raskhaaa/mainstreet-oracle`](https://www.npmjs.com/package/@raskhaaa/mainstreet-oracle). MIT.

**[Tenzro Network](https://tenzro.network)**

- [tenzro-network](https://github.com/tenzro/tenzro-network) - L1 with three ERC-8004 registries exposed as native EVM precompiles: `IDENTITY 0x101a`, `REPUTATION 0x101b`, `VALIDATION 0x101c`. Selectors (`registerAgent`, `submitFeedback`, `requestValidation`, `submitValidation`) are byte-identical to the Ethereum reference, so the same calldata targets either deployment.
- [tenzro-identity::erc8004 adapter](https://github.com/tenzro/tenzro-network/blob/main/crates/tenzro-identity/src/erc8004.rs) - Rust ABI encoders + client. Mirrors TDIP machine registrations (`did:tenzro:machine:*`) onto the Ethereum contracts; `agentId = keccak256(utf8(did_string))` computes identically on both sides.
- [Tenzro MCP + A2A](https://mcp.tenzro.network/mcp) - the three registries surfaced to MCP clients (Claude Desktop, Cursor) and A2A consumers without writing Solidity. Live on Tenzro testnet `https://rpc.tenzro.network` (chain id 1337). Apache-2.0.

**[NameWhisper](https://namewhisper.ai)**

- [namewhisper-mcp](https://github.com/eggybug42069/namewhisper-mcp) - ENS-native agent identity and intelligence over MCP: provision ENSIP-25 agent identities on ENS names, register agents in the ERC-8004 Identity Registry on Ethereum mainnet, check ERC-8004 reputation, and search the registered-agent directory — alongside ENS search, valuation, and Seaport trading tools (44 total). Remote streamable-http endpoint at `https://namewhisper.ai/mcp`, listed in the official MCP Registry as `ai.namewhisper/ens-tools`. AGPL-3.0.

### Collaboration Frameworks

**[AgentTalk](https://github.com/douglasborthwick-crypto/agenttalk)** — _Condition-gated sessions for agent-to-agent communication_

- [AgentTalk](https://github.com/douglasborthwick-crypto/agenttalk) - Wallet auth for A2A: before two agents exchange data, both verify their wallets satisfy the same on-chain conditions. Six condition types — token balances, NFT ownership, EAS attestations, Farcaster identity, and self-scaling amount/supply ratios (e.g. "hold ≥ 10× the amount you're about to pay") — up to 10 composable per channel. Supports bilateral (2 agents) and multi-party ("town hall") flows across 37 chains. Re-verify on demand ejects any agent whose wallet no longer meets the conditions mid-session. Sessions issued as ECDSA P-256 signed JWTs (`kid: insumer-attest-v1`), verifiable offline via [JWKS](https://insumermodel.com/.well-known/jwks.json).
- [Examples (JS/Python/Shell)](https://github.com/douglasborthwick-crypto/agenttalk/tree/main/examples) - Bilateral and multi-party session flows
- [Hosted API](https://skyemeta.com/agenttalk/) - 10 calls per wallet, no signup required

**[Cairn](https://github.com/echo-toolkit/cairn)** — _Append-only shared-state coordination layer for multi-agent systems, with ERC-8004 verifiable coordination receipts_

- [Cairn](https://github.com/echo-toolkit/cairn) - Open-source (AGPLv3) Python library where multiple agents coordinate through a passive append-only blackboard + minimal per-agent context instead of conversation — so agents stop silently overwriting each other's shared state (auditable, debuggable; ~half the tokens in a measured A/B). The shared-state / coordination layer A2A and MCP leave to you. Optional on-chain layer (live on Celo mainnet): ERC-8004 agent identity + verifiable coordination receipts (one per run) + agent payment. Framework-agnostic (LangChain/LangGraph/CrewAI adapters). `pip install cairn-coordination`.

### Commerce & Escrow

**[UFX Agentic Commerce](https://github.com/ufosearchspace-create/ERC8183)** — First `IACPHook` implementations and ERC-8004 reputation bridge for ERC-8183 (Agentic Commerce Protocol). The EIP defines hooks; we built and deployed them.

- [ReputationHook](https://github.com/ufosearchspace-create/ERC8183) - Auto-writes job outcomes to ERC-8004 ReputationRegistry after every completed/rejected job
- [ReputationGateHook](https://github.com/ufosearchspace-create/ERC8183) - Gates provider funding by ERC-8004 reputation score and job history
- [SLAHook](https://github.com/ufosearchspace-create/ERC8183) - Enforces submission deadlines after funding
- [WebScrapingEvaluator + AI Evaluator](https://github.com/ufosearchspace-create/ERC8183) - On-chain attestation for deliverables
- [Python SDK](https://github.com/ufosearchspace-create/ERC8183) - Async client for contract interaction
- 208 Solidity tests (incl. 9 fuzz). 5 verified contracts on Base Mainnet. [Iamalive Agent #1734](https://basescan.org/address/0x3F41E8699D774Eb738967A6506B3A9E919aA1c8B). MIT licensed.

**[Azeth](https://azeth.ai)**

Trust infrastructure for the machine economy. TypeScript SDK suite providing ERC-8004 identity registration, weighted reputation with Sybil-resistant opinions, capability-based service discovery, and x402 payment settlement with automatic reputation feedback. Agents get non-custodial ERC-4337 smart accounts with guardian-enforced guardrails. Deployed on Base Sepolia and Ethereum Sepolia with deterministic CREATE2 addresses.

- [Azeth SDK (`@azeth/sdk`)](https://www.npmjs.com/package/@azeth/sdk) - Smart account creation, ERC-8004 registry operations, x402 payments, and XMTP messaging
- [Azeth MCP Server (`@azeth/mcp-server`)](https://www.npmjs.com/package/@azeth/mcp-server) - MCP tools for AI agents to create accounts, discover services, pay, and submit reputation
- [Azeth Provider (`@azeth/provider`)](https://www.npmjs.com/package/@azeth/provider) - x402 service provider middleware for Hono with on-chain USDC settlement
- [Azeth CLI (`@azeth/cli`)](https://www.npmjs.com/package/@azeth/cli) - Command-line interface for registry and payment operations
- [Azeth Common (`@azeth/common`)](https://www.npmjs.com/package/@azeth/common) - Shared types, ABIs, and contract addresses

**[AgentLux](https://agentlux.ai)**

Identity, marketplace, and services platform for AI agents on Base L2. Production ERC-8004 Identity Registry deployment with behavioral KYA verification, x402 micropayments, agent-to-agent services with escrow, and 32+ MCP tools.

- [AgentLux Github](https://github.com/agentlux/erc-8004)
- [ERC-8004 Identity Registry (Base Mainnet)](https://basescan.org/address/0x08591b838Bd745AFBafE27c254676A3C6Fafb159) - On-chain agent identity with behavioral KYA attestations
- [MCP Server](https://agentlux.ai) - 32+ tools for agent identity, marketplace, av

... [OUTPUT TRUNCATED - 35968 chars omitted out of 85968 total] ...

)** - Client-side identity verification dApp (ethers.js, no backend): register an agent, look up any address against the Identity and Reputation registries, sign a message, and verify a signature. Live on Celo mainnet, bilingual FR/EN

## Research & Papers

_Academic papers and research related to ERC-8004 and trustless agents._

### Agent Identity & Trust

- **[AI Agents with Decentralized Identifiers and Verifiable Credentials](https://arxiv.org/abs/2511.02841)** (Nov 2025) - Proposes equipping each AI agent with a self-controlled DID and Verifiable Credentials for trust establishment in agent-to-agent dialogue. Directly addresses the identity bootstrapping problem that ERC-8004's Identity Registry tackles on-chain.

- **[A Novel Zero-Trust Identity Framework for Agentic AI](https://arxiv.org/abs/2505.19301)** (May 2025) - Argues that traditional IAM is fundamentally inadequate for AI agents and proposes rich, verifiable Agent Identities using DIDs and VCs that encode capabilities, provenance, behavioral scope, and security posture.

- **[Binding Agent ID: Unleashing the Power of AI Agents with Identity](https://arxiv.org/abs/2512.17538)** (Dec 2025) - Explores binding unique identifiers to agentic AI instances for runtime attribution and accountability. Relevant to ERC-8004's on-chain identity binding model.

- **[Trusted AI Agents in the Cloud](https://arxiv.org/abs/2512.05951)** (Dec 2025) - Establishes that cross-principal trust requires compositional, verifiable identity reflecting the code, model, and dependencies involved in each invocation. Complements ERC-8004's validation registry approach.

### Security & Governance

- **[A Survey of Agentic AI and Cybersecurity](https://arxiv.org/abs/2601.05293)** (Jan 2026) - Comprehensive survey covering BlockA2A (securing A2A communication using decentralized identity and blockchain-anchored audit logs), agent hijacking, and supply chain attacks. Essential context for why ERC-8004's trust layer matters.

- **[Sovereign Agents](https://arxiv.org/abs/2602.14951)** (Feb 2026) - Introduces "agentic sovereignty" — the capacity of an agent to persist, act, and control resources with non-overrideability inherited from infrastructure. Analyzes TEEs, DePIN, and agent key continuity protocols. Raises the accountability question for agents that become non-terminable.

- **[Practices for Governing Agentic AI Systems](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf)** (OpenAI) - Framework for governing autonomous AI systems, addressing delegation chains, oversight mechanisms, and accountability structures.

### Policy & Frameworks

- **[Model AI Governance Framework for Agentic AI](https://www.imda.gov.sg/-/media/imda/files/about/emerging-tech-and-research/artificial-intelligence/mgf-for-agentic-ai.pdf)** (Singapore IMDA, Jan 2026) - World's first government governance framework specifically for autonomous AI agents. Four dimensions: bounding risks, human accountability, technical controls, end-user responsibility.

- **[NIST AI Agent Standards Initiative](https://www.nist.gov/caisi/ai-agent-standards-initiative)** (Feb 2026) - U.S. federal initiative for interoperable and secure AI agent standards, including [RFI on AI Agent Security](https://www.federalregister.gov/documents/2026/01/08/2026-00206/request-for-information-regarding-security-considerations-for-artificial-intelligence-agents) and [NCCoE Concept Paper on Agent Identity and Authorization](https://www.nccoe.nist.gov/projects/software-and-ai-agent-identity-and-authorization).

### Industry Reports

- **[Securing Autonomous AI Agents](https://www.strata.io/blog/agentic-identity/the-ai-agent-identity-crisis-new-research-reveals-a-governance-gap/)** (Strata Identity & Cloud Security Alliance, Feb 2026) - Survey finding only 23% of organizations have formal agent identity management strategies, 45.6% still use shared API keys for agent authentication, and only 21.9% treat agents as independent identity-bearing entities.


## Development Resources

### Getting Started

1. [EIP-8004 Specification](https://eips.ethereum.org/EIPS/eip-8004)
2. [ERC-8004 Contracts Repository](https://github.com/erc-8004/erc-8004-contracts)
3. [Best Practices Guide](https://github.com/erc-8004/best-practices)
4. [Telegram Community](http://t.me/ERC8004)

### Contract Deployments

**Official Implementation:** [erc-8004/erc-8004-contracts](https://github.com/erc-8004/erc-8004-contracts)

The contracts are deployed as per-chain singletons. The Identity Registry uses vanity address `0x8004A169...` on mainnets and `0x8004A818...` on testnets. Complete deployment addresses for all networks are maintained in the [contracts repository](https://github.com/erc-8004/erc-8004-contracts).

**Security Audits:** The contracts have been audited by [Cyfrin](https://cyfrin.io/), [Nethermind](https://www.nethermind.io/), and the Ethereum Foundation Security Team.

#### Mainnet Deployments

| Network   | Identity Registry                                                                                       | Reputation Registry                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Ethereum  | [0x8004A169...432](https://etherscan.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)             | [0x8004BAa1...b63](https://etherscan.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)             |
| Base      | [0x8004A169...432](https://basescan.org/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)             | [0x8004BAa1...b63](https://basescan.org/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)             |
| Arbitrum  | [0x8004A169...432](https://arbiscan.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)              | [0x8004BAa1...b63](https://arbiscan.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)              |
| Optimism  | [0x8004A169...432](https://explorer.optimism.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)     | [0x8004BAa1...b63](https://explorer.optimism.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)     |
| Polygon   | [0x8004A169...432](https://polygonscan.com/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)          | [0x8004BAa1...b63](https://polygonscan.com/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)          |
| Linea     | [0x8004A169...432](https://lineascan.build/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)          | [0x8004BAa1...b63](https://lineascan.build/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)          |
| Scroll    | [0x8004A169...432](https://scrollscan.com/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)           | [0x8004BAa1...b63](https://scrollscan.com/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)           |
| Avalanche | [0x8004A169...432](https://snowtrace.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)             | [0x8004BAa1...b63](https://snowtrace.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)             |
| BNB Chain | [0x8004A169...432](https://bscscan.com/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)              | [0x8004BAa1...b63](https://bscscan.com/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)              |
| Celo      | [0x8004A169...432](https://celoscan.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)              | [0x8004BAa1...b63](https://celoscan.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)              |
| Gnosis    | [0x8004A169...432](https://gnosisscan.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)            | [0x8004BAa1...b63](https://gnosisscan.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)            |
| Monad     | [0x8004A169...432](https://monadscan.com/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)            | [0x8004BAa1...b63](https://monadscan.com/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)            |
| Abstract  | [0x8004A169...432](https://explorer.mainnet.abs.xyz/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432) | [0x8004BAa1...b63](https://explorer.mainnet.abs.xyz/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63) |
| Mantle    | [0x8004A169...432](https://mantlescan.xyz/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)           | [0x8004BAa1...b63](https://mantlescan.xyz/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)           |
| Soneium   | [0x8004A169...432](https://soneium.blockscout.com/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)   | [0x8004BAa1...b63](https://soneium.blockscout.com/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)   |
| Taiko     | [0x8004A169...432](https://taikoscan.io/address/0x8004A169FB4a3325136EB29fA0ceB6D2e539a432)             | [0x8004BAa1...b63](https://taikoscan.io/address/0x8004BAa17C55a88189AE136b182e5fdA19dE9b63)             |

See the [contracts repository](https://github.com/erc-8004/erc-8004-contracts) for the full list including SKALE, GOAT Network, MegaETH, Metis, XLayer, and all testnet addresses (Hedera, Arc).

### SDKs and Libraries

#### JavaScript/TypeScript

- **[Agent0 SDK](https://sdk.ag0.xyz/)** - TypeScript and Python SDK with subgraph queries and an interactive playground; developed by Agent0 Lab
- **[create-8004-agent](https://www.npmjs.com/package/create-8004-agent)** - CLI scaffolding package (`npx create-8004-agent`) for bootstrapping ERC-8004 agents
- **[Lucid Agents / Daydreams](https://docs.daydreams.systems/)** - Agent framework with built-in ERC-8004 integration
- **[ChaosChain SDK](https://github.com/ChaosChain/chaoschain/tree/main/packages/sdk)** - Full-featured JavaScript/TypeScript SDK
- **[erc-8004-js](https://github.com/tetratorus/erc-8004-js)** - Lightweight JavaScript library
- **[Azeth SDK (`@azeth/sdk`)](https://www.npmjs.com/package/@azeth/sdk)** - Full-stack TypeScript SDK for ERC-8004 identity, reputation, discovery, and x402 payments

#### Python

- **[Agent0 SDK](https://sdk.ag0.xyz/)** - Python support included alongside TypeScript
- **[erc-8004-py](https://github.com/tetratorus/erc-8004-py)** - Python implementation
- **[chaoschain-sdk](https://pypi.org/project/chaoschain-sdk/)** - Available on PyPI
- **[agentwallet-sdk](https://www.npmjs.com/package/agentwallet-sdk)** - Non-custodial TypeScript SDK for AI agents: ERC-8004 identity, x402 payments, CCTP cross-chain transfers, Uniswap V3 swaps. First ERC-8004 implementation on npm with 158 tests.
- **[trc8004-m2m](https://github.com/M2M-TRC8004-Registry/trc8004-m2m-sdk)** - TRC-8004 Python SDK for TRON (async, Pydantic models)

### Infrastructure & Data

- **[Agent0 Subgraph](https://github.com/agent0lab/subgraph)** - Multi-chain GraphQL subgraph indexing ERC-8004 registries
- **[OASF (Open Agent Specification Format)](https://github.com/agntcy/oasf)** - Skill and capability taxonomy for AI agents; used alongside ERC-8004 agent cards
- **[PayAI](https://payai.network/)** - x402 payment facilitator enabling per-request micropayments for agents on Base and Polygon
- **[Registry Brokers by HashgraphDAO](https://registry.hashgraphonline.com/)** - Cross-network agent discovery bridging Hedera and EVM registries

---

## Smart Contract Interfaces

### Identity Registry (ERC-721 Compatible)

Agents are identified globally by:

- `agentRegistry`: `{namespace}:{chainId}:{identityRegistry}` (e.g., `eip155:1:0x8004A169FB4a3325136EB29fA0ceB6D2e539a432`)
- `agentId`: the ERC-721 `tokenId` assigned incrementally by the registry

```solidity
// Register a new agent (three overloads)
function register(string agentURI, MetadataEntry[] calldata metadata) external returns (uint256 agentId)
function register(string agentURI) external returns (uint256 agentId)
function register() external returns (uint256 agentId)

// Update agent URI
function setAgentURI(uint256 agentId, string calldata newURI) external

// Optional on-chain metadata
function getMetadata(uint256 agentId, string memory metadataKey) external view returns (bytes memory)
function setMetadata(uint256 agentId, string memory metadataKey, bytes memory metadataValue) external

// Agent wallet (reserved metadata key, requires EIP-712 or ERC-1271 proof)
function setAgentWallet(uint256 agentId, address newWallet, uint256 deadline, bytes calldata signature) external
function getAgentWallet(uint256 agentId) external view returns (address)
function unsetAgentWallet(uint256 agentId) external
```

### Reputation Registry

Feedback is stored as a signed fixed-point value (`int128` + `uint8` decimals), enabling a wide range of metrics (quality scores, uptime percentages, response times, revenues, etc.).

```solidity
// Submit feedback for an agent (caller must not be owner or operator of agentId)
function giveFeedback(
    uint256 agentId,
    int128 value,
    uint8 valueDecimals,
    string calldata tag1,
    string calldata tag2,
    string calldata endpoint,
    string calldata feedbackURI,
    bytes32 feedbackHash
) external

// Revoke previously given feedback
function revokeFeedback(uint256 agentId, uint64 feedbackIndex) external

// Append a response to received feedback (anyone may call)
function appendResponse(
    uint256 agentId,
    address clientAddress,
    uint64 feedbackIndex,
    string calldata responseURI,
    bytes32 responseHash
) external

// Read a specific feedback entry
function readFeedback(
    uint256 agentId,
    address clientAddress,
    uint64 feedbackIndex
) external view returns (int128 value, uint8 valueDecimals, string memory tag1, string memory tag2, bool isRevoked)

// Read all feedback for an agent
function readAllFeedback(
    uint256 agentId,
    address[] calldata clientAddresses,
    string calldata tag1,
    string calldata tag2,
    bool includeRevoked
) external view returns (
    address[] memory clients,
    uint64[] memory feedbackIndexes,
    int128[] memory values,
    uint8[] memory valueDecimals,
    string[] memory tag1s,
    string[] memory tag2s,
    bool[] memory revokedStatuses
)

// Count responses appended to a feedback entry
function getResponseCount(
    uint256 agentId,
    address clientAddress,
    uint64 feedbackIndex,
    address[] calldata responders
) external view returns (uint64 count)

// Aggregated summary
function getSummary(
    uint256 agentId,
    address[] calldata clientAddresses,
    string calldata tag1,
    string calldata tag2
) external view returns (uint64 count, int128 summaryValue, uint8 summaryValueDecimals)

// Enumerate clients and feedback indexes
function getClients(uint256 agentId) external view returns (address[] memory)
function getLastIndex(uint256 agentId, address clientAddress) external view returns (uint64)
```

### Validation Registry

```solidity
// Request validation (must be called by the owner or operator of agentId)
function validationRequest(
    address validatorAddress,
    uint256 agentId,
    string calldata requestURI,
    bytes32 requestHash
) external

// Provide validation response (must be called by the validatorAddress from the request)
function validationResponse(
    bytes32 requestHash,
    uint8 response,
    string calldata responseURI,
    bytes32 responseHash,
    string calldata tag
) external

// Query a specific validation record
function getValidationStatus(
    bytes32 requestHash
) external view returns (
    address validatorAddress,
    uint256 agentId,
    uint8 response,
    bytes32 responseHash,
    string memory tag,
    uint256 lastUpdate
)

// Aggregated validation statistics (agentId mandatory; validatorAddresses and tag are optional filters)
function getSummary(
    uint256 agentId,
    address[] calldata validatorAddresses,
    string calldata tag
) external view returns (uint64 count, uint8 averageResponse)

// List all validation request hashes for an agent or validator
function getAgentValidations(uint256 agentId) external view returns (bytes32[] memory requestHashes)
function getValidatorRequests(address validatorAddress) external view returns (bytes32[] memory requestHashes)
```

---

## Standards & References

### Core Standards

- **[CAIP-10](https://github.com/ChainAgnostic/CAIPs/blob/main/CAIPs/caip-10.md)** - Chain Agnostic Improvement Proposal for account identification
- **[RFC 8615](https://www.rfc-editor.org/rfc/rfc8615)** - Well-Known URIs specification
- **[RFC 7071](https://datatracker.ietf.org/doc/html/rfc7071)** - A Media Type for Reputation Interchange (Reputons)
- **[ERC-721](https://eips.ethereum.org/EIPS/eip-721)** - Non-Fungible Token Standard (base for Identity Registry)

### Related Services

- **[EAS (Ethereum Attestation Service)](https://attest.org/)** - Referenced for on-chain attestations

## Related Standards

### Ethereum Ecosystem

- **[ERC-8001](https://github.com/ethereum/ERCs/issues/XXX)** - Agent-to-Agent coordination (mentioned in discussions)
- **[EAS](https://attest.org/)** - Ethereum Attestation Service for on-chain attestations


### Cross-Chain and Alternative Implementations

**[Hashgraph Online (HOL)](https://hol.org)** — _Trust engine for the agentic internet_

Universal agentic registry built on Hedera Hashgraph. Provides blockchain-based identity for AI agents using ERC-8004 standard and HCS-14 Universal Agent IDs (UAIDs). Enables agent discovery, verification, and autonomous commerce via x402 protocol.

- [Website](https://hol.org) | [Registry](https://hol.org/registry) | [GitHub](https://github.com/hashgraph-online) | [SDK](https://www.npmjs.com/package/@hol-org/standards-sdk)

**TRON Implementation:** [M2M-TRC8004-Registry](https://github.com/M2M-TRC8004-Registry)

The TRC-8004 implementation on TRON is deployed on both mainnet and Shasta testnet with four registries (Identity, Reputation, Validation, Incident). See [m2mregistry.io](https://m2mregistry.io) for details.


### External Protocols

- **[A2A Protocol](https://a2a-protocol.org/)** - Agent-to-Agent Protocol that ERC-8004 extends
- **[x402 Payment Standard](https://www.x402.org/)** - Referenced for potential payment integration

## FAQ

<details>
<summary><strong>What is ERC-8004 and how does it relate to the A2A Protocol?</strong></summary>

ERC-8004 extends the Agent-to-Agent (A2A) Protocol with a **trust layer** that allows participants to discover, choose, and interact with agents across organizational boundaries without pre-existing trust. It introduces three lightweight, on-chain registries: Identity, Reputation, and Validation, while leaving application-specific logic to off-chain components.

</details>

<details>
<summary><strong>What are the three core components of ERC-8004?</strong></summary>

The three registries are:

1. **Identity Registry** - Minimal on-chain handle that resolves to an agent's off-chain AgentCard
2. **Reputation Registry** - Standard interface for posting and fetching attestations
3. **Validation Registry** - Generic hooks for requesting and recording independent checks
</details>

<details>
<summary><strong>What trust models does ERC-8004 support?</strong></summary>

ERC-8004 supports three pluggable trust models:

- **Reputation-based systems** using client feedback
- **Stake-secured inference validation** (crypto-economics)
- **TEE attestations** for agents running in Trusted Execution Environments (crypto-verifiability)
</details>

### Specification Status

<details>
<summary><strong>What is the current status of the ERC-8004 specification?</strong></summary>

ERC-8004 is currently in **Draft** status in the EIP process. The final audited contracts for Identity and Reputation registries are deployed on Ethereum mainnet and 20+ networks. The Validation Registry is under active revision with the TEE community.

</details>

<details>
<summary><strong>What does ERC-8004 v1 include?</strong></summary>

The current specification includes:

- Complete smart contract interfaces for all three registries
- ERC-721 compatible Identity Registry with metadata support
- Comprehensive feedback system using signed fixed-point values (`int128` + `uint8` decimals) and off-chain metadata
- Validation framework supporting crypto-economic and crypto-verification models
- Full compatibility with A2A Protocol and MCP endpoints
- Deployment-ready smart contract specifications
</details>

### Technical Implementation

<details>
<summary><strong>Why does ERC-8004 prioritize off-chain data storage over on-chain?</strong></summary>

The protocol deliberately keeps complex data off-chain for several reasons:

- **Gas efficiency** - Avoids requiring agents to sign transactions for each feedback
- **Scalability** - Enables sophisticated reputation algorithms and aggregation services
- **Flexibility** - Allows for custom validation protocols with their own incentive mechanisms
- **Aggregation focus** - Single feedback/validation entries are rarely used alone; they're typically aggregated
</details>

<details>
<summary><strong>Should validation and reputation data be stored on-chain for smart contract composability?</strong></summary>

This is an active debate in the community. Arguments for on-chain storage include:

- Enabling smart contracts to read validation responses and condition logic on them
- Decoupling validation from enforcement (validators focus on validation, other protocols handle slashing)
- Supporting permissionless innovation by other developers

The current specification keeps data off-chain but emits events, though some suggest making on-chain storage optional.

</details>

<details>
<summary><strong>How does domain validation work in the Identity Registry?</strong></summary>

Currently, the ERC doesn't specify how to verify that an agent actually owns the domain they claim. This verification is left to users of the protocol. Future versions might include:

- Trusted party verification
- Consensus/verification mechanisms (e.g., zkTLS proofs)
- Allowing multiple agents to claim the same domain with disambiguation
</details>

<details>
<summary><strong>Why does ERC-8004 require agents to use domains instead of URLs?</strong></summary>

The current specification requires each agent to have its own domain/subdomain with AgentCard at the well-known location `/.well-known/agent-card.json`. This is stricter than the A2A spec, which allows URLs. Some community members suggest using URLs instead to allow multiple agents per domain.

</details>

### Reputation and Trust

<details>
<summary><strong>Should reputation be a single aggregate score or modular?</strong></summary>

The community strongly favors **modular approaches**:

- **Against single scores**: Creates monopolistic behavior and oversimplifies trust relationships
- **For modularity**: Trust is context-dependent and varies between agent pairs
- **Preferred approach**: Index and reference multiple reputation systems, allowing agents to choose relevant metrics
</details>

<details>
<summary><strong>How should reputation providers work together?</strong></summary>

Community suggestions include:

- Multiple providers (e.g., Virtuals, Creatorbid, Base) offering scores for agents
- (Agent, Provider) pairs in the registry for on-chain applications
- Reducing bias and collusion risk through multiple score sources
- Individual attestation history remaining standalone
</details>

<details>
<summary><strong>Is trust universal between agents?</strong></summary>

**No.** Trust is not a universal value but a **vector** from one agent to another. Alice's trust for Bob will differ from Charlie's trust for Bob, and Alice's trust varies by context/domain of interaction. This reinforces the need for modular, context-aware reputation systems.

</details>

### Payment and Economics

<details>
<summary><strong>How does ERC-8004 handle payments between agents?</strong></summary>

ERC-8004 deliberately **doesn't cover payments** to remain unopinionated and avoid coupling trust/discovery with specific payment protocols. However:

- Payment proofs can be included as optional attributes in off-chain schemas
- The team is collaborating with groups working on A2A payment extensions based on x402
- Payment references should be lightweight hooks in Reputation records for correlation
</details>

<details>
<summary><strong>What payment mechanisms are envisioned?</strong></summary>

While payments are orthogonal to ERC-8004, the specification provides examples showing how x402 payment proofs can enrich feedback signals:

```json
{
  "proof_of_payment": {
    "fromAddress": "0x00...",
    "toAddress": "0x00...",
    "chainId": "1",
    "txHash": "0x00..."
  }
}
```

Other potential mechanisms include:

- Time locks and predetermined arbitration
- Staking by buyer or seller
- Escrow systems with crypto-economic guarantees
- Integration with A2A payment extensions based on x402
</details>

<details>
<summary><strong>Should there be incentives for providing feedback or guaranteeing data availability?</strong></summary>

This is mentioned as a possible future direction, including:

- Incentives to provide feedback
- Guarantees for off-chain data availability of feedback and validations
- Crypto-economic mechanisms for validator honesty
</details>

### Validation and Verification

<details>
<summary><strong>How do the two validation scenarios work?</strong></summary>

- **Crypto-economic scenario**: DataHash commits to job re-execution info; AgentValidator can be trusted agents, committees, or stake-secured services
- **Crypto-verification scenario**: DataHash commits to TEE attestation/zkTLS proof info; AgentValidator is a verifier smart contract checking proofs on-chain
</details>

<details>
<summary><strong>What's the relationship between ERC-8004 and other agent standards?</strong></summary>

- **ERC-8001**: Focuses on agent-to-agent coordination and consensus (orthogonal to ERC-8004)
- **EAS**: Referenced for on-chain attestations
- **RFC 7071 (Reputons)**: Standard for reputation interchange, relevant for reputation systems
</details>

### Implementation and Development

<details>
<summary><strong>Will there be a single registry per chain or multiple registries?</strong></summary>

The goal is to have **one singleton Identity Registry per chain** to prevent proliferation of slightly different registries.

</details>

<details>
<summary><strong>Should registration be free or require deposits?</strong></summary>

This implementation detail isn't specified in the current ERC but is under discussion for future versions.

</details>

<details>
<summary><strong>How detailed are the smart contract interfaces?</strong></summary>

The current ERC provides function names and parameters but lacks detailed Solidity interfaces. Future versions will include more precise type specifications and complete interface definitions.

</details>

<details>
<summary><strong>What about cross-chain support?</strong></summary>

Cross-chain identifiers are mentioned as a possible future direction, along with:

- NFT interfaces for agent minting, ownership, and transfer
- ENS support
- Integrations with A2A payment extensions
</details>

### Integration and Ecosystem

<details>
<summary><strong>How does ERC-8004 integrate with existing projects?</strong></summary>

Several projects are already building compatible systems:

- **Ensemble Framework**: Building trustless layer for agent collaboration
- **CoopHive Alkahest**: Smart contracts for peer-to-peer escrowed exchange
- Various reputation and validation service providers
</details>

<details>
<summary><strong>What standards does ERC-8004 build upon?</strong></summary>

Key standards include:

- **CAIP-10**: Chain-agnostic account identification
- **RFC 8615**: Well-Known URIs specification
- **A2A Protocol**: Base agent-to-agent communication
- **EAS**: Ethereum Attestation Service patterns
</details>

## Contributing

We welcome contributions to this awesome list!

### What to Contribute

- Implementations of ERC-8004
- Tools and libraries for developers
- Documentation and tutorials
- Research papers and academic work
- Community projects using ERC-8004
- Discussion summaries and insights

### How to Contribute

1. Check the [issues](https://github.com/sudeepb02/awesome-erc8004/issues) for ongoing discussions
2. Fork this repository
3. Add your resource to the appropriate section
4. Submit a pull request with a clear description
5. Follow the [Awesome List Guidelines](https://github.com/sindresorhus/awesome/blob/main/contributing.md)

**See [Contributing Guidelines](CONTRIBUTING.md) for detailed instructions.**

---

## Acknowledgments

### Core Authors & Contributors

- **Marco De Rossi** [@marco_derossi](https://x.com/marco_derossi) (MetaMask)
- **Davide Crapis** [@dcrapis](https://x.com/DavideCrapis) (Ethereum Foundation)
- **Jordan Ellis** (Google)
- **Erik Reppel** (Coinbase)

### Contributing Organizations

- **Ethereum Foundation's dAI team** - Core protocol development and research
- **Consensys** - Implementation and ecosystem development
- **Builder Community** - Active development and technical feedback

### 🌟 Community

And to all the community members providing feedback and technical contributions to the ecosystem.

---

<div align="center">

## 📄 License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related or neighboring rights to this work.

---

<p><em>Made with ❤️ by the ERC-8004 community</em></p>

</div>

## Security & Auditing Tools

- **[MASSAT Framework](https://github.com/craigmbrown/massat-framework)** - Open-source security audit toolkit for multi-agent AI systems with ERC-8004 passport verification. Covers OWASP ASI01-ASI10 threat categories. Validates agent identity, delegation chains, and trust tiers. Free tier + hosted API by [BlindOracle](https://craigmbrown.com/blindoracle/).
- **[Subcento](https://github.com/septagos/subcento)** - Pre-verification API for x402 agent payments: signed SAFE/CAUTION/BLOCK verdicts on the transaction itself before execution (Base, fail-closed, MIT). A per-payment trust signal that composes with ERC-8004 identity records.
