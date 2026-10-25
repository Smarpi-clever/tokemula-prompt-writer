# tokemula-prompt-writer

为不同 AI 模型编写与交接 Tokemula 分批任务 Prompt 的 Skill，可安装到 Codex 使用。写作会话负责整理下一份完整、可复制的任务 Prompt；执行、验证和独立审计留给相应会话。

目标模型由用户指定；未指定时使用“执行者”等中性称呼。不预设模型身份、版本或厂商，也不假设所有模型具备相同工具和上下文能力。

这是用户工作流 Skill，并非 OpenAI 官方 Skill。

## 工作方式

- 根据当前目标、最新报告和已有授权确定下一批，明确完成条件和停止边界。
- 保护现有定制、用户工作和数据，不恢复已取消任务。
- 每批预算包含验证、独立审计和交接，最多两次上下文压缩。
- 执行者完成后停止修改待审材料，再独立审查；失败或未知如实保留。

两次压缩预算和自动独立审计是本工作流约定，可按其他项目的真实要求调整。使用前需有当前任务材料；Skill 不包含项目源码、私有交接或运行凭据。

## 安装

将仓库克隆到 Codex Skills 目录；若设置了 `CODEX_HOME`，使用对应的 `skills` 目录：

```sh
git clone https://github.com/Smarpi-clever/tokemula-prompt-writer.git ~/.codex/skills/tokemula-prompt-writer
```

已有本地 `tokemula-astra-prompts` 时，先比较版本，避免同时启用两份同用途 Skill。此仓库不自动改动已有安装或 Codex 配置。

## 使用

```text
使用 $tokemula-prompt-writer。此会话只负责写 Prompt。
根据我提供的最新报告、任务入口和已有授权，写出下一批完整可复制的任务 Prompt。
按我指定的目标模型与实际工具能力组织内容；未指定模型时使用中性执行者称呼。
```

入口是 [SKILL.md](SKILL.md)，首次写作前阅读 [Prompt 写作原则](references/prompt-writing-principles.md)。交接给新写作会话时提供安装后的实际路径。

## 参考与发布内容

原则参考 OpenAI Developers 的 [Rethinking skills and prompts for GPT-6 Astra](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra)。文章名称只用于来源归属，不限制本 Skill 的目标模型。本仓库仅保留独立摘要和来源链接，不再分发第三方文章全文。

本次公开发布未添加开源许可证；公开可见不等于授予开源许可。
