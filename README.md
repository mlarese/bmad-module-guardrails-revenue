# Guardrails Revenue (`grv`)

A focused BMad module for hotel revenue management, pricing, forecasting, profit, and PMS/Channel Manager integrations. It keeps external publication behind explicit gates, dry-runs, approval, and rollback.

This is a focused BMad module in the [Guardrails](https://github.com/mlarese/bmad-module-guardrails)
bundle. It keeps the same behavior and shared memory while installing only the figures and
workflows for the revenue area.

> **Generated.** This repository is produced by `tools/build_modules.py` in the
> [bmad-module-guardrails](https://github.com/mlarese/bmad-module-guardrails) repository.
> Make changes there and regenerate; local changes here will be overwritten.

## Agents

| Agent | Role | Skill | Focus |
| ----- | ---- | ----- | ----- |
| 📈 Rhea | Revenue Management Strategist | `grl-agent-revenue` | Occupancy, ADR, RevPAR, TRevPAR, NRevPAR, GOPPAR, MUP, MOL, pickup, forecasting, pricing, PMS, and Channel Manager. |

## Skills and workflows

| Skill | Purpose |
| ----- | ------- |
| `grv-profile` | Project profile | Collects the project context shared by every installed figure. |
| `grv-board` | Multidisciplinary review | Convenes the relevant figures on one artifact and returns a review summary or release verdict. |
| `grl-revenue-audit` | Revenue data and pricing audit | Produces a read-only audit of exports, data quality, KPIs, demand, and the economic floor. |
| `grl-revenue-plan` | Revenue planning | Builds pricing, demand, and profit scenarios while separating the economic floor, market, and forecast. |
| `grl-revenue-preflight` | PMS and Channel Manager preflight | Checks contract, mapping, dry-run, response, reconciliation, idempotency, and rollback before transmission. |
| `grl-automation` | Controlled automation | Routes work from read-only checks through dry-run to observable execution, with explicit approvals and rollback. |

## Installation

```
bmad install grv
```

As a first step, run `grv-profile`. It collects the project profile — sector, data,
market, stack, and criticality — so each figure can calibrate its review. Without a profile,
the default remains `normal` and the figures start without context.

## Shared memory

The profile lives in `{project-root}/_bmad/memory/grl-shared/project-profile.md`, together
with `decisions.md` and `accepted-risks.md`. All Guardrails modules use the same path, so two
installed modules still share one profile.

## Using it with the bundle

This module installs skills with **the same names** as the `grl` bundle — `grl-agent-revenue`
is identical in both. Do not install the full bundle and thematic modules in the same project:
choose the complete bundle, or only the thematic modules you need.

## License

MIT.
