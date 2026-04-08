# Thesis Revision — Changes Log

**Thesis:** *Generative AI in Enterprises: Optimizing Applications with Large Language Models*
**Author:** Donghao Huang

---

## Change 1 — Updated publications list and added Research Progression figure (Chapter 1)

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

---

## Change 2 — Added "Research Journey" discussion subsection (Chapter 1)

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

**Reviewer points:** #1a (Expand core threads with deeper discussion), #2 (Clarify theoretical contributions)
**Files modified:** `Chapter_1_Introduction.tex`

**What changed:**

- Expanded `\subsection{Industry Impact}` from one generic paragraph to two substantive paragraphs.
- **Paragraph 1 — Production deployments:** RAP/ReDA deployed in MAP as primary output-quality gate; Paper 15 accuracy–cost–reasoning trade-offs informing GAIME model selection, with ongoing LoRA/QLoRA fine-tuning of sub-4B models; ASR exposing compliance-relevant workflow deviations for agentic payments (Agent Pay), with +24.2 pp TSR improvement via ASR-guided engineering.
- **Paragraph 2 — Three broader impact themes:** (1) open-weight competitiveness across all three pillars (Orca-2 for RAG, GPT-OSS:120b at 20× lower cost for entity matching, Qwen2.5:32b matching GPT-4.1 on HMASP); (2) edge deployment viability on $5K–$10K consumer GPUs with up to 21× platform speedups; (3) seven complementary metrics (RAP, VCR, ECR@1, ASR, RI, TCR, CPS) plus cost-performance Pareto analysis spanning 175× cost ranges.

---

## Change 5 — Added Section 5.4.3 (Entity Matching) and updated Chapters 1, 2, 5, 6

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

---

## Change 6 — Replaced Section 4.8 (EdgeAgent) with ASR for Agentic Payment Systems

**Reviewer points:** #1a (Expand core threads), #2 (Clarify theoretical contributions), #4 (Stronger cross-chapter linkage)
**Files modified:** `Chapter_4_Agentic_AI.tex`, `Chapter_6_Conclusions.tex`, `main.tex`, `references.bib`

**What changed:**

*Section 4.8 — Complete replacement:*
- Removed the entire EdgeAgent / maritime annotation section (semi-automatic labeling pipeline, OAS-based ASR definition, Qwen model evaluation on maritime risk data, hardware benchmarking).
- Replaced with **"Agentic Success Rate: Measuring Workflow Fidelity in Multi-Agent Payment Systems"** based on the AI4DF paper~\cite{huang2026asr}, extended with deeper analysis from notebooks and the JAAMAS submission.
- New section structure:
  - **Motivation:** Why TSR and HF1 are insufficient for payment compliance (PCI-DSS auditability).
  - **Architecture Adaptations:** A2A protocol layer, UCP-compliant gateway (~85% compliance), multi-turn state-machine protocol replacing LangGraph interrupts, consolidated 3-level agent hierarchy (CPA → Supervisors → Workflows). Architecture diagram copied from JAAMAS paper to `figures/asr_architecture_diagram.pdf`.
  - **ASR Definition:** Transition (bigram)-based metric with Transition Recall (TR) and Transition Precision (TP), grounded in process-mining conformance checking. Replaces the old OAS/weighted-step definition.
  - **Expected Trajectories:** Table of per-scenario trajectories (T1–T4) with detailed T3 step-by-step purpose table.
  - **Experimental Setup:** 18 LLMs, 90,000 instances (5 repeats × 18 models × 1,000 data points × 4 scenarios), M3 Max with 4-bit quantization.
  - **Results:** System engineering effectiveness (+24.2 pp average TSR across 11 HMASP models); ASR reveals hidden workflow deviations (top 8 of 18 models table); root cause analysis of the T3 confirmation shortcut with step-by-step comparison table.
  - **Deep Dive — Per-Sample Deviation Analysis** (new, from notebooks 09/10): Hidden deviation rates (22–26% across models that exhibit the shortcut; `mistral-small3.2:24b` at 0%); input phrasing as primary trigger (imperative phrasings universally shortcutted, deliberative formulations never shortcutted).
  - **Discussion:** Regulatory implications (PCI-DSS), ASR as both evaluation metric and diagnostic signal, integration with 12-category error taxonomy and ECR@1.

