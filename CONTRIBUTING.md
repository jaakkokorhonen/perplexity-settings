# Contributing

Contributions are welcome. This project uses GitHub pull requests.

## How to propose a change

The update path depends on which artifact you are changing.

### Prompt logic (`custom-instructions.md` and `README.md`)

1. **Open an issue first** if you want to discuss a new directive or a change to an existing one before writing anything. This avoids wasted effort if the direction doesn't fit.
2. **Fork the repository** and create a branch from `main`.
3. **Make your changes:**
   - Update the directive in `custom-instructions.md`.
   - Update the corresponding human-readable section in `README.md`.
   - Add an entry to `CHANGELOG.md` under `[Unreleased]` for significant changes (new directives, removals, behavioral changes). Trivial wording fixes do not require a changelog entry; a descriptive commit message is sufficient.
4. **Open a pull request** against `main` with a clear title and a short explanation of what the directive does and why it helps.

### Dataset changes (`cognitive_fallacies.csv`)

The CSV is a standalone machine-readable dataset. Changes to it do not require updating `custom-instructions.md` or `README.md` unless a fallacy is being added to or removed from the human-readable Cognitive Fallacies section of the README as well. Open a PR with the CSV change and describe what was added, corrected, or removed.

### Process or documentation changes (CONTRIBUTING.md, CONVENTIONS.md, README structure)

Open a PR with the changed file(s). A changelog entry is not required for process-only changes.

## Scope

This profile is intentionally compact. Proposals that add significant length without clear analytical benefit are unlikely to be merged. Prefer consolidating existing directives over adding new ones.

## License

By contributing, you agree that your contributions will be licensed under [CC BY 4.0](license.md).
