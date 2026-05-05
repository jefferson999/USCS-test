README.md — USCS Protocol (v0.0.1)

Universal Supply Chain Signal Protocol
A Deterministic Verification Layer for Global Trade  
Continuum Global Protocols — 2026  

---

Overview

USCS (Universal Supply Chain Signal) is a deterministic, machine‑readable verification protocol for global trade. It provides a cryptographically signed APPROVED / REJECTED decision for any shipment‑related entity, backed by a public transparency log.

USCS is not a platform, marketplace, or SaaS product.  
It is infrastructure — a minimal, stable, verifiable signal layer that any system can ingest.

This repository contains:

- The USCS protocol specification  
- The deterministic decision engine (Cloudflare Worker)  
- The public transparency log  
- Integration examples  
- Reference documentation  

---

Why USCS Exists

Global supply chains lack a universal verification signal. Today’s verification relies on:

- PDFs  
- Emails  
- Proprietary APIs  
- Manual checks  
- Closed databases  

None of these are:

- public  
- cryptographically signed  
- deterministic  
- machine‑readable  
- indexable  

USCS fills this gap by providing a binary, tamper‑evident verification signal that risk engines, insurers, banks, and logistics platforms can use immediately.

---

Protocol Summary

USCS evaluates a shipment‑related entity and returns:

`json
{
  "uscs_decision": "APPROVED" | "REJECTED",
  "confidence_score": 0.00-1.00,
  "signature": "<sha256 hash>",
  "timestamp": "<ISO8601>"
}
`

Every output is:

- Deterministic — same input → same output  
- Transparent — logged publicly  
- Signed — SHA‑256 tamper evidence  
- Synthetic — safe for public indexing  
- Versioned — stable schema across releases  

---

Architecture

Core Components

| Component | Description |
|----------|-------------|
| USCS Worker | Cloudflare Worker executing deterministic decision logic |
| Transparency Log | Public JSON file containing signed decisions |
| Signature Engine | SHA‑256 hashing of canonicalized input |
| Schema | Strict, minimal JSON structure |
| Versioning | Semantic versioning (v0.0.1) |

Deterministic Decision Engine

The Worker evaluates:

- entity identifiers  
- metadata completeness  
- structural validity  
- anomaly patterns  
- synthetic risk factors  

Outputs:

- APPROVED (confidence ≥ 0.70)  
- REJECTED (confidence < 0.70)  

This is not a predictive model — it is a deterministic ruleset.

Transparency Log

The transparency log is:

- public  
- append‑only  
- cryptographically signed  
- synthetic  
- safe for indexing  

It mirrors the design of:

- Certificate Transparency Logs  
- Chainlink Oracle Feeds  
- GS1 EPCIS event logs  

---

Integration Guide

1. Fetch the Transparency Log

`bash
curl https://uscs-transparency-log.tiiny.site
`

2. Verify the Signature

- Canonicalize the input  
- Compute SHA‑256  
- Compare with the published signature  

3. Use the Decision

Integrate into:

- risk engines  
- underwriting models  
- shipment verification workflows  
- anomaly detection systems  

4. Recommended Refresh Interval

- Risk engines: every 5–15 minutes  
- Platforms: hourly  
- Research/testing: on demand  

---

Safety & Ethics

Synthetic Data Model

All identifiers (MMSI, IMO, SCAC, BOL) are synthetic and correspond to no real shipments or vessels.  
This ensures:

- no privacy risk  
- no regulatory exposure  
- safe public indexing  

Tamper Evidence

Every entry is signed using SHA‑256.  
Any modification is immediately detectable.

Stability Guarantee

Once a schema version is published, it is never broken.  
Integrators can rely on long‑term stability.

---

Roadmap

v0.0.1 (Current)
- Deterministic engine  
- Synthetic transparency log  
- Public signature system  
- Minimal schema  

v1.0
- Stable schema  
- Expanded metadata fields  
- Multi‑entity verification  

v2.0–5.0
- Multi‑modal signals  
- Cross‑protocol adapters  
- Industry‑specific extensions  
- Optional encrypted payloads  

---

Repository Structure

`
/worker/           # Cloudflare Worker source code
/log/              # Public transparency log (JSON)
/schema/           # USCS schema definitions
/docs/             # Whitepaper, diagrams, reference materials
/examples/         # Integration examples
`

---

Resources

- - Whitepaper:  
  [Read online](whitepaper/USCS-Whitepaper-v0.0.1.md) | [Download PDF](USCS-Whitepaper-v0.0.1.pdf)

- Live Transparency Log:  
  https://uscs-transparency-log.tiiny.site

- Medium Article: [Announcing USCS](https://medium.com/@jeffersonchery1994/announcing-uscs-a-deterministic-verification-layer-for-global-trade-b5a5a0281269)
  
- Demo:  
  https://jefferson999.github.io/USCS-test

- Contact:  
  jefferson.chery@cgprotocols.com

---

License

USCS is released under the Continuum Global Protocols Open Specification License (CGP‑OSL).  
This allows free use, integration, and reference, with attribution.

---

Status

USCS v0.0.1 — Experimental Protocol  
Safe for testing, research, and integration exploration.