*Chapter 4 introduction (lines 11–24):*
- Publication list item 6: "EdgeAgent Annotation Pipeline" → "Agentic Success Rate for Payment Systems" with updated citation keys (`huang2026asr`, `huang2026asrjournal`) and venue info (AI4DF 2026 accepted; JAAMAS under review).
- Chapter structure description: "payments and annotation domains" → "payment processing, introducing trajectory-level workflow fidelity evaluation."
- ASR description: "fine-grained evaluation of tool-calling precision" → "trajectory-level workflow fidelity by comparing observed and expected agent execution sequences."

*Chapter 4 summary (Section 4.10):*
- Bullet 6 rewritten for transition-based ASR framing with 18 LLMs / 90,000 instances.
- Cross-reference paragraphs updated: "LCS-based" → "transition (bigram) level"; model-size invariance sentence updated to reference Llama3.1:8b vs GPT-5.2 (removed JAAMAS-only qwen3.5-0.8b reference).
- Practical Deployment Guidelines: evaluation strategy updated for trajectory-level metrics.

*Chapter 6 — Conclusions:*
- "EdgeAgent Annotation Pipeline" contribution → "Agentic Success Rate (ASR)" with transition-level framing, 18 LLMs, 90,000 instances, "7 of 8 top models skip confirmation checkpoints."

---

## Change 7 — Incorporated ConvPayMAS into Chapter 4; enhanced Enterprise Eval Framework

**Reviewer points:** #1a (Expand core threads), #2 (Clarify theoretical contributions)
**Files modified:** `Chapter_4_Agentic_AI.tex`, `Chapter_6_Conclusions.tex`, `references.bib`

**What changed:**

*Chapter 4 — New Subsection "From Prototype to Production: ConvPayMAS" (Section 4.8.8, label `sec:convpaymas`):*
- Placed between the ASR Discussion subsection and Practical Deployment Guidelines.
- Based on the AAMAS 2026 demonstration paper~\cite{chua2026convpaymas} (collaborative paper; author is not first author).
- Architecture subsubsection: 3-agent ecosystem (ConvPayMAS server with CSA + 5 sub-agents, Shopper Agent, E-commerce Agent) communicating via A2A protocol; architecture diagram copied to `figures/ConvPayMAS_architecture.pdf`.
- Security and Protocol Design subsubsection: Full AP2 three-mandate verification (Intent, Cart, Payment mandates with HMAC-SHA256 and JWT hash chain); Card Data Security (AES-256-CBC, per-session keys, Luhn validation, Guardrail Agent for PCI/PII redaction); Patent-pending security features (described without disclosure).
- Payment Flow subsubsection: 4-phase transaction flow (Intent & Discovery → Selection & Payment Mandate → Session Creation → Payment Execution).
- Enterprise Agentic Evaluation and Optimization Framework subsubsection: Enhanced with 3-pillar structure (Tool Call Reliability grounded in 12-category error taxonomy, Workflow Fidelity operationalized through ASR, Cost Tracking extending LLM-as-Judge cost-performance analysis) and Evaluate → Diagnose → Optimize continuous improvement loop. Content informed by the enterprise deck (Agentic_Eval_Optimization_Enterprises_v1.2.pptx).

*Chapter 4 introduction:*
- Publication count: "six" → "six first-authored publications and one collaborative demonstration paper."
- ConvPayMAS added as item 7 in the publication enumeration.
- Chapter structure paragraph extended to mention Section~\ref{sec:convpaymas}.

*Chapter 4 summary and guidelines:*
- "six systems" → "seven systems" in Practical Deployment Guidelines and Summary.
- ConvPayMAS bullet added to the enumerated contributions list (item 7).

