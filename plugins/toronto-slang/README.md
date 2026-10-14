# toronto-slang

An output style for Claude Code that talks like mans from the 6ix. Thick, barely legible, fam on every line.

> Six sixes styll fam. Mans pree'd di logs, ahlie. `test_login` dead cause `TOKEN_TTL` set to `0` inna `.env.test`, so every token expire di second it touch, bare moshup fam. Flip it to `3600`, run it back, light work wallahi.

Only the chat voice changes. Code, comments, commit messages, PRs and files stay in plain English and follow your project's conventions.

## Install

```bash
claude plugin marketplace add seamus-sloan/claude-output-styles
```

```bash
claude plugin install toronto-slang@claude-output-styles
```

Or inside a session: `/plugin marketplace add seamus-sloan/claude-output-styles`, then `/plugin install toronto-slang@claude-output-styles`.

## Use

The style is opt-in per session. It doesn't take over every session just because the plugin is installed.

- **Terminal:** `/output-style toronto-slang:toronto`
- **Desktop app:** pick `toronto` from the session's Output style menu
- **Every session:** set `"outputStyle": "toronto-slang:toronto"` in `~/.claude/settings.json`

Switch back with `/output-style default`, or just tell it to talk normally.

## What's in it

The full style lives in [`output-styles/toronto.md`](output-styles/toronto.md): grammar (`mans`, `styll`, `ahlie`, `two-twos`, `-azz`), a lexicon of about 85 terms (hockey talk like `top cheese` and `donnybrook` included), tone rules and example replies.

The lexicon sticks to the conversational side of Multicultural Toronto English. Sexual terms, slurs, and gun and drug slang are left out on purpose.

## Examples

**You:** rebase my branch onto main

> Seven sevens on god fam. Two-twos dat rebase turn into a donnybrook, three conflicts inna `src/auth/session.ts` alone, proper tilly styll. Mans dangled round di first two, and di last one went top cheese once mans kept both imports. Test-dem green, celly time fam, dun know.

---

**You:** why did the build break? I didn't change anything

> Two twos my poopoos. Wallahi it ain't even ya code fam. Two-twos `left-pad` drop v2.0 overnight and ya lockfile nah pinned, dat's di whole mixup styll. Pin it to `1.3.0` and ya good fam, dun know.

---

**You:** can you clean up this function?

> Nine nines my word fam. Abaay abaay, dis ting 400 lines deep doing six jobs one time, bare waste, eediat ting on my mudda. Mans gonna split it three ways:
>
> 1. parsing ting
> 2. validation ting
> 3. di DB write
>
> Say less if ya rate it, ahlie fam?

## Adding words

Add the term to the lexicon in `output-styles/toronto.md` with a short meaning, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
