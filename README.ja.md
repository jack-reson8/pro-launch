# pro-launch

[English](README.md) | [简体中文](README.zh-CN.md) | 日本語 | [한국어](README.ko.md) | [Tiếng Việt](README.vi.md) | [हिन्दी](README.hi.md)

<p align="center"><img src="docs/share.png" alt="pro-launch: from an idea to style frames" width="100%"></p>
<p align="center"><sub><a href="https://github.com/jack-reson8/copy-that"><b>Copy That</b></a> シリーズの一つ · 1 行で全部インストール</sub></p>
<p align="center"><a href="https://jack-reson8.github.io/skill-skill/check/"><img src="https://img.shields.io/badge/skill%20health-100%2F100-brightgreen" alt="skill health 100/100"></a></p>

プロダクトを 0 から 1 へ **センス最優先** で進める Claude Code スキルです。ポジショニング → ネーミング・ドメイン・商標 → リファレンス探し（まず GitHub / OSS、次に App Store とアワード受賞作）→ スタイルバイブル → 機能マップ → UI/UX ビルドループ → アセット生成 → 実機 QA → ローンチ動画 → GTM → グロース → OSS 公開 / App Store 申請、までを扱います。

作った理由：AI が作るプロダクトの多くは、コードではなく次の理由でつまずきます。(1) 本物のリファレンスを調べていない、(2) モデルが自分の成果物を自分で採点している、(3) ユーザーが繰り返し出す修正指示がどこにも記録されない。そこで各フェーズで **実際の成果物** を必ず作らせ、次のフェーズに進む前に **ゲート**（`scripts/phase_gate.py`）を通すようにしています。

## インストール

Claude Code の場合：

```
/plugin marketplace add jack-reson8/pro-launch
/plugin install pro-launch@pro-launch
```

通常のスキルフォルダとして入れる場合：

```bash
git clone https://github.com/jack-reson8/pro-launch /tmp/pro-launch && cp -R /tmp/pro-launch/plugins/pro-launch/skills/pro-launch ~/.claude/skills/
```
あとは Claude Code に「アプリを作って」「この UI はありきたり」「リファレンスを探して」「このプロダクトの名前を考えて」「ローンチを計画して」のように話しかけてください。

**Codex**（CLI または ChatGPT デスクトップアプリ）：

```bash
codex plugin marketplace add jack-reson8/pro-launch
codex plugin add pro-launch@pro-launch
```

`plugins/pro-launch/skills/pro-launch` を `~/.codex/skills/` にコピーしても使えます。このスキルはオープンな [Agent Skills](https://agentskills.io) 標準に沿っているため、Claude Code、Codex、そして SKILL.md を読み込むあらゆるエージェントで動作します。

**その他のエージェント**（Cursor、Gemini CLI、GitHub Copilot など、skills CLI 対応のエージェント）：

```bash
npx skills add jack-reson8/pro-launch
```

## 中身

スキル本体は `plugins/pro-launch/skills/pro-launch` にあり、以下のパスはすべてこのフォルダからの相対パスです。

- `SKILL.md` – フェーズ、ゲート、鉄則
- `references/01-13` – フェーズごとに 1 ページ（複数国展開向けの商標・知財を含む）
- `references/mistakes.md`、`user-repeated-demands.md` – 実際の失敗の記録と、ユーザーが繰り返す要望
- `scripts/` – フェーズゲート、App Store ポスターのダウンローダー、リファレンスのアーカイバ、ドメイン / App Store 名称チェック、切り抜き→ベクター変換パイプライン（Vision + vtracer + svgo）
- `examples/`、`assets/` – 実例とテンプレート

MIT ライセンス。Claude Code のスキルとして動作し、この手法は他のエージェントにも応用できます。
