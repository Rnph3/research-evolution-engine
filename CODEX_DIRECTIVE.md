# CODEX DIRECTIVE — Research Evolution Engine v0.1

**Directive status:** READY FOR HANDOFF — **not executed**.  
**Read first:** [`README.md`](README.md), [`RESEARCH_STATE.md`](RESEARCH_STATE.md), [`ARCHITECTURE.md`](ARCHITECTURE.md), [`IMPLEMENTATION_PLAN.md`](IMPLEMENTATION_PLAN.md).

---

## Role and mission

You are the lead implementer of **Research Evolution Engine (REE)**, a local-first, evidence-grounded autonomous computational research system.

Implement the **minimum complete research vertical slice**, drawing design inspiration from the publicly documented mechanisms of Google AI Co-Scientist, Sakana AI Scientist-v2, Google AlphaEvolve, FutureHouse Robin, Sakana Agentic Scientist and Karpathy autoresearch.

**Do not claim** to reproduce proprietary implementations or exceed documented scientific capabilities. Favor a small working system with strong verification over a large nonfunctional swarm.

### Goal

A human supplies a measurable research question. The system discovers authentic evidence, generates multiple falsifiable hypotheses, critiques them, performs bounded computational tests, independently evaluates outputs, records results and either accepts a limited claim, rejects it, declares uncertainty or blocks execution with a concrete reason.

### Hardware / context

- Primary host: Mac mini with 24 GB memory (verify actual OS, Python, Docker and CPU at runtime).
- Secondary controller: MacBook Air M1 / mobile (initially optional, do not require remote connectivity).
- LLM inference: available cloud model API(s); verify credentials without exposing them.
- Local state: SQLite plus content-addressed artifacts; default operation must survive process restart.
- Preferred language: Python 3.12; orchestration candidate: LangGraph; tests: pytest.
- Isolation: Docker with network off for generated-code workers by default.
- Initial UI: CLI report and existing static HTML; dynamic Streamlit UI only if the E2E core already works.

## Non-negotiable principles

1. **Evidence is the source of truth.** Never invent an execution log, benchmark score, paper, URL, experiment or successful test.
2. **Keep the evaluator locked.** Generation agents may alter candidate programs, but not primary metrics, held-out data or acceptance thresholds after the protocol is fixed.
3. **Track lineage.** Every result ties back to a source manifest, code revision, execution environment, time, seed, evaluator and data split.
4. **Stop safely.** Reject or pause unapproved external writes, trading, publication, attempts to access secrets, scope creep and budget overruns.
5. **Bound costs and runtime.** Default external API budget $10 per research run, adjustable by human approval. Enforce per-job CPU/time/memory/disk limits.
6. **Make restart safe.** Use persistent checkpoints, idempotency keys and atomic artifact commits.
7. **Log negative results.** Rejected or uncertain hypotheses are not deleted and cannot be silently promoted.
8. **Do not make a swarm first.** One working sequential loop before adding speculative orchestration complexity.

## Phase 0 — Inspect and freeze scope

- Inspect project directory and local tool availability (do not assume installed dependencies).
- Audit any existing working code before writing replacements; reuse only when licensed and compatible.
- Check read-only access to public source/data APIs, applicable terms, timeframe and rate limits.
- Verify Python, Docker, file permissions and sandbox limits on host.
- Write `reports/ENVIRONMENT_INVENTORY.md` with actual findings.
- Define the R001 research contract before code generation, including primary metric, baseline, chronological split, costs, negative controls, stop rules and intended scientific claim boundary.
- Do not ask the user to provide data already accessible in the approved environment. If an essential credential or permission is missing, record a blocker and perform only an honestly labeled engineering smoke test.

## Phase 1 — Minimal repository and state machine

Recommended code layout (adapt only with documented reasoning):

```text
src/research_engine/
  __init__.py
  director/
  discovery/
  hypothesis/
  experiment/
  evaluation/
  evolution/
  memory/
  adapters/
  reporting/
  security/
configs/
research/R001/
tests/
reports/
artifacts/         # ignored by Git unless sanitized and approved
ui/
```

Implement first-class objects:

`ResearchGoal`, `Source`, `Hypothesis`, `Experiment`, `Run`, `Evaluation`, `Decision`, `Artifact`.

Implement explicit terminal states:

- `SUPPORTED_WITH_LIMITATIONS`
- `REFUTED`
- `INCONCLUSIVE`
- `BLOCKED`

Implement the internal stage transitions `DRAFT → EVIDENCE_READY → HYPOTHESES_READY → PROTOCOL_LOCKED → EXECUTED → EVALUATED → terminal`.

Persist to SQLite with an append-only JSONL event log, stable IDs and hashes. Never treat the LLM conversation as durable execution state.

## Phase 2 — Discovery and hypothesis arena

- Ingest authorized source references with provenance and content hashes.
- Search using official/public domain endpoints where possible; mark partial text clearly.
- Generate at least **three competing hypotheses** for R001, each with mechanism, falsifier, baseline and assumptions.
- Apply skeptical critique and duplication detection.
- Optionally use pairwise rankings for experiment priority; treat rankings as heuristics, not proof.
- Save all hypotheses, including rejected candidates, with reasons and source links.

