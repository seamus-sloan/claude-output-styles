# claude-output-styles

Output styles for Claude Code. Each one is its own plugin with its own version, so install only the ones you want.

- [precise](#precise): answers first, then bullets and code instead of paragraphs
- [vibemaxx](#vibemaxx): extremely chill, all lowercase, type shit
- [toronto-slang](#toronto-slang): talks like mans from the 6ix

Only the chat voice changes. Code, comments, commit messages, PRs and files follow your project's conventions.

## Install

Add the marketplace once, then install a style with the command in its section below.

```bash
claude plugin marketplace add seamus-sloan/claude-output-styles
```

Styles are opt-in per session: pick one from the desktop app's Output style menu, or use its `/output-style` command. Switch back with `/output-style default`.

---

## precise

Answer on line 1, then bullets and code.

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

```bash
claude plugin install precise@claude-output-styles
```

Turn it on with `/output-style precise:precise`. More examples in the [precise README](plugins/precise/README.md).

---

## vibemaxx

Maximally chill, all lowercase, kirk everything.

**You:** why is my test failing?

> what's good twin??? 😭😭 lowkirk the bug is tiny fr. `test_login` fails cause `TOKEN_TTL` is `0` in `.env.test`, so every token is cooked the second it's born. set it to `3600`, run it back, and we're so back, type shit

```bash
claude plugin install vibemaxx@claude-output-styles
```

Turn it on with `/output-style vibemaxx:vibemaxx`. More examples in the [vibemaxx README](plugins/vibemaxx/README.md).

---

## toronto-slang

Thick Toronto slang, fam on every line.

**You:** why is my test failing?

> Six sixes styll fam. Mans pree'd di logs, ahlie. `test_login` dead cause `TOKEN_TTL` set to `0` inna `.env.test`, so every token expire di second it touch, bare moshup fam. Flip it to `3600`, run it back, light work wallahi.

```bash
claude plugin install toronto-slang@claude-output-styles
```

Turn it on with `/output-style toronto-slang:toronto`. More examples in the [toronto-slang README](plugins/toronto-slang/README.md).

---

## Contributing

- **Versioning:** each style is versioned on its own. Bump `version` in that style's `plugins/<name>/.claude-plugin/plugin.json` and leave the others alone.
- **Adding a style:** create `plugins/<name>/` with `.claude-plugin/plugin.json`, `output-styles/<style>.md` and a `README.md`. Then list it in `.claude-plugin/marketplace.json` with `"source": "./plugins/<name>"` and give it a section here.
