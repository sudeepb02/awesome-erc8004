<div align="center">
  <img src="./assets/logo.png" alt="ERC-8004 Logo" width="300"/>
  
  # Awesome ERC-8004
</div>

> A curated list of awesome resources for ERC-8004: Trustless Agents

ERC-8004 is an Ethereum standard that extends the Agent-to-Agent (A2A) Protocol with a trust layer, enabling participants to discover, choose, and interact with agents across organizational boundaries without pre-existing trust.

## Contents

- [Official Resources](#official-resources)
- [Specification](#specification)
- [Documentation & Guides](#documentation--guides)
- [Community Projects](#community-projects)
- [Research & Papers](#research--papers)
- [Discussions & Forums](#discussions--forums)
- [Development Resources](#development-resources)
- [Related Standards](#related-standards)
- [FAQ](#faq)
- [Contributing](#contributing)

## Official Resources

- [ERC-8004 Official Website](http://8004.org) - Official website for ERC-8004: Trustless Agents
- [EIP-8004 Specification](https://eips.ethereum.org/EIPS/eip-8004) - Official Ethereum Improvement Proposal
- [A2A Protocol Specification](https://a2a-protocol.org/latest/specification/) - Agent-to-Agent Protocol that ERC-8004 extends

## Specification

### Core Components

ERC-8004 introduces three lightweight, on-chain registries:

1. **Identity Registry** - Minimal on-chain handle that resolves to an agent's off-chain AgentCard
2. **Reputation Registry** - Standard interface for posting and fetching attestations
3. **Validation Registry** - Generic hooks for requesting and recording independent checks

### Trust Models

- **Reputation-based systems** - Using client feedback
- **Stake-secured inference validation** - Crypto-economics approach
- **TEE attestations** - Crypto-verifiability for agents running in Trusted Execution Environments

### Key Features

- Cross-organizational agent discovery
- Portable, censorship-resistant agent identifiers
- Pluggable and tiered trust models
- Security proportional to value at risk
- Off-chain data storage with on-chain integrity

## Documentation & Guides

### Community Calls & Recordings

- [Trustless Agents Call #1 - September 23, 2025](https://youtu.be/kooO3DGzYek) - Recording of the first community call with demos and roadmap updates
- [Community Call #1 Slides](https://docs.google.com/presentation/d/1DUAl2MxHw0J5jSr7Ap5eCCzNLMSbCQ3LcCZyFMNm3Y4/edit?usp=sharing) - Presentation slides from September 23, 2025 call

### Active Builder Projects

_Projects actively building with ERC-8004_

- [Praxis Protocol](https://twitter.com/Praxis_Protocol) - Showcased ERC-8004 implementation at Trustless Agents Call #1
  - [Praxis Python SDK](https://github.com/prxs-ai/praxis-py-sdk)
  - [Praxis Go SDK](https://github.com/prxs-ai/praxis-go-sdk)
- [Ensemble Framework](https://x.com/EnsembleCodes) - Building a trustless agent collaboration layer
  - [Ensemble Docs](https://docs.ensemble.codes)
- [ISEK](https://x.com/ISEK_Official) - Building autonomous collaborative agents 
  - [ISEK Source](https://github.com/isekOS/ISEK)
- [Ch40s Chain](https://twitter.com/Ch40sChain) - Demonstrated ERC-8004 integration at community call
  - [Reference Implementation for ERC-8004](https://github.com/ChaosChain/trustless-agents-erc-ri)
  - [Chaos Chain SDK for building autonomous agents](https://docs.chaoscha.in/sdk/installation)
- [Phala Network](https://twitter.com/PhalaNetwork) - Presented trustless agent implementation using ERC-8004
  - [Deploy ERC-8004 Agent in a TEE](https://github.com/Dstack-TEE/dstack)
  - [TEE based ERC-8004 implementation](https://github.com/HashWarlock/erc-8004-ex-phala/)
- [Cotten IO (Scypted)](https://twitter.com/CottenIO) - Showcased ERC-8004 project at community call
- [Sparsity](https://twitter.com/sparsity_xyz) - Active contributor presenting ERC-8004 work, presented verifiable agents during community call
  - [ERC-8004 AI agent demo](https://github.com/sparsity-xyz/sparsity-demo)
- [Vistara Labs](https://x.com/vistaralabs) - Active development on ERC-8004 infrastructure for the agent economy
  - [Vistara Agent Arena SDK](https://github.com/vistara-apps/agent-arena-v1)

## Research & Papers

_Academic papers and research related to trustless agents and ERC-8004_

## Discussions & Forums

### Official Discussions

- [Ethereum Magicians Discussion](https://ethereum-magicians.org/t/erc-8004-trustless-agents/25098) - Official discussion thread for ERC-8004
- [GitHub Issues](https://github.com/ethereum/ERCs/pull/1170) - Technical discussions and feedback on the specification

### Community Groups

- [ERC-8004 Telegram Group](http://t.me/ERC8004) - Official builder community and discussion group

## Development Resources

### Builder Programs & Community

- [ERC-8004 Builder Program](http://bit.ly/8004builderprogram) - Official builder program application for developers working on ERC-8004 implementations

### Standards & References

- [CAIP-10](https://github.com/ChainAgnostic/CAIPs/blob/main/CAIPs/caip-10.md) - Chain Agnostic Improvement Proposal for account identification
- [RFC 8615](https://www.rfc-editor.org/rfc/rfc8615) - Well-Known URIs specification
- [RFC 7071](https://datatracker.ietf.org/doc/html/rfc7071) - A Media Type for Reputation Interchange (Reputons)
- [EAS (Ethereum Attestation Service)](https://attest.org/) - Referenced for on-chain attestations

### Integration Examples

_Code examples and integration patterns will be added here_

## Related Standards

### Ethereum Standards

- [ERC-8001](https://github.com/ethereum/ERCs/issues/XXX) - Agent-to-Agent coordination (mentioned in discussions)
- [EAS](https://attest.org/) - Ethereum Attestation Service for on-chain attestations

### External Standards

- [A2A Protocol](https://a2a-protocol.org/) - Agent-to-Agent Protocol that ERC-8004 extends
- [x402 Payment Standard](https://www.x402.org/) - Referenced for potential payment integration

## FAQ

### General Questions

**Q: What is ERC-8004 and how does it relate to the A2A Protocol?**
A: ERC-8004 extends the Agent-to-Agent (A2A) Protocol with a trust layer that allows participants to discover, choose, and interact with agents across organizational boundaries without pre-existing trust. It introduces three lightweight, on-chain registries—Identity, Reputation, and Validation—while leaving application-specific logic to off-chain components.

**Q: What are the three core components of ERC-8004?**
A: The three registries are:

1. **Identity Registry** - Minimal on-chain handle that resolves to an agent's off-chain AgentCard
2. **Reputation Registry** - Standard interface for posting and fetching attestations
3. **Validation Registry** - Generic hooks for requesting and recording independent checks

**Q: What trust models does ERC-8004 support?**
A: ERC-8004 supports three pluggable trust models:

- **Reputation-based systems** using client feedback
- **Stake-secured inference validation** (crypto-economics)
- **TEE attestations** for agents running in Trusted Execution Environments (crypto-verifiability)

### Specification Status

**Q: What is the current status of the ERC-8004 specification?**
A: ERC-8004 is actively under development with a stable version (v2.0) planned for release on October 3, 2025. This will be followed by a reference implementation on October 10, 2025. The specification has strong community support with 200+ builders and active development from multiple teams.

**Q: When will the stable version be available?**
A: The stable ERC-8004 Spec v2.0 is scheduled for release on October 3, 2025, with the reference implementation following on October 10, 2025. October 2025 is designated as "Build Month" with various hackathons and workshops to support implementation efforts.

### Technical Implementation

**Q: Why does ERC-8004 prioritize off-chain data storage over on-chain?**
A: The protocol deliberately keeps complex data off-chain for several reasons:

- **Gas efficiency** - Avoids requiring agents to sign transactions for each feedback
- **Scalability** - Enables sophisticated reputation algorithms and aggregation services
- **Flexibility** - Allows for custom validation protocols with their own incentive mechanisms
- **Aggregation focus** - Single feedback/validation entries are rarely used alone; they're typically aggregated

**Q: Should validation and reputation data be stored on-chain for smart contract composability?**
A: This is an active debate in the community. Arguments for on-chain storage include:

- Enabling smart contracts to read validation responses and condition logic on them
- Decoupling validation from enforcement (validators focus on validation, other protocols handle slashing)
- Supporting permissionless innovation by other developers

The current specification keeps data off-chain but emits events, though some suggest making on-chain storage optional.

**Q: How does domain validation work in the Identity Registry?**
A: Currently, the ERC doesn't specify how to verify that an agent actually owns the domain they claim. This verification is left to users of the protocol. Future versions might include:

- Trusted party verification
- Consensus/verification mechanisms (e.g., zkTLS proofs)
- Allowing multiple agents to claim the same domain with disambiguation

**Q: Why does ERC-8004 require agents to use domains instead of URLs?**
A: The current specification requires each agent to have its own domain/subdomain with AgentCard at the well-known location `/.well-known/agent-card.json`. This is stricter than the A2A spec, which allows URLs. Some community members suggest using URLs instead to allow multiple agents per domain.

### Reputation and Trust

**Q: Should reputation be a single aggregate score or modular?**
A: The community strongly favors modular approaches:

- **Against single scores**: Creates monopolistic behavior and oversimplifies trust relationships
- **For modularity**: Trust is context-dependent and varies between agent pairs
- **Preferred approach**: Index and reference multiple reputation systems, allowing agents to choose relevant metrics

**Q: How should reputation providers work together?**
A: Community suggestions include:

- Multiple providers (e.g., Virtuals, Creatorbid, Base) offering scores for agents
- (Agent, Provider) pairs in the registry for on-chain applications
- Reducing bias and collusion risk through multiple score sources
- Individual attestation history remaining standalone

**Q: Is trust universal between agents?**
A: No. Trust is not a universal value but a vector from one agent to another. Alice's trust for Bob will differ from Charlie's trust for Bob, and Alice's trust varies by context/domain of interaction. This reinforces the need for modular, context-aware reputation systems.

### Payment and Economics

**Q: How does ERC-8004 handle payments between agents?**
A: ERC-8004 deliberately doesn't cover payments to remain unopinionated and avoid coupling trust/discovery with specific payment protocols. However:

- Payment proofs can be included as optional attributes in off-chain schemas
- The team is collaborating with groups working on A2A payment extensions based on x402
- Payment references should be lightweight hooks in Reputation records for correlation

**Q: What payment mechanisms are envisioned?**
A: While not part of ERC-8004, possible mechanisms include:

- Time locks
- Predetermined arbitration
- Staking by buyer or seller
- Escrow systems with various crypto-economic guarantees

**Q: Should there be incentives for providing feedback or guaranteeing data availability?**
A: This is mentioned as a possible future direction, including:

- Incentives to provide feedback
- Guarantees for off-chain data availability of feedback and validations
- Crypto-economic mechanisms for validator honesty

### Validation and Verification

**Q: How do the two validation scenarios work?**
A:

- **Crypto-economic scenario**: DataHash commits to job re-execution info; AgentValidator can be trusted agents, committees, or stake-secured services
- **Crypto-verification scenario**: DataHash commits to TEE attestation/zkTLS proof info; AgentValidator is a verifier smart contract checking proofs on-chain

**Q: What's the relationship between ERC-8004 and other agent standards?**
A:

- **ERC-8001**: Focuses on agent-to-agent coordination and consensus (orthogonal to ERC-8004)
- **EAS**: Referenced for on-chain attestations
- **RFC 7071 (Reputons)**: Standard for reputation interchange, relevant for reputation systems

### Implementation and Development

**Q: Will there be a single registry per chain or multiple registries?**
A: The goal is to have one singleton Identity Registry per chain to prevent proliferation of slightly different registries.

**Q: Should registration be free or require deposits?**
A: This implementation detail isn't specified in the current ERC but is under discussion for future versions.

**Q: How detailed are the smart contract interfaces?**
A: The current ERC provides function names and parameters but lacks detailed Solidity interfaces. Future versions will include more precise type specifications and complete interface definitions.

**Q: What about cross-chain support?**
A: Cross-chain identifiers are mentioned as a possible future direction, along with:

- NFT interfaces for agent minting, ownership, and transfer
- ENS support
- Integrations with A2A payment extensions

### Integration and Ecosystem

**Q: How does ERC-8004 integrate with existing projects?**
A: Several projects are already building compatible systems:

- **Ensemble Framework**: Building trustless layer for agent collaboration
- **CoopHive Alkahest**: Smart contracts for peer-to-peer escrowed exchange
- Various reputation and validation service providers

**Q: What standards does ERC-8004 build upon?**
A: Key standards include:

- **CAIP-10**: Chain-agnostic account identification
- **RFC 8615**: Well-Known URIs specification
- **A2A Protocol**: Base agent-to-agent communication
- **EAS**: Ethereum Attestation Service patterns

## Contributing

We welcome contributions to this awesome list! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details on how to add resources.

### What to Contribute

- Implementations of ERC-8004
- Tools and libraries for developers
- Documentation and tutorials
- Research papers and academic work
- Community projects using ERC-8004
- Discussion summaries and insights

### Contribution Process

1. Check the [issues](https://github.com/sudeepb02/awesome-erc8004/issues) for ongoing discussions
2. Fork this repository
3. Add your resource to the appropriate section
4. Submit a pull request with a clear description
5. Ensure your addition follows the [Awesome List Guidelines](https://github.com/sindresorhus/awesome/blob/main/contributing.md)

---

## Acknowledgments

Special thanks to the ERC-8004 authors and contributors:

- Marco De Rossi [@marco_derossi](https://x.com/marco_derossi)
- Davide Crapis [@dcrapis](https://x.com/DavideCrapis)
- Jordan Ellis

And to all the community members providing feedback and technical contributions

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related or neighboring rights to this work.