## Phase 3 — Executable experiment and frozen evaluator

- Build an **independent** baseline; do not rely on a model asserting it exists.
- Lock one primary metric and holdout splitting logic before final testing.
- Enforce chronological boundaries and feature availability timestamps.
- Include fee, spread, latency, slippage, liquidity and partial-fill modeling if claiming executable financial performance.
- Run generated candidate code under restrictions: no secrets, no network by default, read-only data, non-root user, no Docker socket, resource/process limits, and no writable host mounts.
- Prevent prompt-injection instructions from fetched data or repos becoming authority over the controller.
- Separate `experiment` and `evaluation` trust zones.
- Add negative controls and cost/latency stress tests.

For R001, the first **30 cases are discovery cases only**, not an adequate sample for profitability claims. Define a broader, pre-specified event universe for out-of-sample evaluation.

## Phase 4 — Evaluation and bounded evolution

- Compute metrics from actual saved outputs and compare to the frozen baseline.
- Report uncertainty, sample size, invalid runs and reasons for exclusion.
- Archive all candidates and scores, including regressions and failures.
- Only accept a candidate improvement if the gate criteria allow it; never optimize repeatedly on final holdout.
- Allocate limited candidate experiments for one next cycle; do not add an unbounded agent search loop.
- Ensure that an inconclusive result produces an honest research report.

## Phase 5 — Test suite and reliability

Implement and run at least these test scenarios:

1. Deterministic fixture rerun.
2. Data-manifest tampering detection.
3. Unsupported citation rejection.
4. Duplicate hypothesis detection.
5. Unauthorized evaluator modification denied.
6. Missing baseline fails G3.
7. Future-data leakage fixture rejected.
8. Crash-and-restart idempotence.
9. API cost/time cap enforcement.
10. Missing reproducibility metadata fails gate.
11. Forbidden sandbox network/secret access denied.
12. Unsupported metric/report claim rejected.

Record tests that fail or cannot be exercised. **Do not mark tests as passed without running them**.

## Phase 6 — Real R001 end-to-end run

Target question:

> Can identifiable cryptocurrency market dislocations be detected in advance using lawful historical data, and do they survive realistic costs and time-based independent validation?

- Execute **simulation only**; never submit live trades or move funds.
- Prefer actual public datasets with explicit terms and provenance.
- If real data is not available, run a separately marked **synthetic engineering smoke test** and report the scientific benchmark as `BLOCKED`.
- Produce every real artifact: source manifest, hypothesis set, locked evaluator, run logs, metrics, negative controls, conclusions and limitations.
- Independently recompute selected reported metrics from stored files.

## Phase 7 — Deliverables and review

Provide:

- `README.md` updated with **actual** implementation status and **real** setup/run commands.
- `ARCHITECTURE.md` reflecting code, not only speculation.
- `RESEARCH_PROTOCOL.md` with immutable R001 evaluation contract.
- `SECURITY.md`, `EVALUATION.md` and `HANDOFF.md`.
- `src/`, `configs/`, `tests/`, `research/R001/`, `reports/`, and `ui/` (if implemented).
- `research/R001/FINAL_REPORT.md` and `research/R001/REPRODUCE.md`.
- An **exact command** to regenerate the demonstrated outcome, if and only if tested.

The final report must contain:

```text
1. Research objective and permitted scope
2. Source/data provenance and license notes
3. Competing hypotheses and counterarguments
4. Locked protocol, metrics and baseline
5. Code versions, environment, seed and execution transcript
6. Measured metrics, negative controls and uncertainty
7. Independent evaluation gate results G0–G6
8. Reproduction instructions
9. Supported/refuted/inconclusive/blocked verdict with limits
10. Open failures and next three evidence-based actions
```

### Acceptance gates

- [ ] One **real** R001 run terminates with honest recorded verdict.
- [ ] Code, evaluation and metadata are independently inspectable.
- [ ] Twelve safeguards are executed, with truthful pass/fail status.
- [ ] Restart does not duplicate completed external or local effects.
- [ ] Hard budget and runtime limits demonstrably operate.
- [ ] No unapproved external write, public push, financial transaction or publication occurs.
- [ ] Technical success and scientific validity are reported separately.

### Reporting convention

At each milestone, return:

`Implemented / Executed / Evidence paths / Tested / Failed / Blockers / Cost / Next 3 actions`.

Use exact observed paths, commit IDs and commands. If you cannot verify a fact, say `UNVERIFIED`. If a gate is blocked, stop safely and preserve completed work.

---

**Implementation order:** documentation audit → R001 locked contract → minimal discovery → candidate generation → sandbox execution → independent evaluation → evidence and report → reliability gates → optional evolution and multi-agent expansion.

**Publishing rule:** do not create GitHub repositories, push commits or publish reports without explicit user approval. This directive is a build handoff, not permission for external actions.
