# Thesis Review — Response & Update Plan

**Thesis:** *Generative AI in Enterprises: Optimizing Applications with Large Language Models*
**Author:** Donghao Huang
**Date:** April 2026

---

## Reviewer Verdict

The reviewer confirms the thesis **meets the expected EngD standard** and is "a solid dissertation." All requested changes are **minor**. The four recommendations are addressed below, each with a concrete action plan.

---

## 1. Highlight Most Focused Work with More Content

**Reviewer comment:** *"The thesis covers a list of topics … This breadth is impressive. Suggests highlight most focused work with more contents."*

### Interpretation

The reviewer is not asking to remove topics — the breadth is acknowledged as a strength. Rather, the suggestion is to deepen coverage of the core contributions so that the most focused threads stand out from the supporting/application papers.

### Proposed actions

**a) Identify the "core spine" and expand it.** The three deepest research threads are:

| Thread | Key papers | Chapter |
|--------|-----------|---------|
| RAP metric & repetition control | Papers 1–3 (PAKDD Workshops, IEEE CAI, NAACL 2025) | Ch 3 |
| Multi-agent reliability (Invoice → HMASP → CMAS4G2 → ASR) | Papers 4–9 (ICDSAAI, ICAIBD, AAAI Workshops, PAKDD 2026) | Ch 4 |
| Reasoning effectiveness, task complexity & entity matching | Papers 10–17 incl. Paper 14 (PAKDD 2026) & Paper 15 Entity Matching (PAKDD 2026 Workshops) | Ch 5 |

For each of these three threads, add 1–2 pages of deeper discussion covering design rationale, ablation insights, failure cases, and lessons learned that go beyond what the published papers contain.

**b) Reframe supporting work as "validation."** For the papers that are more application-driven (translation, soccer betting, logical reasoning puzzles), add a brief framing paragraph at the start of each section explaining how they serve as cross-domain validation of the core metrics/strategies rather than standalone contributions.

**c) Add a "Research Progression" figure.** In Chapter 1, add a visual (e.g., a timeline or flow diagram) showing how the 17 papers build on each other — making the focused progression explicit rather than leaving it to the reader to reconstruct.

### Recently incorporated papers

Two new papers have been formally added to the dissertation publications list in the revised Chapter 1:

- **Paper 9** — *Beyond Task Success: Measuring Workflow Fidelity in LLM-Based Agentic Payment Systems* (PAKDD 2026 Workshops, Accepted) → introduces the ASR metric for trajectory-level workflow fidelity; replaces EdgeAgent as the culminating paper in the Ch 4 multi-agent reliability thread.
- **Paper 15** — *Entity Matching with LLMs at Scale: Accuracy, Cost, and Reasoning Effects* (PAKDD 2026 Workshops, Accepted) → cross-domain validation of accuracy–cost–reasoning trade-offs across 46 model configurations and 8 datasets; strengthens the Ch 5 enterprise deployment thread.

### Additional published paper available for strengthening (not currently in thesis)

- **ConvPayMAS** (AAMAS 2026 Demonstration, Accepted) — extends HMASP payments work with agent-to-agent protocols. Currently commented out in Chapter 1; could be cited in Ch 4 discussion if needed.

---

## 2. Clarify Theoretical Contributions Beyond Practical Optimization

**Reviewer comment:** *"The theoretical contributions should be clearer. It should go beyond practical optimization and evaluation."*

### Proposed actions

**a) Add a "Theoretical Contributions" subsection in Chapter 6 (Conclusions).** Frame the seven metrics (RAP, VCR, ECR@1, ASR, RI, TCR, CPS) as a unified **operational reliability theory** for enterprise LLM systems — they collectively formalize dimensions that traditional NLP evaluation ignores. Argue that this constitutes a theoretical contribution: a measurement framework where each metric captures a distinct failure mode invisible to accuracy alone.

**b) Formalize the Task-Complexity Hypothesis (Chapter 5).** The finding that reasoning effectiveness is systematically task-dependent (degradation on simple tasks, gains on complex ones) is already empirically validated across 504 configurations and 7 model families. Elevate this from an "empirical finding" to a formally stated hypothesis with boundary conditions, making the theoretical claim explicit.

