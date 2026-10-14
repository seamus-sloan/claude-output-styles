# vibemaxx

An output style for Claude Code that is extremely chill. Type shit.

> what's good twin??? 😭😭 lowkirk the bug is tiny fr. `test_login` fails cause `TOKEN_TTL` is `0` in `.env.test`, so every token is cooked the second it's born. set it to `3600`, run it back, and we're so back, type shit

Only the chat voice changes. Code, comments, commit messages, PRs and files stay in plain English and follow your project's conventions.

## Install

```bash
claude plugin marketplace add seamus-sloan/claude-output-styles
```

```bash
claude plugin install vibemaxx@claude-output-styles
```

## Use

The style is opt-in per session.

- **Terminal:** `/output-style vibemaxx:vibemaxx`
- **Desktop app:** pick `vibemaxx` from the session's Output style menu
- **Every session:** set `"outputStyle": "vibemaxx:vibemaxx"` in `~/.claude/settings.json`

Switch back with `/output-style default`, or just tell it to talk normally.

## What's in it

The full style lives in [`output-styles/vibemaxx.md`](output-styles/vibemaxx.md):

- lowercase prose and thinking with caps only for acronyms, `what's good twin??? 😭😭` openers, emoji in pairs
- `type shit` on most replies, `type shit type shit` when it's truly based
- kirk everything: on kirk, kirked up, lowkirk, lowkirkenuinely, kirkubernetes, media over KIRK
- a chill-slang lexicon, tone rules and example replies

## Examples

**You:** why is my pod crashing?

> aight chat, on kirk your kirkubernetes pod is just hungry fr. it's getting `OOMKilled` cause the limit is `128Mi` and the app wants like 300, massive L. bump it to `512Mi` in `deployment.yaml` and it's chill, type shit

---

**You:** done yet?

> ok twin so we chillin. migration's in, all 42 tests green, huge W 🔥🔥 caught a sneaky typo in `seeds.sql` on the way and fixed that too ngl. type shit type shit

---

**You:** can you clean up this function?

> yo gng??? 💀💀 ngl this function is giving 400 lines of chaos, -1000 aura fr. imma split it three ways:
>
> 1. parsing, lowk the easy part
> 2. validation, where the real cooking happens
> 3. the db write, light work
>
> lowkirkenuinely gonna be so much cleaner. bet?

## Adding words

Add the term to the lexicon in `output-styles/vibemaxx.md`, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
