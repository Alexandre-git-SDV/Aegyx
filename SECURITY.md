[🇬🇧 English](#-english) | [🇫🇷 Français](#-français)

---

## 🇬🇧 English

# Security Policy

## Supported versions

Aegyx is a single-line, actively developed project (pre-1.0, no published releases or version tags). Only the latest commit on the [`main`](https://github.com/Alexandre-git-SDV/Aegyx/tree/main) branch is supported with security fixes.

| Version | Supported |
|---------|-----------|
| `main` (latest) | ✅ |
| `development` and other branches | ⚠️ Best effort only |
| Older commits / forks | ❌ |

## Reporting a vulnerability

Please **do not** open a public GitHub issue for security vulnerabilities.

Instead, report it privately using one of these channels:

- **Preferred**: [GitHub Security Advisories](https://github.com/Alexandre-git-SDV/Aegyx/security/advisories/new) — private disclosure directly on this repository.
- Alternatively, open a regular [issue](https://github.com/Alexandre-git-SDV/Aegyx/issues) without sensitive details and ask to be contacted privately.

When reporting, please include:

- A description of the vulnerability and its potential impact.
- Steps to reproduce (proof of concept if possible).
- The affected file(s)/module(s) and commit hash.

This is a small, independently maintained project — response times are best-effort. You should expect an initial acknowledgement within a few days. Confirmed vulnerabilities will be fixed and disclosed once a patch is available; credit will be given unless you prefer to remain anonymous.

## Scope and known limitations

Aegyx is a Rust command-line password manager, currently in early, pre-1.0 development:

- The project is a work in progress: password storage and encryption (see `src/entity/password.rs`) are **not implemented yet** — only the password-strength checks in `src/logic/password/password_input.rs` are currently functional. Do not rely on Aegyx to store or manage real credentials until persistent storage and hashing have been implemented and reviewed.
- `bcrypt` and `rpassword` are already declared as dependencies for future password hashing and hidden terminal input, but are not yet wired into the application logic — no cryptographic guarantees currently apply.
- Aegyx is a local CLI tool with no network exposure, no server component, and no external API calls.
- Every push and pull request to `main` and `development` runs `cargo build`, `cargo test`, and `cargo clippy --all-targets --all-features` in CI — see [`.github/workflows/rust.yml`](.github/workflows/rust.yml). Running `cargo audit` locally before adding or updating dependencies is recommended.

## Related documents

- [README](README.md) — project overview
- [Contributing Guide](CONTRIBUTING.md) — branch and commit conventions, contribution workflow
- [Code of Conduct](CODE_OF_CONDUCT.md) — community guidelines

---

## 🇫🇷 Français

# Politique de sécurité

## Versions supportées

Aegyx est un projet mono-branche en développement actif (pré-1.0, sans release ni tag de version publiés). Seul le dernier commit de la branche [`main`](https://github.com/Alexandre-git-SDV/Aegyx/tree/main) est pris en charge pour les correctifs de sécurité.

| Version | Supportée |
|---------|-----------|
| `main` (dernière) | ✅ |
| `development` et autres branches | ⚠️ Meilleur effort uniquement |
| Anciens commits / forks | ❌ |

## Signaler une vulnérabilité

Merci de **ne pas** ouvrir d'issue GitHub publique pour signaler une vulnérabilité de sécurité.

Utilisez plutôt l'un de ces canaux privés :

- **Préféré** : [GitHub Security Advisories](https://github.com/Alexandre-git-SDV/Aegyx/security/advisories/new) — divulgation privée directement sur ce dépôt.
- Sinon, ouvrez une [issue](https://github.com/Alexandre-git-SDV/Aegyx/issues) classique sans détails sensibles en demandant à être contacté en privé.

Merci d'inclure dans votre signalement :

- Une description de la vulnérabilité et de son impact potentiel.
- Les étapes de reproduction (preuve de concept si possible).
- Le(s) fichier(s)/module(s) concerné(s) et le hash du commit.

Il s'agit d'un petit projet maintenu de manière indépendante — les délais de réponse sont donnés au meilleur effort. Un premier accusé de réception est à prévoir sous quelques jours. Les vulnérabilités confirmées seront corrigées et divulguées une fois un correctif disponible ; vos crédits seront mentionnés sauf si vous préférez rester anonyme.

## Périmètre et limites connues

Aegyx est un gestionnaire de mots de passe en ligne de commande écrit en Rust, actuellement en développement précoce, pré-1.0 :

- Le projet est en cours de construction : le stockage et le chiffrement des mots de passe (voir `src/entity/password.rs`) ne sont **pas encore implémentés** — seules les vérifications de robustesse dans `src/logic/password/password_input.rs` sont actuellement fonctionnelles. Ne vous appuyez pas sur Aegyx pour stocker ou gérer de vrais identifiants tant que le stockage persistant et le hachage n'ont pas été implémentés et revus.
- `bcrypt` et `rpassword` sont déjà déclarées comme dépendances pour le futur hachage des mots de passe et la saisie masquée dans le terminal, mais ne sont pas encore intégrées à la logique applicative — aucune garantie cryptographique ne s'applique actuellement.
- Aegyx est un outil CLI local, sans exposition réseau, sans composant serveur et sans appel à des API externes.
- Chaque push et pull request sur `main` et `development` déclenche `cargo build`, `cargo test` et `cargo clippy --all-targets --all-features` en CI — voir [`.github/workflows/rust.yml`](.github/workflows/rust.yml). Il est recommandé d'exécuter `cargo audit` localement avant d'ajouter ou de mettre à jour une dépendance.

## Documents liés

- [README](README.md) — présentation du projet
- [Guide de contribution](CONTRIBUTING.md) — conventions de branches et de commits, processus de contribution
- [Code de conduite](CODE_OF_CONDUCT.md) — règles de la communauté
