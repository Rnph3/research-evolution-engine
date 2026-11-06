# Research State — Conversation-to-Repository Record

**Project:** Research Evolution Engine (REE)  
**Status as of:** 2026-11-06 (Asia/Seoul)  
**Lifecycle state:** `DESIGN / PRE-IMPLEMENTATION`  
**Record type:** faithful consolidation of the design discussion; **not** an engineering execution report.

## A. Original intent and final objective

The objective is to reconstruct the **publicly documented, reusable mechanisms** behind leading autonomous-research systems and compose them into a **working end-to-end research engine** on a personal computer and remote model APIs. It must perform real research operations rather than merely generate plausible text:

`research goal → evidence discovery → competing hypotheses → adversarial review → executable experiment → independent evaluation → iterative improvement → durable research output`

The end state is a **domain-adaptable researcher** with a reproducible audit trail: code, data, baseline, experimental variants, failure cases, evaluation, claims and supporting evidence. It is **not** an assertion that human-level science or frontier-lab capabilities have been reproduced.

## B. How the discussion progressed

| Stage | What was requested | What the discussion produced | Confirmed status |
| --- | --- | --- | --- |
| 1. Ecosystem inventory | Enumerate Google AI Co-Scientist-like systems | A broad taxonomy of autonomous scientists, scientific-discovery agents, experimental laboratories, research agents and orchestration frameworks | **Conceptual list**; not a benchmark of 111 independently verified products |
| 2. Core selection | Combine Google Co-Scientist, Sakana AI Scientist, AlphaEvolve, Robin | Extraction of complementary strengths: hypothesis tournaments, experimental tree search, program evolution, feedback from evidence and experiments | **Architecture hypothesis** |
| 3. Integrated operating model | Design a locally deployable E2E system | Research Director, Discovery, Hypothesis, Experiment, Evaluation, Evolution, Memory and output layers | **Design drafted** |
| 4. Engineering choices | Adapt design to personal infrastructure | Local-first Python, orchestration, SQLite, Docker isolation, swappable cloud models, Streamlit UI | **Proposed stack**, not compatibility-tested |
| 5. Scientific validity | Prevent agents from incorrectly declaring success | Seven validation gates, frozen metrics, baseline, held-out testing, provenance, reproducibility and publication approval | **Protocol drafted**, not implemented |
| 6. First demonstration | Pick a measurable research target | R001 market-microstructure study and 48-hour MVP / 30-day expansion plan | **Proposed benchmark**, not run |
| 7. Development handoff | Turn plan into agent instructions | Codex implementation directive and acceptance criteria | **Draft prepared**, no verified development execution |
| 8. Repository packaging | Remove project-specific branding and publish current state | Six standalone documents plus reference register and packaging | **Files prepared locally**; GitHub publication not yet verified |

The discussion established **what to build**. It did not produce evidence that the complete software system already exists.

## C. Decisions and confidence labels

Use three labels throughout the project:

- **SOURCE-VERIFIED:** explicitly described in cited official material, within its published scope.
- **DESIGN-DECIDED:** a deliberate project choice, not evidence that it works.
- **OPEN / UNVERIFIED:** needs tests, external validation, credentials or further investigation.

