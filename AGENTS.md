# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`audit-trail-keeper` 是一个 **Agent Skill 发布包**，核心资产是 `SKILL.md`。把本目录放入 Agent 的技能目录即可获得「防篡改审计轨迹存储」能力。

## 可用的工作命令

```bash
head -15 SKILL.md
cat SKILL.md
```

## 约定（Do）

- 修改 `SKILL.md` 时保持 YAML frontmatter 字段兼容。
- 新增字段组时同步更新追加协议与验证能力描述。

## 禁止（Don't）

- 不要改动 `LICENSE.md` 的版权主体（© 2026 注册老炮@MedXpert）。
- 不要在仓库内提交任何真实客户数据、密钥或签名私钥。
- 不要声称本技能「已通过监管认证」。

## 边界

本技能专注审计轨迹存储与验证；不覆盖策略制定、风险评估等独立技能域。