**c) Articulate the "Architecture Over Scale" principle.** The repeated finding that smaller well-configured models outperform larger ones (DeepSeek-R1:32b > 70b; qwen3:8b > 14B/30B/32B) challenges the scaling-law orthodoxy. Frame this as a theoretical contribution about the interaction between architecture, quantization, and task structure.

**d) Frame the 12-category error taxonomy (Chapter 4) as a theoretical diagnostic framework.** Position it as a generalizable taxonomy for tool-invocation failure modes in agentic systems, not just an empirical observation from one system.

---

## 3. More Cautious Generalizability Claims

**Reviewer comment:** *"Claims about generalizability should be more cautious."*

### Proposed actions

**a) Audit all generalizability claims.** Systematically review Chapters 3–5 for language like "generalizes to," "broadly applicable," "any enterprise," etc. Add appropriate qualifiers.

**b) Add a "Threats to Validity" or "Limitations" subsection to each technical chapter (Chapters 3, 4, 5).** Each should explicitly state:

- **Domain scope:** which domains/tasks were tested vs. which are untested
- **Model scope:** which model families were evaluated and the risk of model-specific effects
- **Temporal scope:** models and benchmarks evolve rapidly; findings reflect a specific snapshot
- **Scale scope:** enterprise deployment at thousands of users/day was not tested

**c) Soften specific claims.** For example:

- "ASR generalizes to arbitrary agentic architectures including chains, trees, or complex DAGs" → "ASR is designed to be architecture-agnostic and could in principle extend to chains, trees, or DAGs, though empirical validation was conducted on HMASP's hierarchical payment workflows (Paper 9)"
- Claims about open-source competitiveness should note they apply to the specific benchmarks tested

---

## 4. Stronger Cross-Chapter Linkage and Integration

**Reviewer comment:** *"Stronger linkage and integration across chapters are needed."*

### Proposed actions

**a) Add explicit forward/backward references.** At the end of each chapter, add a short "Connections" paragraph linking to the next chapter. For example:

- Ch 3 → Ch 4: "The RAP metric's approach to output quality assessment directly informs the reliability evaluation of agentic outputs in Chapter 4, where multi-step workflows amplify quality issues."
- Ch 4 → Ch 5: "The edge deployment requirements discovered during invoice reconciliation (Ch 4) motivate the systematic hardware benchmarking in Chapter 5."
- Ch 5 → Ch 4: "The task-complexity hypothesis from Chapter 5 explains why reasoning configuration has such dramatic effects on CMAS4G2 performance in Chapter 4."

**b) Add a unifying "Integration" section in Chapter 6.** Create a subsection that explicitly synthesizes how findings from all three pillars combine — e.g., a practitioner choosing to deploy an agentic RAG system would use RAP (Ch 3) for output quality, ASR/ECR@1 (Ch 4) for reliability, and the edge deployment guidelines + task-complexity hypothesis (Ch 5) for infrastructure decisions.

**c) Add a cross-chapter metrics summary table.** A single table in Chapter 1 or Chapter 6 showing all seven metrics, which chapter introduces each, and how they relate to each other (complementary dimensions of the same operational reliability framework).


## Priority, Effort & Workflow

| Step | Reviewer Point | Est. Effort | Key Chapters | Rationale | Status |
|------|---------------|-------------|--------------|-----------|--------|
| 1 | Highlight focused work (#1) | 2–3 days | Ch 1, 3, 4, 5 | Expand core threads with integration framing already in place | |
| 2 | Clarify theoretical contributions (#2) | 1–2 days | Ch 1, 5, 6 | Requires the most careful writing | |
| 3 | Cautious generalizability (#3) | 1 day | Ch 3, 4, 5 | Audit and soften claims while re-reading the full text | |
| 4 | Cross-chapter linkage (#4) | 1 day | Ch 1, 3, 4, 5, 6 | Add connection paragraphs during the same re-read pass | |
| 5 | Final pass | 0.5 day | All | Re-read end-to-end for consistency and voice | |

**Total estimated effort: ~5–7 days of focused revision**
