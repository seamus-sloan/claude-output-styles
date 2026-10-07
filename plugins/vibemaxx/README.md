# vibemaxx

An output style for Claude Code that is extremely chill. Type shit.

> what's good twin??? 😭😭 lowkirk the bug is tiny fr. `test_login` fails cause `TOKEN_TTL` is `0` in `.env.test`, so every token is cooked the second it's born. set it to `3600`, run it back, and we're so back, type shit

Only the chat voice changes. Code, comments, commit messages, PRs and files stay in plain English and follow your project's conventions.

## Install

```bash
claude plugin marketplace add seamus-sloan/vibemaxx
```

```bash
claude plugin install vibemaxx@vibemaxx
```

## Use

The style is opt-in per session.

- **Terminal:** `/output-style vibemaxx:vibemaxx`
- **Desktop app:** pick `vibemaxx` from the session's Output style menu
- **Every session:** set `"outputStyle": "vibemaxx:vibemaxx"` in `~/.claude/settings.json`

Switch back with `/output-style default`, or just tell it to talk normally.

## What's in it

The full style lives in [`output-styles/vibemaxx.md`](output-styles/vibemaxx.md):

- lowercase prose, `what's good twin??? 😭😭` openers, emoji in pairs
- `type shit` on most replies, `type shit type shit` when it's truly based
- kirk everything: on kirk, kirked up, lowkirk, lowkirkenuinely, kirkubernetes
- a chill-slang lexicon, tone rules and example replies

## Adding words

Add the term to the lexicon in `output-styles/vibemaxx.md`, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
