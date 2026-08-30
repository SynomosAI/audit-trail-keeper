---
name: audit-trail-keeper
description: >-
  This skill is the tamper-evident storage layer for the human-AI co-governance
  loop, implementing EU AI Act Article 12 automatic record-keeping. Use it to
  append, store, query, and verify AI decision/action logs as an immutable,
  hash-chained, signed JSONL series with >=6-month retention. It is the "工具显影"
  (artifact-rendering) storage that makes ai-governance's audit trail real, not
  just a schema. Supports regime-specific export (EU AI Act / FDA / ISO 42001).
  Humans own accountability; the trail is the proof.

version: 1.0.0
author: 注册老炮@MedXpert
license: MIT
category: 合规审计
platforms: [windows, macos, linux]
displayName: 审计轨迹留存器
title: 审计轨迹留存器
tags: [审计轨迹, 审计留存, 合规审计, 证据链, 可信]
---

# Audit Trail Keeper（防篡改审计轨迹保管 · Art.12）

## Overview

`ai-governance` defines *what* to log; this skill *stores and proves* it. Append-only JSONL, where each record carries a hash-chain pointer to the prior record plus a signature over its canonical serialization. Modifying any record breaks the chain and fails verification. This is the engineering answer to Art.12 "automatic" + "tamper-resistant" logging.

## When to use

- Any governed AI action / external publish / evaluation — emit a trail record.
- An auditor or customer requests evidence of control.
- Periodic integrity verification of the trail.

## Core capabilities

### 1. Append
Canonical JSONL record: fixed field order, deterministic serialization. Field groups:
- **identity**: natural person (caller) + agent identity + session id.
- **request**: timestamp (ms), route, prompt fingerprint (content hash), classifications (PII/PHI/MNPI), tool-call set.
- **model**: provider / name / version / endpoint / params / token counts.
- **policy**: bundle version, matched rules, decision (passed / redacted / blocked / queued), rationale.
- **integrity**: signature over canonical record, hash-chain pointer to prior record, anchoring receipt.
The write path sits outside the application so the app cannot alter the record.

### 2. Query
By `agent_id` / `skill` / `intent` / time-range / `verdict`. Per-record retrieval + per-series replay.

### 3. Verify
Per-record signature check + series hash-chain check. Invalid signature → tampering signal; broken chain → retroactive insert / delete / modify detected.

### 4. Retention
Default **>=6 months** (Art.26(5)); configurable longer for sector law (FDA / SOC 2 / California). Auto-archive; never silent-delete within the window.

### 5. Export
Regime-specific field projection: EU AI Act Art.12 (timestamp, natural-person id, input, verification persons), FDA 21 CFR Part 11, ISO/IEC 42001 A.6.2.8.

## Workflow

1. Receive a decision / action event (from `ai-governance` or `human-oversight-gate`).
2. Canonicalize → sign → append with hash-chain pointer.
3. On query / audit: verify chain + signatures, project requested fields.
4. Enforce retention; emit export on demand.

## Bridging existing skills

| Need | Delegate to |
|---|---|
| Gate decision source | `ai-governance` |
| Human sign-off record | `human-oversight-gate` |
| Signature key custody | `authz-code-design` / credential vault |

## Compliance mapping

- **EU AI Act Art.12** (automatic logging) + **Art.26(5)** (>=6-month retention).
- **ISO/IEC 42001:2023 A.6.2.8** (recording of event logs).
- **NIST AI RMF** (traceability across Govern / Map / Measure / Manage).
- **FDA 21 CFR Part 11** (audit trails for regulated decisions).

## Status（占位已落）

上述 5 项能力已落到本 SKILL.md；签名密钥 custody 与 `AUDIT_ROOT` 存储路径为运行环境依赖（非阻塞，待真实部署时配置）。

---

## 交付元数据（Deliverable Metadata）

- **版权（Copyright）**：© 2026 注册老炮@MedXpert。保留所有权利。引用需附出处。
- **时间戳（Timestamp）**：2026-08-28 10:41 GMT+8（生成）
- **指纹（Fingerprint / SHA-256）**：637a087cd2e984124572d00892efe7ed18e083221d0d411545bb1a28ee091c30（正文 SHA-256，不含本元数据块，可复验）
- **配套治理框架**：`人与AI治理理论及闭环落地_v1.0.md`（外部共享治理框架，未随包，需从治理理论知识库另行获取）
