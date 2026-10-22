# pro-launch

A Claude Code skill that takes a product from 0 to 1 **taste-first**: positioning → naming, domains & trademark → reference hunting (GitHub/open-source first, then App Store and award winners) → style bible → feature map → UI/UX build loop → asset generation → device QA → launch video → GTM → growth → open-source / App Store shipping.

Why it exists: most AI-built products fail not on code but because (1) no real references were studied, (2) the model grades its own work, (3) the user's repeated corrections never get written down. Every phase here forces a **real artifact** and a **gate** (`scripts/phase_gate.py`) before the next phase starts.

## Install
```bash
git clone https://github.com/jack-reson8/pro-launch ~/.claude/skills/pro-launch
```
Then ask Claude Code things like "build me an app", "this UI looks generic", "find references", "name this product", "plan the launch".

## What's inside
- `SKILL.md` – phases, gates, iron rules
- `references/01-13` – one page per phase (incl. trademark & IP for multi-country launches)
- `references/mistakes.md`, `user-repeated-demands.md` – ledger of real mistakes and the demands users repeat
- `scripts/` – phase gate, App Store poster downloader, reference archiver, domain/App Store name check, cutout→vector pipeline (Vision + vtracer + svgo)

MIT licensed. Works with Claude Code skills; the method is portable to other agents.
