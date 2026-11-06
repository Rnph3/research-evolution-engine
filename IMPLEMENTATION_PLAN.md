# Implementation Plan, R001 Research Protocol, and Acceptance Gates

**Version:** v0.1 · **Status:** future execution plan · **Date:** 2026-11-06

## 1. Engineering outcome and scope

**First release target:** one **real** end-to-end computational research cycle that terminates with an evidence-grounded verdict and a reproducibility package, without live transactions or unauthorized external actions.

Not required for the first release: 20-agent swarms, distributed infrastructure, production dashboards, novel scientific breakthroughs, autonomous publication, GPUs or physical laboratory control.

### Definition of done (engineering)

- Research question and measurable primary metric defined before execution.
- At least three hypotheses proposed; a skeptical critique and baseline are recorded.
- A real dataset is downloaded or supplied with manifest and lawful use identified.
- Real code runs in a controlled environment; the evaluator is separate and frozen.
- An out-of-sample or appropriately independent test is executed, or limitation is explicitly recorded.
- `SUPPORTED_WITH_LIMITATIONS`, `REFUTED`, `INCONCLUSIVE` or `BLOCKED` verdict is attached to evidence.
- Reports, code hashes, logs, artifacts and evaluator version are saved.
- Negative tests, restart tests and budget enforcement are demonstrated.

The code could operate correctly while a given hypothesis is refuted. That is a successful **research engine** demonstration, not a positive research finding.

## 2. First benchmark: R001 — Market Microstructure Discovery

**Research question:** Can observable cross-venue or intra-venue cryptocurrency price discrepancies be predicted *ex ante* from available data, and do they remain robust after realistic transaction costs and verification outside discovery data?

**Scope:** public/authorized historical market data only; no private account data, keys, live orders, capital deployment or trading automations.

**Candidate mechanism families (hypotheses, not established facts):**

| Hypothesis | Falsifier / challenge |
| --- | --- |
| H1: Price dislocations predict short-term convergence under certain liquidity regimes | No positive effect on chronological holdout after costs |
| H2: Order-book imbalance provides incremental signal beyond a naive baseline | Equal or worse performance vs baseline under identical access and latency |
| H3: Dislocations are mostly measurement artifacts, asynchronous timestamps or illiquid quotes | After timestamp alignment and execution simulation, claimed edge disappears |
| H4 (optional): Cross-venue lead-lag depends on volatility regime | Regime interaction disappears in pre-registered unseen segments |

### Evidence and sampling

- **Discovery phase:** curate *up to 30 examples* to map mechanisms and test instrumentation. Selection must log why each case was included.
- **Statistical testing phase:** use a separately defined continuous historical time span or representative event universe. Thirty hand-picked wins are **not** evidence of profitability.
- Preserve both positive and negative occurrences; annotate original venue, symbol, timestamps, available order book depth, fee tier and data limitations.
- Source access, licensing, rate limits, timestamps, missing data and reproducible downloads must be verified before making empirical claims.

### Minimum frozen evaluation contract

| Dimension | Contract to lock before final test |
| --- | --- |
| Prediction time | All features available at or before decision timestamp; document latency |
| Target | Pre-specified spread convergence / net return horizon; avoid post-hoc target changes |
| Primary metric | One pre-registered out-of-sample metric, e.g., mean net return per eligible event after all modeled costs |
| Baseline | No-trade plus a simple fixed-rule reference; include equal risk exposure where meaningful |
| Fees and friction | Trading fees, spread, slippage, latency, fill uncertainty, depth and partial fills |
| Time split | Chronological discovery/training → validation → untouched final test |
| Significance | Effect size, confidence intervals/uncertainty, number of events and multiple-testing limitations |
| Negative controls | Timestamp shuffle, symbol/time placebo or cost perturbation as applicable |
| Robustness | Subperiods, regimes, venues, sensitivity to cost/latency assumptions |
| Stop conditions | Missing reliable prices, evaluator tampering, unauthorized action, budget breach, invalid split |

**Rule:** repeated optimization on the final test data invalidates its status as a holdout; reopen the protocol and obtain new untouched data.

### Acceptable research verdicts

- `SUPPORTED_WITH_LIMITATIONS`: preliminary evidence under explicitly listed tested assumptions; not a profit guarantee.
- `REFUTED`: evidence contradicts the tested hypothesis under the stated protocol.
- `INCONCLUSIVE`: data or statistical power insufficient, or results fragile.
- `BLOCKED`: technical, access, legal or safety constraint prevents a valid test.

## 3. Research and engineering gates

| Gate | Required evidence | Automatic handling of failure |
| --- | --- | --- |
| G0 — Goal | question, measurable metric, baseline intent, budget, stop rules | return to specification |
| G1 — Provenance | sources exist, retrieval and license information, dataset hash | block unsupported data |
| G2 — Hypotheses | falsifiable alternatives, critiques, deduplication | revise or reject |
| G3 — Protocol | pre-registered evaluator, data splits, no leak, valid controls | no experiment execution until fixed |
| G4 — Execution | sandboxed run, code revision, manifest, complete logs | mark failed run; debug within limits |
| G5 — Independent validation | frozen scores, controls, uncertainty, replication where possible | refuted/inconclusive/blocked as applicable |
| G6 — Conclusion | evidence map, limitations, publication approval boundary | no unsupported report claim |

