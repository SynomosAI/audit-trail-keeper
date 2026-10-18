# audit-trail-keeper

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-blue.svg)](SKILL.md)
[![EU AI Act](https://img.shields.io/badge/EU%20AI%20Act-Art.12-brightgreen.svg)](SKILL.md)
[![Tamper Evident](https://img.shields.io/badge/tamper-evident-hash--chain-2ea44f.svg)](SKILL.md)

SynomosAI 四支柱体系：**身份（Identity）· 溯源（Traceability）· 治理（Governance）· 共生（Symbiosis）**——当 AI 进入商业，可信是唯一的硬通货。

> 本仓库属于 [SynomosAI](https://github.com/SynomosAI) 生态技能包的一员。生态全景见 [`synomosai-skills`](https://github.com/SynomosAI/synomosai-skills)，理论站位见 [`traceability-audit`](https://github.com/SynomosAI/traceability-audit)。

**关键词 / Keywords**：审计轨迹 · 防篡改 · 哈希链 · 证据存储 · EU AI Act Art.12 · audit trail · tamper-evident · hash-chained logging

## 🚀 快速开始 / Quick Start

本仓是一个 **Agent Skill 发布包**（遵循 SKILL.md 规范），不是可运行的 SDK。

```bash
# 1. 克隆本仓
git clone https://github.com/SynomosAI/audit-trail-keeper.git
cd audit-trail-keeper

# 2. 查看技能主文件（字段组 / 追加协议 / 验证能力）
cat SKILL.md
```

```bash
# 3. 查看技能元信息
head -15 SKILL.md

# 4. 把技能目录放入你的 Agent 技能目录
#    cp -r . ~/.workbuddy/skills/audit-trail-keeper/
```

## 仓库内容

防篡改审计轨迹守护

本技能是 SynomosAI 工作流的**审计轨迹存储层**：以 append-only JSONL 形式记录每一次模型决策，每条记录包含 identity（身份）、request（请求）、model（模型版本与配置）、policy（生效策略与规则版本）、integrity（哈希链签名）五个字段组。记录只追加、不可篡改；查询能力支持按时间范围、模型版本、策略版本回查；验证能力支持哈希链重算与签名校验。满足 EU AI Act Art.12 对日志保留（≥6 个月）的要求，并可导出 FDA / ISO 42001 格式证据包。

## 元信息

- **技能名**：`audit-trail-keeper`
- **版本**：1.0.0
- **署名**：SynomosAI
- **许可**：MIT（详见仓库 LICENSE）

## 使用方式

1. 克隆本仓库或将该技能目录放入你的 Agent 技能目录（如 `~/.workbuddy/skills/`）；
2. 在 Agent 中按 `SKILL.md` 的描述触发对应能力；
3. 需要审计/合规证据的场景，参考 `SKILL.md` 内模板产出工件。

## 记录结构概览

```text
append-only JSONL
  ├── identity   : actor / subject / role
  ├── request    : input / intent / context ref
  ├── model      : model id / version / config
  ├── policy     : active policy id / rule version
  └── integrity  : prev_hash + record_hash + signature
```

## 仓库结构 / Repository layout

```text
audit-trail-keeper/
├── README.md              # 本文件
├── README.en.md           # 英文版说明
├── SKILL.md               # 技能主文件（字段组 / 追加协议 / 验证能力）
├── LICENSE.md             # MIT License
├── llms.txt               # 给 AI 的最小索引
├── llms-full.txt          # 给 AI 的完整文本
├── AGENTS.md              # 给 AI Agent 的工作指引
├── SECURITY.md            # 安全策略
└── .github/CODEOWNERS      # 代码所有者
```

## License / 许可

本项目以 **MIT** 许可发布，详见仓库根目录 [LICENSE.md](LICENSE.md)。版权：© 2026 注册老炮@MedXpert。

---

## 免责声明

本仓库内容为 SynomosAI 的**理论站位与工具化探索**，不代表任何已获认证、已商业化交付或已服务特定客户的声明；文中涉及的 ISO/IEC 42001、NIST AI RMF、GB/Z 185、EU AI Act、FDA 等外部标准与条款信息为公开资料转述，正式引用前请**独立核实**。API、授权码与形象大使等为路线图（roadmap）事项，尚未上线。