*Chapter 6 — Conclusions:*
- Removed duplicate ASR entry (item 3 with old definition: "tool-calling precision...qwen3:32b achieves 98%") that conflicted with the correct transition-based ASR entry (item 7). The old entry predated the Section 4.8 replacement in Change 6 and was never updated.

*Not changed (by design):*
- Chapter 1 publication list: ConvPayMAS deliberately NOT added to the 17 first-authored publications list, as the author is not first author on this paper. The ConvPayMAS entry remains commented out in Chapter 1. Paper numbering (P4–P9 for Ch 4, P10–P17 for Ch 5) and total count (17) unchanged.

---

## Change 8 — Cross-file consistency fixes (Chapters 4, 6, abstract)

**Reviewer points:** General consistency review
**Files modified:** `Chapter_6_Conclusions.tex`, `Chapter_4_Agentic_AI.tex`, `abstract.tex`

**What changed:**

*Chapter 6 — stale references from pre-Change-6 era:*
- "sixteen publications" → "seventeen publications" (lines 7 and 344), matching Chapter 1's count after Entity Matching was added in Change 5.
- Finding 1 (Open-Source Viability): removed stale EdgeAgent bullet "qwen3:32b matches GPT-4.1 quality (98% ASR, 83% F1) on annotation tasks" → replaced with "qwen2.5:32b achieves 100.0% ASR matching GPT-4.1 on payment workflows" to reflect the Section 4.8 replacement.
- Metrics summary table: ASR description "Tool-calling precision in workflows" → "Trajectory-level workflow fidelity" to match the transition-based definition.
- Finding 6: "six multi-agent systems" → "seven multi-agent systems" to include ConvPayMAS, consistent with Chapter 4's count.
- Concluding remarks paragraph: "sixteen publications" → "seventeen publications"; replaced "annotation pipelines (qwen3:32b matching GPT-4.1)" with "entity matching (GPT-OSS:120b outperforming GPT-4.1 at 20× lower cost)" and "payment workflow fidelity (qwen2.5:32b achieving 100.0% ASR matching GPT-4.1)."


---

## Change 10 — Updated ASR top-models table and highlighted open-weight dominance

**Date:** 2026-04-08
**Reviewer points:** #1a (Expand core threads), #2 (Clarify theoretical contributions)
**Files modified:** `Chapter_4_Agentic_AI.tex`, `Chapter_1_Introduction.tex`

**What changed:**

*Chapter 4 — ASR Results table (top 8 models):*
- Added Qwen3:14b to the top-8 table (T3 ASR: 99.7±0.3 / 99.8±0.2 / 99.6±0.3; Avg ASR: 99.9 / 99.9 / 99.9). Qwen3:14b was already among the 18 evaluated models but had not previously appeared in the top-8 ranking.
- Removed Llama3.1:8b from the top-8 table (now displaced to rank 9). It remains in the full deviation analysis table as that covers all 18 models.
- Added `\midrule` separator between the 6 open-weight models (ranks 1–6) and the 2 proprietary GPT models (ranks 7–8).
- Updated table caption: added "All six open-weight models outperform both proprietary GPT models on average ASR."

*Chapter 4 — Text surrounding the table:*
- Added bold callout before the table: "all six open-weight models in the top eight outperform both proprietary GPT models on average ASR."
- Updated ASR gap range from "0.01–6.7%" to "0.01–2.9%" (the maximum gap is now GPT-4.1's 1.6% T3 deviation rather than Llama3.1:8b's former 6.7%).

*Chapter 4 — Discussion subsection:*
- ASR gap range updated from "0.01–6.7%" to "0.01–2.9%."

*Chapter 4 — Summary (Section 4.10):*
- ASR bullet updated with open-weight dominance finding: "all six open-weight models outperform both proprietary GPT models on average ASR."
- Summary paragraph updated: replaced Llama3.1:8b reference with open-weight dominance statement; ASR gap range updated to 0.01–2.9%.

*Chapter 1 — Research Contributions:*
- ASR gap range updated from "0.01–6.7%" to "0.01–2.9%."

