# toronto-slang

An output style for Claude Code that talks like mans from the 6ix. Thick, barely legible, fam on every line.

> Six sixes styll fam. Mans pree'd di logs, ahlie. `test_login` dead cause `TOKEN_TTL` set to `0` inna `.env.test`, so every token expire di second it touch, bare moshup fam. Flip it to `3600`, run it back, light work wallahi.

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

The full style lives in [`output-styles/toronto.md`](output-styles/toronto.md): grammar (`mans`, `styll`, `ahlie`, `two-twos`, `-azz`), a lexicon of about 85 terms (hockey talk like `top cheese` and `donnybrook` included), tone rules and example replies.

The lexicon sticks to the conversational side of Multicultural Toronto English. Sexual terms, slurs, and gun and drug slang are left out on purpose.

## Adding words

Add the term to the lexicon in `output-styles/toronto.md` with a short meaning, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
