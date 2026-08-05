# understanding

A Claude Code / Cursor skill that turns agent-created work — diffs, features, plans, investigations, architecture — into a short [Sideshow](https://github.com/modem-dev/sideshow) session optimized for *understanding*, not coverage.

Invoke with `/understanding` (or ask to understand what an agent made). The skill is invoke-only; it does not auto-trigger.

## Install

```bash
# Claude Code
git clone https://github.com/grqg-dev/understanding.git ~/.claude/skills/understanding

# Cursor (project or user skills)
git clone https://github.com/grqg-dev/understanding.git ~/.cursor/skills/understanding
```

Or copy `SKILL.md` into your skills directory.

## Requires

- [`sideshow`](https://github.com/modem-dev/sideshow) CLI on `PATH`
- A running sideshow surface (`sideshow serve`), or `SIDESHOW_URL` set

The skill calls `sideshow agent-howto` and `sideshow guide` at session start. It does not embed those docs.

## What it does

Builds a progressive-disclosure explanation:

1. **Orientation** — one-sentence headline, then what this is, why it exists, what changed, why you care
2. **Background** — deep (skippable) + narrow (needed for this work)
3. **Core intuition** — before → after → because, one concrete example, and the likely misconception corrected
4. **Walkthrough** — one representative scenario end to end
5. **Consequences** — what is now true, what breaks it, where to go next

Every post opens with its one-line takeaway. Before finishing, the agent runs a silent **transfer test** — can the core idea, predicted behavior, bug-location, misconception, and model limits all be answered from the posts alone? If not, it revises. The user is never quizzed.

## License

MIT
