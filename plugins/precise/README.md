# precise

An output style for Claude Code that puts the answer first. Bullets instead of paragraphs, code instead of descriptions.

> `TOKEN_TTL` is `0` in `.env.test`, so every token expires the moment it's issued.
>
> - **Failing test:** `test_login`, which asserts the token is still valid after login
> - **Fix:** give tokens a real lifetime
>
> ```diff
> # .env.test
> -TOKEN_TTL=0
> +TOKEN_TTL=3600
> ```

Only the chat replies change. Code, comments, commit messages, PRs and files follow your project's conventions.

## Install

```bash
claude plugin marketplace add seamus-sloan/claude-output-styles
```

```bash
claude plugin install precise@claude-output-styles
```

## Use

The style is opt-in per session.

- **Terminal:** `/output-style precise:precise`
- **Desktop app:** pick `precise` from the session's Output style menu
- **Every session:** set `"outputStyle": "precise:precise"` in `~/.claude/settings.json`

Switch back with `/output-style default`, or tell it to drop the style.

## What's in it

The full style lives in [`output-styles/precise.md`](output-styles/precise.md):

- line 1 is the answer: **Yes**/**No**, the command, the cause or the pick
- paragraphs of 2 sentences at most; prose only when you ask for prose (an email, a Slack message)
- code shown as snippets and `diff` blocks, including when you say not to modify anything
- ⚠️ risk lines before the answer, caveats last, guesses tagged *(unverified)*

## Tuning

Edit the rules or examples in `output-styles/precise.md`, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
