# audit-trail-keeper

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-blue.svg)](SKILL.md)
[![EU AI Act](https://img.shields.io/badge/EU%20AI%20Act-Art.12-brightgreen.svg)](SKILL.md)

SynomosAI four-pillar system: **Identity · Traceability · Governance · Symbiosis**.

> This repo is part of the [SynomosAI](https://github.com/SynomosAI) skill ecosystem.

**Keywords**: audit trail · tamper-evident · hash-chained logging · evidence storage · EU AI Act Art.12

## Quick Start

This repo is an **Agent Skill** (SKILL.md spec).

```bash
git clone https://github.com/SynomosAI/audit-trail-keeper.git
cd audit-trail-keeper
cat SKILL.md
```

```bash
head -15 SKILL.md
# cp -r . ~/.workbuddy/skills/audit-trail-keeper/
```

## What this skill covers

The audit-trail storage layer of the SynomosAI workflow: append-only JSONL records for every model decision, each with five field groups:

- **identity**: actor / subject / role
- **request**: input / intent / context ref
- **model**: model id / version / config
- **policy**: active policy id / rule version
- **integrity**: prev_hash + record_hash + signature

Records are append-only and tamper-evident. Query supports time-range, model-version, and policy-version lookups. Verification recomputes the hash chain and checks signatures. Meets EU AI Act Art.12 retention (≥6 months) and exports FDA / ISO 42001 evidence packages.

## License

MIT License. © 2026 注册老炮@MedXpert.

## Disclaimer

This repo is a theoretical-positioning and tooling exploration; external standards (EU AI Act, FDA, ISO 42001) are paraphrased from public sources; verify independently before formal citation.
