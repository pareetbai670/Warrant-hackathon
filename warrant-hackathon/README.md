# Warrant — permission slips for AI agents

**Agents act. Warrants decide.**

Warrant is a trust layer for multi-agent AI systems. Every tool call an agent wants to make must pass a policy gate and receive a signed, scoped, single-use, expiring *warrant*. Risky actions wait for a human to countersign. Every outcome, including refusals, is written to a SHA-256 hash-chained ledger, so rewriting history is detectable.

## What the demo shows

Three scripted agents (Planner, Researcher, Executor) work a task. The Researcher reads a page with a hidden prompt-injection. Watch the gate:

- **Trust boundary**: refuses actions that began as untrusted outside content.
- **Egress allowlist**: refuses destinations that are not approved.
- **Human countersign**: irreversible or over-limit actions pause for Approve / Deny.
- **Ledger**: hash-chained audit trail with **Verify chain**, **Play attacker** (tamper) and **Export JSON**.

Flip the policy switches mid-run to see an injection succeed, and prove it from the ledger.

Three scenarios: Support desk, DevOps release, Procurement.

## What is real vs. simulated

Real, running in the browser: policy decisions, warrant issuance and signing (demo SHA-256 keyed signature), human countersign flow, hash chain, tamper detection, JSON export.
Simulated: the agents' moves are scripted so the demo is repeatable.

## Run locally

No build step. Open `index.html`, or:

```bash
npx serve .
```

## Deploy to Vercel

1. Push this folder to a GitHub repo (`index.html` must be at the repo root).
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework Preset: **Other**. Leave Build Command and Output Directory empty.
4. Deploy.

## Roadmap

MCP proxy so any agent stack plugs in · Ed25519 signing with hardware-backed keys · policy-as-code (Cedar/Rego) · anchoring ledger roots to a public transparency log.

## Files

- `index.html` — page structure and copy
- `styles.css` — design
- `app.js` — gate, ledger and demo engine
- `vercel.json` — clean URLs and basic security headers
