[简体中文](README.md) | [English](README.en.md)

<div align="center">

# ⚒️ Scene Anchor System

**Create consistent scene spaces, camera anchors, and composition constraints.**

> 为游戏和视觉叙事建立一致的场景空间、镜头锚点与构图约束。

<p>
  <a href="https://github.com/Fable-Forge/scene-anchor-system/blob/main/LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-0969da"></a>
  <img alt="Maturity: beta" src="https://img.shields.io/badge/maturity-beta-8250df">
  <img alt="Agents: Codex and Claude Code" src="https://img.shields.io/badge/agents-Codex_%C2%B7_Claude_Code-1f883d">
  <a href="https://github.com/Fable-Forge/fableforge-agent-skills/blob/main/SUPPORT.md"><img alt="Sponsor FableForge" src="https://img.shields.io/badge/%E2%99%A5-support_FableForge-bf3989"></a>
</p>

</div>

**[Use cases](#use-cases) · [Quick install](#quick-install) · [Compatibility](#compatibility) · [Validation](#validation) · [Support](https://github.com/Fable-Forge/fableforge-agent-skills/blob/main/SUPPORT.md) · [Contact](#contact)**

---

<a id="use-cases"></a>
## When to use it

Ask your Agent to load this repository's `SKILL.md` when your task matches the outcome above. `SKILL.md` is the authority for triggers, boundaries, and the complete workflow.

<a id="quick-install"></a>
## Quick install

Give this instruction to an Agent with command-line access:

```text
Install scene-anchor-system: https://raw.githubusercontent.com/Fable-Forge/scene-anchor-system/main/docs/install.md
```

Or use the Agent Skills CLI:

```bash
npx skills add Fable-Forge/scene-anchor-system
```

Read the [installation guide](docs/install.md) first. See [update](docs/update.md) and [uninstall](docs/uninstall.md) for lifecycle instructions.

<a id="compatibility"></a>
## Compatibility

- Supported: Codex · Claude Code · Agent Skills
- Maturity: `beta`
- GitHub Topics: `scene-design`, `game-art`, `camera`, `composition`, `narrative`

Compatibility means the repository format and installation paths cover these Agents. It does not guarantee that an already-running session will hot-load the skill. Verify a natural-language trigger in a fresh session after installation.

## Repository layout

- `SKILL.md`: triggers, boundaries, and primary workflow
- `agents/openai.yaml`: Codex display metadata
- `references/`: detailed material loaded on demand, when present
- `scripts/`: reusable tools and repository validator, when present
- `docs/`: install, update, and uninstall guides

<a id="validation"></a>
## Validation boundary

Structural validation, installation visibility, real triggering, and final output quality are separate claims. Passing CI proves only the repository structure and static rules; a real Agent trigger still requires its own acceptance test.

## ❤️ Support the author

These skills are free, open source, and maintained over time. If this one saved you time, you can [support FableForge through Alipay or WeChat](https://github.com/Fable-Forge/fableforge-agent-skills/blob/main/SUPPORT.md). Support is voluntary and does not unlock hidden features, priority service, or commercial rights.

<a id="contact"></a>
## Contact and collaboration

- 📚 All skills: [FableForge Agent Skills](https://github.com/Fable-Forge/fableforge-agent-skills)
- 📧 Email: [53815263@qq.com](mailto:53815263@qq.com)
- 🐛 Bugs and feature requests: [scene-anchor-system Issues](https://github.com/Fable-Forge/scene-anchor-system/issues)
- 💬 Usage questions and business collaboration: [FableForge Discussions](https://github.com/Fable-Forge/fableforge-agent-skills/discussions) or email

## License

[MIT](LICENSE) © 2026 FableForge
