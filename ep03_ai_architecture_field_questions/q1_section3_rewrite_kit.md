# Question 01 · Section 3 rewrite kit

## New structure

Title: **3. Choosing How Much the Model Decides** (nav label: "How Much the Model Decides")

1. Bridge from Section 2 (new)
2. Scope before you build: the seven questions, each saying what its answer changes (rewritten)
3. Six ways to split the work between model and code: plain-language intro, Table 3 (rewritten, renumbered), Figure 3, and a reading guide for Figure 3 (new)
4. Pick per step, not per system: a worked mapping on the prior-authorization case (new)
5. Which regulations apply: Table 4 (letters fixed)
6. The cost of trust (unchanged)

Use the page's existing subheading style (h3, or bold lead-in paragraphs if the page has no h3 style) for items 2–6.

---

## 1. Bridge (replaces "How far we go on those controls depends on seven questions we align on with the customer:")

> The layers in Section 2 wrap any model. The second lever is how much of each decision the model makes at all. A model that only reads documents and extracts facts needs far less trust than one that decides, so the most effective control is often architectural: give the model the language work, and give the decision to something a person can inspect. Which split is right depends on the customer's answers to a few scoping questions.

## 2. Scope before you build

Lead-in:
> Seven questions to align on with the customer, and what each answer changes in the design:

Replace the plain list with this list (keep the page's list style; bold the question):

1. **What exact decision does the system make, and what does an error cost?** Sets how much autonomy is acceptable (Layer D) and which option below fits each step.
2. **Who needs the explanation?** End users need citations, operators need dashboards, auditors need logs and lineage, and regulators need formal documentation. Sets what Layers B and E must produce.
3. **Which regulations apply?** Decides which layers are mandatory rather than optional (Table 4, below).
4. **Where does the data live, and who can access it?** Shapes the data perimeter (Layer A), and whether self-hosted open weights (Option 4) are required.
5. **What measurable bar defines "good" before we build?** Becomes the golden set and its pass threshold (Layer F).
6. **How fast is a bad output detected and fixed?** Sets monitoring (Layer E) and the kill switch (Layer G).
7. **How do model updates roll out?** Sets pinning and the cutover process (Layer F).

## 3. Six ways to split the work between model and code

Intro (replaces "Depending on the answers, we choose for each step among six options that trade open-ended language flexibility against structural transparency (Table 2, Figure 3):"):

> Every design choice for a decision step trades two things: **transparency**, meaning how much of the logic a person can inspect, and **language flexibility**, meaning how much unstructured text the step can handle. Table 3 describes six options in plain terms, and Figure 3 places them on those two axes.

### Table 3 · Six Ways to Split the Work Between Model and Code

(Rename from "Table 2 · Six Options Trading Transparency Against Flexibility". New columns: Option | What It Is | What a Person Can Inspect | Limits | Good Fit.)

| Option | What It Is | What a Person Can Inspect | Limits | Good Fit |
|---|---|---|---|---|
| 1. Deterministic rules and solvers | Hand-written if-then logic, SQL queries, or math formulas | Every rule, line by line | Needs clean, structured input; cannot read free text | Calculations, thresholds, hard policy gates |
| 2. Interpretable classical ML + SHAP | Traditional machine-learning models trained on tables of numbers and categories rather than text: logistic regression, decision trees, or gradient-boosted decision trees (GBDTs, ensembles of many small decision trees such as XGBoost) | Each prediction broken into per-input contributions with SHAP, a method that attributes a single prediction to its inputs (for example, "missed payments: −30 points") | Needs structured, tabular data | Credit scoring, risk grading, numerical forecasting |
| 3. Hybrid (sweet spot) | The LLM reads documents and extracts structured facts with source quotes; rules or a scoring model make the decision | The decision logic, plus every fact it used and the quote behind it | Extraction can still miss a fact, so quotes are verified in code (Layer C) | Policy, eligibility, and compliance decisions made from documents (Section 4) |
| 4. Pinned small or open-weight model | A model whose exact weights the customer hosts and freezes | The exact checkpoint (by checksum) and its training documentation | Its reasoning is still neural and opaque (Section 1) | Air-gapped or sovereignty requirements; strict version control |
| 5. Constrained generation | The LLM chooses from fixed categories or fills approved templates instead of writing freely | The complete list of outputs it is allowed to produce | Controls what it outputs, not how it chose | Routing, classification, templated letters |
| 6. Pure search and retrieval | Returns ranked passages from the source documents; generates no text of its own | The exact passages shown | Does not synthesize an answer; the reader decides | Users who prefer to read primary sources themselves |

*(Figure 3 stays where it is, directly after Table 3.)*

### Reading guide for Figure 3 (new paragraph, directly after Figure 3)

> **How to read Figure 3.** The vertical axis is how much of the logic a person can inspect; the horizontal axis is how much unstructured language the option can handle. Most options sit in one of two corners. Rules, search, and classical ML (top left) are inspectable but need structured input or refuse to synthesize. Pinned open weights and an unconstrained LLM (bottom right) handle any language but stay neural inside. Constrained generation sits between them: it narrows what the model may output, not how it reasons. Only the hybrid reaches the top right, because it never asks one component to do both jobs: the model handles the language, and code makes the decision on facts it can check.

## 4. Pick per step, not per system (new paragraph, after the Figure 3 reading guide)

> **Pick per step, not per system.** A real workflow mixes options. In the prior-authorization case (Section 4), looking up the applicable policy is pure search (Option 6); reading the chart and extracting facts with quotes, then applying the policy, is the hybrid (Option 3); thresholds such as "at least 6 weeks" are deterministic rules (Option 1); and the notice to the provider fills an approved template (Option 5). The option chosen also decides which Section 2 layers carry the weight: in the hybrid, checks in code (Layer C) carry the decision; in pure search, grounding (Layer B) is the whole product.

## 5. Which regulations apply

Lead-in (replaces "Question (3), which regulations apply, usually decides how much of each layer is mandatory (Table 4):"):

> Scoping question 3 often settles the argument about how much control is enough, because regulation makes some layers mandatory (Table 4):

Fix two cells in Table 4's Layer column:
- SR 11-7 / SR 26-2: "B, C" → **"E, F"**
- HIPAA: "C, F" → **"A, E"**

## 6. The cost of trust

Unchanged.

---

## Table renumbering (page-wide)

Since the merge, the layer table appears before the options table, so swap their numbers:
- Current "Table 3 · What Each Layer Gives the Customer…" (in Section 2) → **Table 2**
- Current "Table 2 · Six Options…" (in Section 3) → **Table 3** (with its new title above)

Update every in-text reference to match. In particular:
- Section 2's lead into the layers says "Table 3 lists what the customer receives…" → **"Table 2 lists…"**
- Section 1's "fourth route" paragraph says "Option 3 (Hybrid) in Table 2" → **"in Table 3"**
- The Figure 3 caption and legend say "(numbered as in Table 2)" or "SIX OPTIONS (TABLE 2)" → **"Table 3"**. This includes the label inside the Figure 3 SVG; it is the only SVG text to change.

## New reference

- Lundberg and Lee, *A Unified Approach to Interpreting Model Predictions* (arXiv:1705.07874), May 2017 (NeurIPS 2017). Introduces SHAP, which attributes a single prediction to each of its input features. https://arxiv.org/abs/1705.07874
