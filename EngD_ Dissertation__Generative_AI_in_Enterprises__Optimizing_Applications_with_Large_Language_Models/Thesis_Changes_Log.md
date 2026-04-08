# Thesis Revision — Changes Log

**Thesis:** *Generative AI in Enterprises: Optimizing Applications with Large Language Models*
**Author:** Donghao Huang

---

## Change 1 — Updated publications list and added Research Progression figure (Chapter 1)

**Date:** 2026-04-07
**Reviewer points:** #1 (Highlight most focused work), #1c (Add a "Research Progression" figure)
**Files modified:** `Chapter_1_Introduction.tex`, `main.tex`

**What changed:**

*Publications list:*
- Replaced EdgeAgent as a standalone publication entry with **Paper 9** — *Beyond Task Success: Measuring Workflow Fidelity in LLM-Based Agentic Payment Systems* (PAKDD 2026 Workshops, Accepted). This ASR paper now serves as the culminating paper in the Ch 4 multi-agent reliability thread.
- Added **Paper 15** — *Entity Matching with LLMs at Scale: Accuracy, Cost, and Reasoning Effects* (PAKDD 2026 Workshops, Accepted) to Ch 5 (Enterprise Deployment), providing cross-domain validation of accuracy–cost–reasoning trade-offs.
- Total publication count updated from 16 to 17 (ASR replaces EdgeAgent = net 0; Entity Matching added = +1).
- Publications mapping table updated to reflect Papers 4–9 (Ch 4) and Papers 10–17 (Ch 5).

*Research Progression figure:*
- Added TikZ figure (`fig:research_progression`) between the publications mapping table and the Research Contributions section, wrapped in `\resizebox{\textwidth}{!}` for proper fit.
- Added inline reference: "Figure~\ref{fig:research_progression} illustrates how these papers build on each other within and across the three research pillars."
- The figure is a timeline-based flow diagram showing all 17 papers arranged chronologically (2024–2026) and grouped by pillar:
  - **Pillar 1 (blue):** P1, P2 → P3 (RAP metric builds on RAG evaluations)
  - **Pillar 2 (red):** P4 → P5 (error taxonomy), P4 → P8 → P9 (Invoice → HMASP → ASR); P6 → P7 (Judge → CMAS4G2)
  - **Pillar 3 (teal):** P10 → P11 → P14 (edge → reasoning → task complexity); P13 → P14; P14 → P15 (entity matching); P12, P16, P17 as standalone application papers
- Three cross-pillar dashed arrows show:
  - P3 (RAP) → P4: quality metrics inform agentic output evaluation
  - P10 (Edge) → P4: edge deployment benchmarking (Ch 5) directly informed the edge-deployed invoice reconciliation system (Ch 4)
  - P14 (Task Complexity) → P7: reasoning effectiveness findings — P14 shows reasoning helps complex tasks but hurts simple ones; P7 (CMAS4G2) validates this in agentic context where structured reasoning enables gains for small models but excessive depth causes catastrophic degradation through context exhaustion
- Added `\usetikzlibrary{arrows.meta,positioning,fit,backgrounds,calc,decorations.pathreplacing}` to `main.tex` preamble.

---

## Change 2 — Added "Research Journey" discussion subsection (Chapter 1)

**Date:** 2026-04-07
**Reviewer points:** #1a (Expand core threads with deeper discussion), #4 (Stronger cross-chapter linkage)
**Files modified:** `Chapter_1_Introduction.tex`

**What changed:**

