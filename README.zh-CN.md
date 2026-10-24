# pro-launch

[English](README.md) | 简体中文 | [日本語](README.ja.md) | [한국어](README.ko.md) | [Tiếng Việt](README.vi.md) | [हिन्दी](README.hi.md)

<p align="center"><img src="docs/share.png" alt="pro-launch: from an idea to style frames" width="100%"></p>

A Claude Code skill，用 **审美优先** 的方式把产品从 0 做到 1：定位 → 起名、域名与商标 → 找参考（先 GitHub 开源，再 App Store 和获奖作品）→ 风格圣经 → 功能地图 → UI/UX 搭建循环 → 素材生成 → 真机 QA → 发布视频 → GTM → 增长 → 开源 / App Store 上架。

为什么要做它：大多数 AI 做出来的产品，败的不是代码，而是 (1) 没有认真研究过真实参考，(2) 模型自己给自己打分，(3) 用户反复提的纠正从来没被记下来。这里每个阶段都必须产出 **真实的产物**，并在进入下一阶段前通过一道 **关卡**（`scripts/phase_gate.py`）。

## 安装

在 Claude Code 中：

```
/plugin marketplace add jack-reson8/pro-launch
/plugin install pro-launch@pro-launch
```

或者当作普通 skill 文件夹安装：

```bash
git clone https://github.com/jack-reson8/pro-launch /tmp/pro-launch && cp -R /tmp/pro-launch/plugins/pro-launch/skills/pro-launch ~/.claude/skills/
```
然后对 Claude Code 说："帮我做个 App"、"这个 UI 太像模板了"、"找参考"、"给这个产品起名"、"规划发布"。

**Codex**（CLI 或 ChatGPT 桌面端）：

```bash
codex plugin marketplace add jack-reson8/pro-launch
codex plugin add pro-launch@pro-launch
```

也可以把 `plugins/pro-launch/skills/pro-launch` 复制到 `~/.codex/skills/`。该 skill 遵循开放的 [Agent Skills](https://agentskills.io) 标准，所以在 Claude Code、Codex 以及任何读取 SKILL.md 的 agent 里都能用。

**其他 agent**（Cursor、Gemini CLI、GitHub Copilot 以及其他 skills CLI 支持的 agent）：

```bash
npx skills add jack-reson8/pro-launch
```

## 里面有什么

skill 位于 `plugins/pro-launch/skills/pro-launch`，下面所有路径都相对于这个文件夹。

- `SKILL.md` – 各阶段、关卡和铁律
- `references/01-13` – 每个阶段一页（含面向多国上线的商标与知识产权）
- `references/mistakes.md`、`user-repeated-demands.md` – 真实踩坑记录，以及用户反复提的要求
- `scripts/` – 阶段关卡、App Store 海报下载器、参考归档器、域名 / App Store 重名检查、抠图→矢量流水线（Vision + vtracer + svgo）
- `examples/`、`assets/` – 实战示例和模板

MIT 许可。适用于 Claude Code skills；这套方法也可以迁移到其他 agent。
