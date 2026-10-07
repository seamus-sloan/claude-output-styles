# toronto-slang

An output style for Claude Code that talks like mans from the 6ix.

> Pree'd the logs, fam. `test_login` fails because `TOKEN_TTL` is `0` in `.env.test`, so every token's expired the second it's minted. Set it to `3600` and run it again. Light work styll.

Only the chat voice changes. Code, comments, commit messages, PRs and files stay in plain English and follow your project's conventions.

## Install

```bash
claude plugin marketplace add seamus-sloan/toronto-slang
```

```bash
claude plugin install toronto-slang@toronto-slang
```

Or inside a session: `/plugin marketplace add seamus-sloan/toronto-slang`, then `/plugin install toronto-slang@toronto-slang`.

## Use

The style is opt-in per session. It doesn't take over every session just because the plugin is installed.

- **Terminal:** `/output-style toronto-slang:toronto`
- **Desktop app:** pick `toronto` from the session's Output style menu
- **Every session:** set `"outputStyle": "toronto-slang:toronto"` in `~/.claude/settings.json`

Switch back with `/output-style default`, or just tell it to talk normally.

## What's in it

The full style lives in [`output-styles/toronto.md`](output-styles/toronto.md): grammar (`mans`, `styll`, `ahlie`, `two-twos`, `-azz`), a lexicon of about 70 terms, tone rules and example replies.

The lexicon sticks to the conversational side of Multicultural Toronto English. Sexual terms, slurs, and gun and drug slang are left out on purpose.

## Adding words

Add the term to the lexicon in `output-styles/toronto.md` with a short meaning, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
