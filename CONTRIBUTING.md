<a id="en"></a>
[🇫🇷 Lire en français ⇩](#fr)

# Contributing Guide

This file defines the branch and commit conventions for the
**Aegyx** repository. It applies to all
contributors and is the reference for the development workflow.

> Looking to report a security vulnerability instead? See the [Security Policy](SECURITY.md).

---

## Branch management

### Structure

```
  main (production)
    │
    └── development (integration / active development)
          │
          └── feature/*, fix/* (created from development)
```

- **`main`** — production branch, holds the current released, stable version of the app.
- **`development`** — active development branch where features and fixes are
  integrated and tested (including via CI) before being promoted to `main`.

### Rules

| Rule | Description |
|------|-------------|
| **Creation** | `feature/*` / `fix/*` branches are always created from `development` |
| **Validation** | Once development is finished, a Pull Request is opened towards `development` |
| **Merge to development** | After PR validation (CI green: build, tests, clippy), the branch is merged into `development` |
| **Promotion to production** | `development` is merged into `main` when a release is ready |
| **Forbidden** | No branch should be created directly from `main` |
| **Forbidden** | `development` must never be merged directly into `main` without going through a reviewed PR |

---

## Commit naming conventions

### Prefixes

| Prefix | Meaning | When to use it |
|--------|---------|-----------------|
| **[FIX]** | Bug Fix | Fixing an existing bug. |
| **[IMP]** | Improvement | Code improvement, optimization, UX, performance, light cleanup without changing functional behavior. |
| **[REF]** | Refactoring | Significant code restructuring, moving, or removing code without adding a feature or directly fixing a bug. |
| **[NEW]** | Add | Adding a new feature. |
| **[DOC]** | Documentation | Documentation-only change (README, comments, guides...). |
| **[TEST]** | Tests | Adding, changing, or fixing unit or integration tests. |
| **[REV]** | Revert | Reverting a previous commit. |
| **[I18N]** | Internationalization | Changes to translations or the `i18n` module. |
| **[PERF]** | Performance | Performance optimization without functional change. |
| **[BOT]** | Automated Commit | Commit generated automatically (e.g. dependency bump, formatting). |

### Examples

```
[FIX] logic: reject passwords shorter than 12 characters
[IMP] i18n: simplify translation lookup
[REF] logic: split password checks into dedicated functions
[NEW] entity: add Password struct
[DOC] README: update installation instructions
[TEST] logic: add regression test for digit check
[I18N] add English translations
[BOT] update Cargo.lock
```

---

## Contribution process

1. Create a `feature/*` or `fix/*` branch from `development`
2. Implement your change
3. Run `cargo build`, `cargo test`, and `cargo clippy --all-targets --all-features` locally (same checks as CI)
4. Open a Pull Request towards `development`
5. Once the PR is reviewed, approved, and CI is green, it is merged into `development`
6. `development` is periodically merged into `main` for releases

---
---

<a id="fr"></a>
[🇬🇧 Read in English ⇧](#en)

# Guide de contribution (Français)

Ce fichier définit les règles de gestion des branches et des commits pour
le dépôt **Aegyx**. Il s'applique à
l'ensemble des contributeurs et constitue la référence pour le workflow
de développement.

> Vous souhaitez signaler une vulnérabilité de sécurité ? Consultez la [Politique de sécurité](SECURITY.md).

---

## Gestion des branches

### Structure

```
  main (production)
    │
    └── development (intégration / développement actif)
          │
          └── feature/*, fix/* (créées depuis development)
```

- **`main`** — branche de production, contient la version stable actuellement publiée de l'application.
- **`development`** — branche de développement actif où les fonctionnalités
  et correctifs sont intégrés et testés (notamment via la CI) avant d'être
  promus vers `main`.

### Règles

| Règle | Description |
|-------|-------------|
| **Création** | Les branches `feature/*` / `fix/*` sont toujours créées depuis `development` |
| **Validation** | Une fois le développement terminé, une Pull Request est ouverte vers `development` |
| **Merge vers development** | Après validation de la PR (CI au vert : build, tests, clippy), la branche est fusionnée dans `development` |
| **Promotion en production** | `development` est mergé vers `main` lorsqu'une release est prête |
| **Interdit** | Aucune branche ne doit être créée directement depuis `main` |
| **Interdit** | `development` ne doit jamais être mergé directement dans `main` sans passer par une PR revue |

---

## Conventions de nommage des commits

### Préfixes

| Préfixe | Signification | Quand l'utiliser |
|---------|---------------|------------------|
| **[FIX]** | Bug Fix | Correction d'un bug existant. |
| **[IMP]** | Improvement | Amélioration du code, optimisation, UX, performances, nettoyage léger sans modifier le comportement fonctionnel. |
| **[REF]** | Refactoring | Restructuration importante du code, déplacement ou suppression de code, sans ajout de fonctionnalité ni correction directe de bug. |
| **[NEW]** | Add | Ajout d'une nouvelle fonctionnalité. |
| **[DOC]** | Documentation | Modification de la documentation uniquement (README, commentaires, guides...). |
| **[TEST]** | Tests | Ajout, modification ou correction de tests unitaires ou d'intégration. |
| **[REV]** | Revert | Annulation d'un commit précédent. |
| **[I18N]** | Internationalization | Modification des traductions ou du module `i18n`. |
| **[PERF]** | Performance | Optimisation des performances sans modification fonctionnelle. |
| **[BOT]** | Automated Commit | Commit généré automatiquement (ex : mise à jour de dépendance, formatage). |

### Exemples

```
[FIX] logic: rejette les mots de passe de moins de 12 caractères
[IMP] i18n: simplifie la recherche de traduction
[REF] logic: sépare les vérifications du mot de passe en fonctions dédiées
[NEW] entity: ajoute la struct Password
[DOC] README: met à jour les instructions d'installation
[TEST] logic: ajoute un test de non-régression pour la vérification du chiffre
[I18N] ajoute les traductions anglaises
[BOT] met à jour Cargo.lock
```

---

## Processus de contribution

1. Créez une branche `feature/*` ou `fix/*` depuis `development`
2. Implémentez votre changement
3. Lancez `cargo build`, `cargo test` et `cargo clippy --all-targets --all-features` en local (mêmes vérifications que la CI)
4. Ouvrez une Pull Request vers `development`
5. Une fois la PR revue, approuvée et la CI au vert, elle est fusionnée dans `development`
6. `development` est régulièrement mergé vers `main` lors des releases