- Inserted new `\subsection{Research Journey: From Open-Weight LLMs to Enterprise AI Systems}` between the Research Progression figure and the Research Contributions section.
- Three `\paragraph` phases narrating the full research arc:
  - **Phase 1 — Securing Enterprise LLM Adoption through RAG (2023–2024):** Security motivation at Mastercard → open-weight LLM evaluation (Llama 2, Orca-2) → RAG as first enterprise pattern → RAP metric and ReDA algorithm (Paper 3) adopted in MAP production.
  - **Phase 2 — Pivoting to Agentic AI and Edge Deployment (2024–2026):** MAP transitions to commercialisation → edge feasibility confirmed by Paper 10 (14B on 16 GB GPU) → three progressive agentic use cases: invoice reconciliation (Papers 4 & 5), acceptance testing (Papers 6 & 7), payment processing (Papers 8 & 9) → cross-pillar insight flow → Agentic Evaluation & Optimisation initiative.
  - **Phase 3 — Reasoning, Fine-Tuning, and Cross-Domain Applications (2025–2026):** Few-shot prompting strengths (Paper 13: DeepSeek-R1 99.31% with 5 shots; Paper 12: Qwen2.5-72B surpasses GPT-4o with 10 shots) and scalability limitations (Paper 12: models unable to complete at higher shot counts due to compute cost) → fine-tuning addresses both reliability and efficiency (VCR 1.17% → 100% in 0.2 epochs, Paper 12) → reasoning model trade-offs across 504 configurations (Papers 11–14) → task-complexity hypothesis → cross-domain validation (Papers 12, 16, 17) → Paper 15 bridges to GAIME production.
- Explains all three cross-pillar arrows from the Research Progression figure: quality metrics (P3→P4), edge deployment (P10→P4), reasoning effectiveness (P14→P7).
- GAIME paragraph: describes Generative AI Merchant Enrichment product; documents two-stage optimisation strategy (frontier models refine prompts → best prompt used to generate LoRA/QLoRA fine-tuning data for sub-4B models); notes early results with 0.8B-parameter models approaching accuracy of much larger models; framed as ongoing work.

---

## Change 3 — Updated Research Contributions: enhanced ASR metric and added Entity Matching finding (Chapter 1)

**Date:** 2026-04-07
**Reviewer points:** #1a (Expand core threads with deeper discussion), #2 (Clarify theoretical contributions)
**Files modified:** `Chapter_1_Introduction.tex`

**What changed:**

*ASR metric (Novel Evaluation Metrics, item 4):*
- Expanded with full formal definition: transition multisets $B_E$, $B_O$; explicit TR and TP formulas alongside ASR $F_1$.
- Added quantitative evidence from the ASR paper: 18 LLMs, 90,000 task instances (5 repeats per model–scenario pair).
- Documented the specific finding: 7 of 8 models skip the CPA-mediated confirmation checkpoint during T3 (payment checkout), with ASR gaps of 0.01–6.7% despite near-perfect TSR and HF1.
- Explained root cause: for unambiguous payment intents, models execute 9 hops instead of expected 11 (TR = 80%, TP = 100%, ASR = 88.9% per affected sample).
- Added PCI-DSS regulatory significance.
- Added ASR-guided system engineering result: +24.2 pp average TSR improvement across 11 models.

*Entity Matching finding (Empirical Findings, new item):*
- Added "Reasoning Effort Has Opposite Effects Across Model Families for Entity Matching" based on Paper 15.
- Key results: 46 model configurations across 8 ER benchmark datasets; low reasoning optimal for GPT-5 (93.14 F1 at $6.25), high reasoning critical for open-weight models (GPT-OSS:120b: 90.11→92.10 F1), asymmetric thinking effects for Claude models (+10.13 F1 for Sonnet 4.5, −0.25 for Opus 4.5).
- Open-weight competitiveness: GPT-OSS:120b (92.10 F1) outperforms GPT-4.1 (90.36) and GPT-4o (89.58) at 20× lower cost.
- Pareto frontier analysis with budget tiers: ultra-budget (<$0.10) achieves 87–89 F1; diminishing returns beyond $3.

---

## Change 4 — Enhanced Industry Impact subsection (Chapter 1)

**Date:** 2026-04-07
**Reviewer points:** #1a (Expand core threads with deeper discussion), #2 (Clarify theoretical contributions)
**Files modified:** `Chapter_1_Introduction.tex`

**What changed:**

- Expanded `\subsection{Industry Impact}` from one generic paragraph to two substantive paragraphs.
- **Paragraph 1 — Production deployments:** RAP/ReDA deployed in MAP as primary output-quality gate; Paper 15 accuracy–cost–reasoning trade-offs informing GAIME model selection, with ongoing LoRA/QLoRA fine-tuning of sub-4B models; ASR exposing compliance-relevant workflow deviations for agentic payments (Agent Pay), with +24.2 pp TSR improvement via ASR-guided engineering.
- **Paragraph 2 — Three broader impact themes:** (1) open-weight competitiveness across all three pillars (Orca-2 for RAG, GPT-OSS:120b at 20× lower cost for entity matching, Qwen2.5:32b matching GPT-4.1 on HMASP); (2) edge deployment viability on $5K–$10K consumer GPUs with up to 21× platform speedups; (3) seven complementary metrics (RAP, VCR, ECR@1, ASR, RI, TCR, CPS) plus cost-performance Pareto analysis spanning 175× cost ranges.