| ID | Decision / proposition | Label | Reason / next check |
| --- | --- | --- | --- |
| D-001 | Separate hypothesis generation from empirical evaluation | DESIGN-DECIDED | Prevent self-approval by model-generated prose |
| D-002 | Use six scientific functions in the top-level research loop | DESIGN-DECIDED | Domain-neutral composition of existing mechanisms |
| D-003 | Use eight implementation subsystems (director, discovery, hypothesis, experiment, evaluation, evolution, memory, UI) | DESIGN-DECIDED | Practical module boundaries; no need for eight concurrent services |
| D-004 | Start sequentially on a Mac mini with remote models | DESIGN-DECIDED | Reduce complexity and hardware dependence |
| D-005 | Use a frozen evaluator and held-out data in R001 | DESIGN-DECIDED | Required for meaningful out-of-sample claims |
| D-006 | Add bounded tree search only after a functioning vertical slice | DESIGN-DECIDED | Limit cost, failure surface and debugging time |
| D-007 | Record failed hypotheses as first-class research memory | DESIGN-DECIDED | Reduce repeated dead ends and selective reporting |
| D-008 | Require human approval for external writes and publishing | DESIGN-DECIDED | Safety and research accountability |
| D-009 | Treat R001 as simulation-only | DESIGN-DECIDED | Avoid live execution and unknown financial consequences |
| D-010 | 48-hour initial implementation and 30-day expansion | OPEN / UNVERIFIED | Planning targets; may require replanning |
| D-011 | Scientific validity of any R001 edge or strategy | OPEN / UNVERIFIED | Requires real data, tests and independent analysis |
| D-012 | Specific model/harness superiority | OPEN / UNVERIFIED | Compare on identical tasks, budget and metrics |

## D. Current deliverables: design versus execution

| Deliverable | Defined? | Implemented? | Independently tested? |
| --- | --- | --- | --- |
| Mission / non-goals | Yes | N/A | No external audit |
| Architecture diagram / module contracts | Yes, preliminary | No verified runtime | No |
| Research objects / persistence model | Yes, conceptual | No verified DB migration | No |
| Source discovery / citations | Yes, design | No pipeline execution evidence | No |
| Hypothesis competition | Yes, design | No working tournament evidence | No |
| Sandboxed experimentation | Yes, design | No sandbox test evidence | No |
| Fixed evaluator and G0–G6 | Yes, design | No gate runner evidence | No |
| R001 dataset and result | Protocol only | No real experiment evidence | No |
| Research dashboard | Static atlas included | No live backend | No |
| GitHub repository | Proposed name | Not created by this package | Not pushed |

## E. Known blockers and risks

1. **Evidence/data access:** authoritative market data completeness, exchange rules, historical coverage and timestamps remain unverified.
2. **Execution security:** generated code needs limits on network, files, processes, time and credentials; Docker alone is not a formal security proof.
3. **Evaluation integrity:** an evolving agent must not edit its own grading function or see hidden test answers.
4. **Scientific overclaiming:** apparent improvement can arise from leaks, multiple comparisons, survivorship selection or unrealistic costs.
5. **Hardware fit:** a Mac mini can orchestrate and run CPU experiments, but CUDA-oriented repos cannot be assumed to run unchanged.
6. **Operational durability:** crash/restart, idempotence and checkpoints are design targets until tested.
7. **Cost:** model usage, data-provider terms and storage need measured limits.
8. **Source licenses:** public research/code ≠ automatically unrestricted reuse.

## F. Next actions in execution order

1. Freeze **R001 evaluation contract**: benchmark question, time boundaries, metric, baseline, controls, limits and terminal verdicts.
2. Verify API/data access and create a **real data manifest**; if blocked, distinguish an engineering smoke test from scientific validation.
3. Build minimum sequential pipeline with immutable run identifiers and artifact hashes.
4. Run independent evaluator and intentionally corrupted inputs; exercise restart and budget limits.
5. Produce one evidence-linked report (positive, negative or inconclusive) that another person can reproduce.
6. Only then add hypothesis tournaments, branching evolution, parallel execution and additional domain adapters.

## G. Interpretation policy

- A documentation artifact proves a **design decision**, not a working system.
- A successful script execution proves **technical execution**, not scientific validity.
- A hold-out result is evidence only within its **dataset, hypothesis and evaluation protocol**.
- An inconclusive or negative result is a legitimate completed research cycle.
- A publication decision remains with the accountable human reviewer.

Related: [Architecture](ARCHITECTURE.md), [Plan](IMPLEMENTATION_PLAN.md), [Handoff](CODEX_DIRECTIVE.md), [Sources](REFERENCES.md).
