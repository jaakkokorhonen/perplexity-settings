# Changelog

All notable changes to the configuration are documented here. Dates are in ISO 8601 format.

## [Unreleased]

## 2026-06-28

### Added
- `CITE=inline` — cite sources inline at the point of each claim, not collected in a list at the end. Ensures claims stay anchored to their evidence throughout the response.
- `HEDGE=explicit` — state uncertainty explicitly ("evidence is limited", "this is contested", "no data available") rather than softening claims silently through word choice. Complements `BAYES P↑↓|E` and `EVIDENCE=label` by making the confidence level of each claim visible.
- `VERIFY_BEFORE_REFUTE` — added to prevent the common LLM pattern of refuting a claim before checking whether it is actually true. Order is fixed: verify → judge, never judge → verify.
- `SOURCES=global; SEARCH_LANG={EN,orig}; GEO=unrestricted` — added to prevent Finnish-language queries from being restricted to Finnish sources regardless of topic scope.
- `QUOTE_LANG={orig,ANS_lang}` — `ANS_lang` replaces hardcoded `FI` to make the profile portable across languages.
- `READ(Q)->interp_BAYES(Q|history)` — added to instruct the model to interpret each question probabilistically, conditioned on conversation history.
- GitHub Pages support (`_config.yml`, Jekyll front matter).
- `CONTRIBUTING.md` — contribution instructions.
- `CHANGELOG.md` — this file.

### Changed
- `LANG=FI*` → `LANG=user*` — profile now responds in the user's query language automatically instead of hardcoding Finnish.
- `FMT=structured` + separate `QUOTE=max` + `QUOTE_LANG={orig,FI}` → `FMT=structured+quotes(orig+FI)` — consolidated into one parameter.
- Theme switched from `jekyll-theme-cayman` to `jekyll-theme-minimal`.
- README restructured: added Source and search scope section, Verification discipline section, updated Purpose section.

## 2026-06-09

### Added
- `READ(Q)->interp_BAYES(Q|history)` — first version: instruct model to read questions with Bayesian logic to answer the most likely intended question.

## 2026-06-06

### Added
- Initial configuration published.
- `cognitive_fallacies.csv` — structured list of named cognitive fallacies for use as prompt attachment.
- Core directives: `LANG=FI*`, `ANTI-ANTHRO`, `SEM≠PRAG≠LAW`, `BAYES P↑↓|E`, `OCCAM`, `HUME`, `GRICE=>hypothesis`, `GT`, `CAUSAL`, `NO-fallacies`, and others.
