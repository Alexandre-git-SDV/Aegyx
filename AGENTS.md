# AGENTS.md

Development rules for AI coding agents (Claude Code, Codex, Copilot, ...) working on Aegyx.
They complement [CONTRIBUTING.md](CONTRIBUTING.md), which remains the reference for the
development workflow. When in doubt, CONTRIBUTING.md wins.

---

## Commits and pull requests

- **No AI attribution.** Never add `Co-Authored-By: Claude ...` (or any other AI co-author
  trailer), `🤖 Generated with Claude Code`, or any similar mention to commit messages,
  pull request titles or descriptions. Commits are authored by the repository owner only.
- **Message format:** `[PREFIX] scope: short description`, written in English, using the
  prefixes defined in [CONTRIBUTING.md](CONTRIBUTING.md#commit-naming-conventions)
  (`[FIX]`, `[IMP]`, `[REF]`, `[NEW]`, `[DOC]`, `[TEST]`, `[REV]`, `[I18N]`, `[PERF]`, `[BOT]`).
  `[CI]` is also used for changes limited to `.github/`.
- Commit, push, or open a pull request only when explicitly asked.

## Branches

- `main` — production. Never commit or push directly to it; `development` is promoted to
  `main` only through a reviewed pull request.
- `development` — integration branch, and the repository's default branch.
- `feature/*`, `fix/*` — always created from `development`, merged back into `development`
  through a pull request.
- Never force-push to `main` or `development`, and never rewrite their history, unless
  explicitly asked.

## Before committing

Run the same checks as the CI and make sure they all pass:

```bash
cargo build
cargo test
cargo clippy --all-targets --all-features
```

## Code conventions

- **Layout:** `src/entity/` (data structures), `src/logic/` (business logic: `conditions`,
  `parser`, `password`), `src/i18n/` (translations), `src/main.rs` (entry point only).
- **i18n:** never hardcode user-facing strings. Use `i18n::t("key")` and add every new key
  to **both** `src/i18n/fr.rs` and `src/i18n/en.rs`. French is the default language.
- **Documentation** (`README.md`, `CONTRIBUTING.md`, `SECURITY.md`) is bilingual: update the
  English and the French sections together.
