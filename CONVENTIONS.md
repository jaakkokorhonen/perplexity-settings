# Conventions

This document defines the contribution conventions for this repository. All contributors and AI assistants working on this repository must follow these rules. The rules apply to every file type: `.md`, `.csv`, `.yml`, configuration files, and binary assets alike.

## Pull Request Requirement

**Every change to every file goes through a pull request.** No direct commits to `main` are permitted, including documentation edits, typo fixes, and single-line changes to `.md` files. The rationale is traceability: `main` must reflect a reviewed, intentional state at all times, and the PR diff is the canonical record of what changed and why.

The only permitted exception is an emergency hotfix that fixes a broken link or a build-breaking error. Even then, the commit message must include `[hotfix]` and a follow-up issue must be opened within 24 hours documenting the bypass.

## Branch Naming

Branch names follow a short, hyphenated slug describing the change. No ticket numbers, no personal identifiers, no dates.

```
<type>/<short-slug>
```

Examples:

- `docs/update-criteria-section`
- `fix/single-line-criteria-truncation`
- `feat/add-test-hypotheses`
- `perf/position-bias-reorder`
- `chore/update-ga4-id`

Valid types: `feat`, `fix`, `docs`, `perf`, `refactor`, `chore`, `test`.

## Commit Message Format

Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/) v1.0.0.

```
<type>(<optional scope>): <short description in imperative mood>

[optional body]

[optional footer]
```

The short description must be in English, lowercase after the colon, and under 72 characters. It must describe what the commit does, not what the file is. `Update README.md` is not a valid message. `docs: update CRITERIA human-readable section` is valid.

### Type Reference

| Type | When to use |
|---|---|
| `feat` | A new directive, section, or rule that adds behavior |
| `fix` | Correcting an error, inconsistency, or broken link |
| `docs` | Documentation changes with no behavioral effect on the configuration |
| `perf` | Compression or reordering that improves attention-budget efficiency |
| `refactor` | Restructuring without adding or removing behavior |
| `chore` | Dependency updates, asset replacements, build config |
| `test` | Adding or updating test hypotheses or CI fixtures |

### Examples of Valid Commit Messages

```
docs: update CRITERIA human-readable section to reflect conditional exposure
perf: front-load SIGNAL_FIRST, VERIFY_BEFORE_REFUTE, CLAIM_BASELINE
fix: add missing clauses to single-line CRITERIA
feat: add H5 test hypothesis for Gricean intent attribution
refactor: split SUPPRESS into SUPPRESS_OUTPUT and SUPPRESS_ATTR
chore: update GA4 measurement ID
```

### Examples of Invalid Commit Messages

```
Update README.md          ← no type, describes the file not the change
fix stuff                 ← no type, not specific
WIP                       ← not a complete commit
minor changes             ← no type, not specific
```

## File Synchronization Rule

`custom-instructions.md` and `README.md` are a synchronized pair. A change to one almost always requires a change to the other. Specifically:

- Any directive added, removed, or reworded in `custom-instructions.md` requires a corresponding update to the human-readable section in `README.md`.
- Any change to section ordering in `custom-instructions.md` requires the same ordering in the README's human-readable interpretation.
- Single-line and multi-line versions in `README.md` must be semantically equivalent. If the single-line version must truncate for length, add a comment `(truncated — see multi-line for full form)` immediately after the truncated directive.
- The PR description must explicitly state whether the `README.md` / `custom-instructions.md` pair was kept in sync, or provide a reason why one was intentionally left unchanged.

## Section Header Consistency

Section headers in the machine-readable `# comment` lines inside `custom-instructions.md` must match the corresponding `###` heading in the README's human-readable interpretation section. Example: `# Criteria` in the config maps to `### Criteria` in the README. If a section is renamed, both must be renamed in the same commit.

## PR Description Requirements

Every PR description must answer three questions:

1. **What changed?** State the directive, section, or file modified.
2. **Why?** Name the theoretical basis, empirical finding, or observed deficiency that motivated the change.
3. **Sync status:** Did this change require updating both `custom-instructions.md` and `README.md`? If yes, confirm both were updated. If no, state why not.

For compression changes, the PR description must also state which equivalence criterion was used (Dung strong equivalence, SETAF kernel redundancy, ADF acceptance-condition merge, or MDL token count) and the before/after token count if measurable.

## What Not to Do

- Do not push directly to `main`, including for `.md` files, `_config.yml`, `cognitive_fallacies.csv`, or any binary asset.
- Do not use `Update README.md` or similarly generic commit messages.
- Do not change directive names in `custom-instructions.md` without updating the corresponding README section header in the same commit.
- Do not truncate the single-line version of a directive without marking it as truncated.
- Do not open a PR without a description that answers the three questions above.
- Do not merge a PR that leaves `custom-instructions.md` and `README.md` out of sync unless the PR description explicitly documents the reason.
