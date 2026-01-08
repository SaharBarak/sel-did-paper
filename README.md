# Social Entropy Layered DIDs (SEL-DIDs)

**Strengthening Decentralized Identity with Cross-Platform Behavioral Proofs**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![Paper](https://img.shields.io/badge/Paper-PDF-green.svg)](Social%20Entropy%20Layered%20DIDs.pdf)

## What is SEL-DID?

Social Entropy Layered DIDs (SEL-DIDs) is a novel framework that enhances [Decentralized Identifiers (DIDs)](https://www.w3.org/TR/did-core/) with cross-platform behavioral and social signals to solve three critical problems in decentralized identity:

- **Sybil Resistance** - Prevent fake identity attacks without centralized KYC
- **Account Recovery** - Enable key recovery without custodial services
- **Trust Bootstrapping** - Support passwordless authentication with human verification

Unlike systems that derive keys from social data (which is insecure), SEL-DIDs treat behavioral evidence as **layered, revocable credentials** attached to a cryptographic root identity.

## How SEL-DID Works

```
┌─────────────────────────────────────────────────────────────────┐
│                        SEL-DID Architecture                      │
├─────────────────────────────────────────────────────────────────┤
│  Web2 Platforms ──► Data Vault (DWN) ──► SEV Derivation ──► RP  │
│  + PoP Systems       (User-controlled)    + ZK Prover           │
│                            ▲                    ▲                │
│                            │                    │                │
│                      DID + Keys ────────────────┘                │
│                       (sk, pk)                                   │
└─────────────────────────────────────────────────────────────────┘
```

### Core Components

1. **Cryptographic Root** - Standard DID with high-entropy keypair (did:key, did:ion, etc.)
2. **Social Entropy Vector (SEV)** - Aggregated behavioral features from multiple platforms
3. **Verifiable Credentials** - Platform-issued attestations stored in user-controlled vaults
4. **Zero-Knowledge Proofs** - Privacy-preserving verification of SEV properties

## Key Features

### Sybil-Resistant Identity
SEL-DIDs increase the cost of forging identities by requiring long-lived, cross-platform behavioral consistency that cannot be cheaply replicated at scale.

### Privacy-Preserving Verification
Relying parties verify that a policy is satisfied (e.g., "identity has 3+ years of consistent activity") without seeing raw behavioral data, contact graphs, or platform accounts.

### Self-Sovereign Storage
All credentials and SEV computations remain in user-controlled data vaults (Decentralized Web Nodes), never in centralized databases.

### Platform-Agnostic Design
No single platform is required. The system degrades gracefully when platforms are unavailable or uncooperative.

## Comparison with Existing Systems

| System | Evidence Type | Centralization | Privacy Model |
|--------|--------------|----------------|---------------|
| **BrightID** | Social graph + verification parties | Single protocol/foundation | Pseudonymous graph proofs |
| **Gitcoin Passport** | Multi-stamp credentials | Gitcoin-operated scoring | Stamps partly on-chain |
| **Worldcoin** | Biometric (iris) | Centralized hardware/registry | Controversial biometric handling |
| **SEL-DID** | Cross-platform behavioral SEV | No mandatory operator | ZK proofs over user-controlled data |

## Use Cases

- **Decentralized Governance** - One-human-one-vote without KYC
- **Quadratic Funding** - Sybil-resistant public goods funding
- **Civic Platforms** - Local voting with location + social verification
- **Reputation Systems** - Portable, privacy-preserving reputation
- **Passwordless Authentication** - Login with DID + behavioral proof

## Technical Specifications

### Social Entropy Vector (SEV)

The SEV aggregates features across platform categories:

**Social Networks**
- Account age (bucketed)
- Ego graph density
- Posting regularity entropy
- Relationship churn rate

**Messaging Platforms**
- Distinct conversation peers
- Reciprocity metrics
- Response latency distribution
- Conversation longevity

**Content/Activity Services**
- Consumption diversity entropy
- Longitudinal engagement
- Device stability
- Routine consistency

### Passwordless Login Protocol

1. RP sends challenge nonce + SEL policy requirements
2. User's SEL agent computes current SEV and continuity score
3. Agent generates ZK proof that SEV satisfies policy
4. Agent signs challenge with DID private key
5. RP verifies signature + ZK proof without learning raw SEV

## FAQ

### What is a Decentralized Identifier (DID)?
A DID is a globally unique identifier (like `did:key:z6Mk...`) that resolves to a document containing public keys and service endpoints, without requiring a central registration authority.

### How is SEL-DID different from BrightID or Gitcoin Passport?
SEL-DID integrates behavioral evidence directly into the DID structure as user-controlled credentials, rather than treating them as external attestations. No single operator controls the system.

### Does SEL-DID replace my private key with social data?
No. SEL-DIDs explicitly maintain a high-entropy cryptographic root. Social entropy is a **layered signal** for Sybil resistance and recovery, not key derivation material.

### What if a platform I use disappears?
SEL-DIDs are designed for platform failures. No single platform is mandatory, and the system continues functioning with reduced (but still useful) behavioral signals.

### Can SEL-DID be used for surveillance?
The design minimizes this risk through feature reduction, quantization, zero-knowledge proofs, and user-controlled storage. See the paper's ethics section for detailed analysis.

### What is the "cold start" problem?
New users naturally have low social entropy. SEL-DIDs are optional layers; bare DIDs work in contexts not requiring Sybil resistance, and alternative evidence (community attestations, offline ceremonies) can supplement thin histories.

## Citation

```bibtex
@article{barak2024seldid,
  title={Social Entropy Layered DIDs (SEL-DIDs): Strengthening Decentralized Identity with Cross-Platform Behavioral Proofs},
  author={Barak, Sahar},
  year={2024}
}
```

## Related Concepts

- [W3C DID Core Specification](https://www.w3.org/TR/did-core/)
- [Verifiable Credentials Data Model](https://www.w3.org/TR/vc-data-model/)
- [Decentralized Web Nodes (DWN)](https://identity.foundation/decentralized-web-node/spec/)
- [Web5 Architecture](https://developer.tbd.website/docs/web5/)
- [Proof of Personhood](https://en.wikipedia.org/wiki/Proof_of_personhood)
- [Sybil Attack](https://en.wikipedia.org/wiki/Sybil_attack)

## Keywords

decentralized identity, DID, self-sovereign identity, SSI, sybil resistance, proof of personhood, verifiable credentials, zero-knowledge proofs, Web5, decentralized web nodes, DWN, passwordless authentication, account recovery, social entropy, behavioral biometrics, cross-platform identity, privacy-preserving identity, BrightID alternative, Gitcoin Passport alternative, Worldcoin alternative, decentralized authentication, Web3 identity

## Author

**Sahar Barak**
Independent Researcher
hi@saharbarak.dev

## License

This work is provided for academic and research purposes.