Pass/fail of **technical safety gates** is distinct from support/refutation of a scientific hypothesis.

## 4. Minimum automated safeguard tests (12)

| ID | Test | Expected result |
| --- | --- | --- |
| T01 | Same input/data/seed on deterministic fixture | stable result and provenance |
| T02 | Mutated raw data after manifest hash | rejected integrity mismatch |
| T03 | Source URL missing or fabricated citation | citation cannot become VERIFIED |
| T04 | Duplicate hypothesis with minor paraphrase | duplicates linked or flagged |
| T05 | Worker tries to edit frozen evaluator | blocked and audit event recorded |
| T06 | Experiment submitted without baseline | gate G3 rejects |
| T07 | Feature computed using future prices | leakage fixture rejected |
| T08 | Runtime killed and resumed at checkpoint | no duplicate completed run/side effects |
| T09 | Runtime cost/time budget exceeded | safe stop and recorded `BLOCKED` |
| T10 | Missing log or environment/seed metadata | reproducibility gate fails |
| T11 | Sandbox attempts unauthorized network / secret read | denied, alert logged |
| T12 | Report includes metric unsupported by evaluation | claim auditor rejects publication-ready status |

These are **tests to implement**, not test results already achieved.

## 5. 48-hour MVP target (ambitious, subject to revision)

| Time from start | Work | Gate/exit artifact |
| --- | --- | --- |
| 0–2 h | Inspect host, data terms and available APIs; freeze R001 goal and evaluator | environment report; G0 contract |
| 2–6 h | Bootstrap Python package, SQLite events, source manifest and real data ingestion | ingest run; source provenance G1 |
| 6–12 h | Create hypothesis generation/critique and basic experiment runner | hypotheses with falsifiers G2; runnable baseline |
| 12–20 h | Lock scorer and data split, implement independent evaluator and initial controls | G3 verified; real evaluation script |
| 20–30 h | Wire complete sequential cycle, record logs, support failure states and restart | technical E2E run G4 |
| 30–40 h | Execute T01–T12, address defects, rerun from clean state | test report; G5 evidence |
| 40–48 h | Generate reproducibility bundle, human audit, report and GitHub-ready update | G6 report; explicit limitations |

This is a **schedule**, not proof that steps or tests have been completed or will fit the stated hours. If real data is unavailable, run a separately labeled **synthetic engineering smoke test** and mark scientific validation `BLOCKED`.

## 6. 30-day staged expansion

| Period | Primary focus | Measured deliverables |
| --- | --- | --- |
| Week 1 | Reliable research core | first real loop, provenance, test fixtures, evaluator independence, operator review |
| Week 2 | Replication and domain-adapter API | rerun R001 on new time window; a second **computational** domain adapter with independent benchmark |
| Week 3 | Controlled evolution | bounded search tree, candidate DB, pairwise hypothesis tournament, cost and novelty accounting |
| Week 4 | Operational reliability | scheduled internal research runs, resume/abort, artifact diff, human approvals, systematic failure review |

**Promotion from MVP to parallel swarms is gated** by correct reproducibility, stable failure handling, measured costs and evaluator isolation.

## 7. Resource and security budgets

Recommended initial limits (adjust after measurement; **not estimated actual price**):

- Maximum **$10** externally billed LLM/API usage per run unless approved.
- One active primary experiment worker initially; explicit worker count if parallelized later.
- Per-job execution deadline, CPU quota, RAM quota, disk quota and process limit.
- Explicit API allowlist for ingestion; generated-code experiment container has **no outbound network** by default.
- Local storage retention, hash verification and backups; commit only approved/non-sensitive artifacts.
- No API key, wallet private key, exchange trading credential, unlicensed raw data or personal information in Git.
- User confirmation before any public publish, push, external write or live financial action.

## 8. Acceptance and handoff checklist

- [ ] Actual device/environment inventory recorded.
- [ ] R001 data license and manifest verified.
- [ ] Locked baseline, protocol and evaluator created.
- [ ] First full **real** R001 run reaches terminal verdict.
- [ ] All 12 safeguard tests run with recorded outcomes.
- [ ] Crash/restart and budget limits demonstrably work.
- [ ] Report can be regenerated from immutable artifacts.
- [ ] All limitations and negative results disclosed.
- [ ] Final human review authorizes any public posting.

No checkbox is prechecked because no implementation evidence is present in the source discussion.

## 9. Required report artifacts

```text
research/R001/
  RESEARCH_BRIEF.md
  SOURCES.jsonl
  HYPOTHESES.jsonl
  EVALUATION_CONTRACT.json
  dataset_manifest.json
  experiments/
  runs/
  evaluations/
  FINAL_REPORT.md
  REPRODUCE.md
```

Every result in `FINAL_REPORT.md` must cite an exact `run_id`, metric record, code commit and data manifest. No model-written number may be treated as measured without a matching artifact.

See [Architecture](ARCHITECTURE.md) and [Codex Directive](CODEX_DIRECTIVE.md).