---

## Change 5 — Added Section 5.4.3 (Entity Matching) and updated Chapters 1, 2, 5, 6

**Date:** 2026-04-07
**Reviewer points:** #1a (Expand core threads), #1b (Reframe supporting work as validation), #4 (Stronger cross-chapter linkage)
**Files modified:** `Chapter_5_Strategies.tex`, `Chapter_2_Literature_Review.tex`, `Chapter_6_Conclusions.tex`, `Chapter_1_Introduction.tex`, `references.bib`

**What changed:**

*Chapter 5 — New Section 5.4.3 "Entity Matching with LLMs at Scale":*
- Full subsection with Motivation, Background (ComEM framework), Experimental Setup, and Results subsubsections.
- Covers: 46 model configurations across 8 pyJedAI benchmark datasets; ComEM two-stage pipeline (Flan-T5-XL ranking + LLM selection); 4 model categories (OpenAI, Anthropic, open-weight local, open-weight API).
- Results table (Top 15 of 46) with F1, Precision, Recall, Cost.
- Three key findings: (1) open-weight models rival proprietary APIs (GPT-OSS:120b 92.10 F1, outperforming GPT-4.1/GPT-4o at 20× lower cost); (2) reasoning effort has family-dependent effects (low optimal for GPT-5, high critical for open-weight, asymmetric for Claude); (3) Pareto frontier with actionable budget tiers (ultra-budget <$0.10, value $0.46–$1.20, premium $3+).
- Links back to task-complexity findings (Section 5.3.3) and forward to GAIME production.
- Updated Chapter 5 Summary (Cross-Domain Application Patterns) with entity matching bullet.

*Chapter 2 — New Subsection "Entity Matching and Resolution":*
- Added under Section 2.7 (Sentiment Analysis and Cross-Domain Applications), after Sports Predictive Analytics.
- Covers: blocking-and-matching pipeline, traditional approaches (rule-based, distance-based, deep learning), pre-trained LM advances, LLM zero-shot/few-shot paradigms, ComEM framework.
- Identifies research gap: impact of configurable reasoning effort on EM unexplored.
- Added "Entity Matching at Scale" as new gap item #6 in Section 2.8.3 (Gaps in Enterprise Deployment).

*Chapter 6 — Conclusions updates:*
- Added entity matching contribution to Section 6.1.3 (Enterprise Deployment Contributions).
- Added GPT-OSS:120b entity matching result to Finding 1 (Open-Source Viability).
- Extended Finding 3 (Task Complexity) with family-dependent reasoning effects from entity matching.

*Chapter 1 — Structure of Dissertation:*
- Updated Chapter 5 description to mention entity matching evaluation (46 configurations, 8 datasets, family-dependent reasoning, Pareto guidance).

*References:*
- Added 15 entity matching references from the paper's bibliography (wang2025match, fellegi1969theory, getoor2012entity, papadakis2021blocking, binette2022almost, benjelloun2009swoosh, bilenko2003adaptive, li2015rule, mudgal2018deep, barlaug2021neural, li2020deep, tu2023unicorn, narayan2022can, peeters2023using, peeters2025entity, fan2024cost).

---

## Pending Changes

| Reviewer Point | Description | Status |
|----------------|-------------|--------|
| #1a | Expand core threads with 1–2 pages of deeper discussion | **Done** (Research Journey + Entity Matching section + Industry Impact) |
| #1b | Reframe supporting work as "validation" | **Partially done** (Entity matching validates cross-domain reasoning findings) |
| #1c | Add Research Progression figure | **Done** |
| #2 | Clarify theoretical contributions (Ch 6) | **Partially done** (Entity matching added to contributions and findings) |
| #3 | More cautious generalizability claims | Not started |
| #4 | Stronger cross-chapter linkage | **Done** (Research Journey + entity matching links Ch 2↔5↔6↔1) |
