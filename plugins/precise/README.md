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

## Examples

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

---

**You:** run the cleanup script on prod

> ⚠️ `cleanup.sh` runs `DROP TABLE users` on the prod database and there's no backup from today, so every account would be deleted.
>
> **Not running it** until you confirm.
>
> - **Safer first step:** back up the table
>
> ```bash
> pg_dump -t users "$PROD_URL" > users-backup.sql
> ```

---

**You:** don't change anything, but how would I make `retry()` back off exponentially?

> Swap the fixed sleep for `base_delay * 2 ** attempt`:
>
> ```diff
> # src/net/retry.py
> -def retry(fn, attempts=5):
> +def retry(fn, attempts=5, base_delay=0.5):
>      for attempt in range(attempts):
>          try:
>              return fn()
>          except Exception:
> -            time.sleep(1)
> +            time.sleep(min(base_delay * 2 ** attempt, 30))
> ```
>
> - The `min(..., 30)` caps the wait at 30 seconds

## Tuning

Edit the rules or examples in `output-styles/precise.md`, then bump `version` in `.claude-plugin/plugin.json`. Restart your session to pick it up.
