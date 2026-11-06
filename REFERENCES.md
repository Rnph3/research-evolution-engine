# Primary References and Provenance Register

**Compiled:** 2026-11-06. These are public project materials for architectural understanding. Links do not establish that this repository contains the referenced implementations or that any empirical result has been independently replicated.

| ID | Source | What it supports | Access / caution |
| --- | --- | --- | --- |
| REF-01 | [Google DeepMind — Co-Scientist](https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/) | Supervisor; generate, reflect, rank, proximity, evolve and meta-review | Published description; not full public code of proprietary runtime |
| REF-02 | [Google Cloud — Co-Scientist agent](https://docs.cloud.google.com/gemini/enterprise/docs/co-scientist) | Product description and access limitations | Restricted product access may apply |
| REF-03 | [Sakana AI Scientist v1](https://github.com/SakanaAI/AI-Scientist) | End-to-end automated experimental research lineage | Follow repository license and execution warnings |
| REF-04 | [Sakana AI Scientist v2](https://github.com/SakanaAI/AI-Scientist-v2) | Experiment manager and progressive agentic tree search | Generated-code risk; setup and GPU assumptions must be checked |
| REF-05 | [Google Cloud — AlphaEvolve architecture](https://docs.cloud.google.com/gemini/enterprise/docs/alphaevolve/developer-guide/architecture-and-workflows) | LLM ensemble, candidate program database, prompt sampler, evaluator responsibility | A use-case-specific evaluator is required |
| REF-06 | [FutureHouse — Robin research](https://www.futurehouse.org/research/demonstrating-end-to-end-scientific-discovery-with-robin-a-multi-agent-system) | Biological discovery, strategy, experimental analysis and follow-ups | Physical experiments and outcomes are not reproduced here |
| REF-07 | [FutureHouse — Robin code](https://github.com/Future-House/robin) | Public implementation and components | Confirm current repo license and prerequisites before reuse |
| REF-08 | [Sakana — The Agentic Scientist (Oct 2026)](https://pub.sakana.ai/agentic-scientist/) | Coding agent orchestration, evaluators, rubrics, ablations and evidence maps | Researchers explicitly check claims and remain responsible for conclusions |
| REF-09 | [Karpathy — autoresearch](https://github.com/karpathy/autoresearch) | Constrained editable surface, fixed evaluation budget and metric | Original training repo targets a compatible NVIDIA GPU |
| REF-10 | [LangGraph — checkpoints](https://docs.langchain.com/oss/python/langgraph/persistence) | State persistence, checkpoint strategy and durable memory | Runtime needs explicit configuration |
| REF-11 | [LangGraph — human interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts) | Approval gates, pause and resume semantics | Resumed node can rerun code; use idempotent operations |

## Evidence hierarchy

1. **Independent experimental artifact** — observed run, frozen metric, source/hash and independent validator.
2. **Official project paper / source code** — evidence of what the reference *claims and makes public*, not a reproduced result.
3. **Project-authored design** — an implementation hypothesis, not evidence of execution.
4. **LLM-generated synthesis** — useful for hypotheses, never an empirical measurement on its own.

## Usage and citation

Do not copy licensed source code without reviewing its current license. If derivative code is eventually included, retain required notices and scientific/AI-attribution disclosures. For externally submitted science, document human review and model contributions under the publication venue's rules.