*Not changed (verified correct):*
- "18 LLMs" and "90,000 task instances" counts remain accurate — Qwen3:14b was already one of the 18 evaluated models.
- The full deviation analysis table in Chapter 4 still includes Llama3.1:8b (it covers all models, not just the top 8).

---

## Change 9 — Generalized error taxonomy terminology; repositioned ConvPayMAS as work-in-progress

**Date:** 2026-04-08
**Reviewer points:** #2 (Clarify theoretical contributions), #3 (More cautious generalizability claims)
**Files modified:** `Chapter_4_Agentic_AI.tex`, `Chapter_1_Introduction.tex`, `Chapter_2_Literature_Review.tex`, `Chapter_6_Conclusions.tex`, `Appendix_A.tex`, `abstract.tex`

**What changed:**

*Error taxonomy terminology (all files):*
- "12-category error taxonomy" → "structured error taxonomy" throughout all `.tex` files. The "12" was specific to the invoice reconciliation system (4 error types × 3 tool call stages = 12 categories); the four error types (initialization, parameter handling, execution, result interpretation) are the generalizable contribution that scales with system complexity.
- Section 4.3 subsection heading: "12-Category Error Taxonomy" → "Structured Error Taxonomy."
- Section 4.3 introductory text: added explanation that the taxonomy "scales with system complexity: in the three-tool invoice reconciliation system, the four types yield twelve distinct failure modes; systems with more tool calls would produce correspondingly more categories."
- Diagnostic error analysis table caption: "12-category taxonomy" → "four-type taxonomy (yielding twelve categories across the three tool stages)."

*ConvPayMAS repositioned as work-in-progress (Chapter 4 and abstract):*
- Subsection title: "From Prototype to Production: ConvPayMAS" → "Ongoing Work: ConvPayMAS and Enterprise Evaluation Framework."
- Introductory paragraph: reframed from completed evolution to ongoing effort with "significant engineering work remains before production readiness, including comprehensive evaluation, scalability testing, and regulatory certification."
- Security subsubsection: "represents a significant evolution" → "introduces three advances" (less definitive).
- Enterprise Eval Framework subsubsection: reframed from "is being built" to "being designed"; changed definitive "implements" to "envisioned framework implements"; added closing sentence about remaining work needed.
- Chapter 4 intro item 7: "Production-evolved" → "Ongoing evolution...work in progress."
- Chapter 4 summary item 7: "Evolution of the research prototype into a production-ready" → "Ongoing evolution...toward a production" with "demonstrated at AAMAS 2026 as a work in progress."
- Chapter structure paragraph: "presents the evolution" → "describes ongoing work evolving."
- Abstract: "further evolved into...a production-ready system" → "Ongoing work is evolving...into" with "(demonstrated at AAMAS 2026)" and "being designed" for the eval framework.

---

## Pending Changes

| Reviewer Point | Description | Status |
|----------------|-------------|--------|
| #1a | Expand core threads with 1–2 pages of deeper discussion | **Done** (Research Journey + Entity Matching section + Industry Impact + ASR deep analysis + ConvPayMAS + Enterprise Eval Framework) |
| #1b | Reframe supporting work as "validation" | **Partially done** (Entity matching validates cross-domain reasoning findings; ConvPayMAS validates prototype→production evolution; ASR validates diagnostic framework in regulated domain) |
| #1c | Add Research Progression figure | **Done** |
| #2 | Clarify theoretical contributions (Ch 6) | **Done** (ASR formal definition in Ch 1 contributions; Ch 6 duplicate ASR removed; metrics table updated; Finding 1/6 updated; "Unifying the Evaluation Metrics" subsection added; concluding remarks updated) |
| #3 | More cautious generalizability claims | Not started |
| #4 | Stronger cross-chapter linkage | **Done** (Research Journey narrative + entity matching links Ch 2↔5↔6↔1 + ConvPayMAS links ASR diagnostics→production system→Enterprise Eval Framework) |