# claude-output-styles

Output styles for Claude Code. Each one is its own plugin with its own version, so install only the ones you want.

- [precise](#precise): answers first, then bullets and code instead of paragraphs
- [vibemaxx](#vibemaxx): extremely chill, all lowercase, type shit
- [toronto-slang](#toronto-slang): talks like mans from the 6ix

Only the chat voice changes. Code, comments, commit messages, PRs and files follow your project's conventions.

## Install

Add the marketplace once:

```bash
claude plugin marketplace add seamus-sloan/claude-output-styles
```

Then install the styles you want:

```bash
claude plugin install precise@claude-output-styles
claude plugin install vibemaxx@claude-output-styles
claude plugin install toronto-slang@claude-output-styles
```

## Use

Styles are opt-in per session. Pick one from the desktop app's Output style menu, or:

| Style | Terminal | `outputStyle` in `~/.claude/settings.json` |
|---|---|---|
| precise | `/output-style precise:precise` | `"precise:precise"` |
| vibemaxx | `/output-style vibemaxx:vibemaxx` | `"vibemaxx:vibemaxx"` |
| toronto-slang | `/output-style toronto-slang:toronto` | `"toronto-slang:toronto"` |

Switch back with `/output-style default`, or tell it to talk normally.

## Examples

### precise

Answer on line 1, then bullets and code. More in [`plugins/precise`](plugins/precise).

**You:** why is my test failing?

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

**You:** should I use SQLite or Postgres for this?

> **SQLite.** It's one process on one machine, with no concurrent writers.
>
> | | SQLite | Postgres |
> |---|---|---|
> | Setup | a file | a server |
> | Concurrent writes | one at a time | many |
> | Fits this app | ✅ | overkill |
>
> - **Switch when** you add a second writer or a second server

### vibemaxx

Maximally chill, all lowercase, kirk everything. More in [`plugins/vibemaxx`](plugins/vibemaxx).

**You:** why is my test failing?

> what's good twin??? 😭😭 lowkirk the bug is tiny fr. `test_login` fails cause `TOKEN_TTL` is `0` in `.env.test`, so every token is cooked the second it's born. set it to `3600`, run it back, and we're so back, type shit

**You:** why is my pod crashing?

> aight chat, on kirk your kirkubernetes pod is just hungry fr. it's getting `OOMKilled` cause the limit is `128Mi` and the app wants like 300, massive L. bump it to `512Mi` in `deployment.yaml` and it's chill, type shit

### toronto-slang

Thick Toronto slang, fam on every line. More in [`plugins/toronto-slang`](plugins/toronto-slang).

**You:** why is my test failing?

> Six sixes styll fam. Mans pree'd di logs, ahlie. `test_login` dead cause `TOKEN_TTL` set to `0` inna `.env.test`, so every token expire di second it touch, bare moshup fam. Flip it to `3600`, run it back, light work wallahi.

**You:** rebase my branch onto main

> Seven sevens on god fam. Two-twos dat rebase turn into a donnybrook, three conflicts inna `src/auth/session.ts` alone, proper tilly styll. Mans dangled round di first two, and di last one went top cheese once mans kept both imports. Test-dem green, celly time fam, dun know.

## Versioning

Each style is versioned on its own. When you change a style, bump `version` in that style's `plugins/<name>/.claude-plugin/plugin.json` and leave the others alone.

## Adding a style

1. Create `plugins/<name>/` with `.claude-plugin/plugin.json`, `output-styles/<style>.md` and a `README.md`.
2. Add the plugin to `.claude-plugin/marketplace.json` with `"source": "./plugins/<name>"`.
3. Add it to the list at the top of this README and to Examples.
