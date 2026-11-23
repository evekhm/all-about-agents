# Question 01 · Section 2 restructure: one spine, three steps

## The idea

Section 2 currently shows the concern → layer → evidence → Google Cloud mapping four times (Table 1's "What Addresses It" column, the A–G paragraphs, Table 2, and Figure 3). Give each element one job, connected by the layer letter:

1. **Why** — Table 1: the customer's concern, who raises it, the risk, and **which layer letter answers it**. (Slimmed: drop "What Addresses It".)
2. **Where** — Figure 2: where each letter acts on a request.
3. **What** — seven **layer cards**, A–G, each with the same four lines: what it does, which concerns it answers, what the customer gets, and the Google Cloud products. The cards replace both the old A–G paragraphs and Table 2.
4. **On Google Cloud** — Figure 3 closes the section as the picture of all the "On Google Cloud" lines.

A memorable frame to use throughout: **five checks on every request (A–E), two controls on every change (F–G).**

This works on Medium: Table 1 and the figures become images, and the cards are plain headings and short lines, with no table or hover needed.

---

## 1. New reading-path sentence

Add at the end of the paragraph that introduces Table 1 (after "...which concerns matter first"):

> Read the rest of this section in three steps: find the customer's concern and its layer letter in Table 1, see where that layer acts on a request in Figure 2, then read that layer's card below.

## 2. Table 1: remove the "What Addresses It" column

Keep: What the Customer Says | Concern (numbered 1–9) | Layer | Usually Raised By | Risk Behind It. Keep the row numbering, the layer badges, and the web-only hover highlighting.

The unique details from the removed column move into the cards below (provenance details into A, pass^k into F, the Model Weights detail into the Option 4 note).

## 3. Figure 2 caption: add the frame

Replace the caption with:

> Figure 2 — The model stays opaque; trust comes from checks around it. Five checks run on every request, in the order it meets them: screen it inside the customer's data perimeter (A), ground it in their sources (B), check the model's output in code (C), route it by risk (D), and log every step (E). Two controls run on every change: evaluate and pin (F), and roll out gradually (G).

## 4. Layer cards (replace the lead sentence, the A–G paragraphs, and Table 2)

Lead sentence (replaces "The seven layers in detail, in the order a request meets them (Figure 2). Table 1 shows...; Table 2 lists..."):

> **The seven layers.** Each card says what the layer does, which concerns from Table 1 it answers, what the customer receives as evidence, and the Google Cloud products behind it, followed by the details.

Format each card the same way: a heading with the letter and name, the one-line summary in bold, then four labeled lines, then the details. On the web, style it as a light card or bordered block; on Medium it is an H3 heading plus short lines.

---

**A · Data perimeter**
**Keep their data inside enforceable boundaries, and screen every request at the edge.**
- **Answers:** 3 Training-Data Provenance · 5 Data Governance
- **Customer gets:** zero-training terms, residency region, key ownership, input-screening results, model card, data statements, and certifications
- **On Google Cloud:** VPC Service Controls, CMEK (Cloud KMS), Assured Workloads and regional endpoints; Model Armor; published model cards
- **Details:** *(keep the current A paragraph unchanged, then add:)* For training-data questions, provide data statements (source categories, knowledge cut-off, filtering), published bias and safety evaluations, licensing terms, and IP indemnification. When the customer needs line-level disclosure of training data, fully open models with published training corpora (such as AI2 OLMo) are the option.

**B · Ground in their sources**
**Every answer cites the customer's own documents, or says it found nothing.**
- **Answers:** 1 Explainability · 6 Reliability
- **Customer gets:** verbatim source quotes with links; an explicit "not found in your documents" when evidence is missing
- **On Google Cloud:** RAG Engine grounding; structured output schemas
- **Details:** *(keep the current B paragraph unchanged)*

**C · Check outputs in code**
**Code verifies every claim and applies the business rules, so the model never has the last word.**
- **Answers:** 1 Explainability · 2 Predictability
- **Customer gets:** quote-verification results, rule checks, and schema validation
- **On Google Cloud:** Model Armor output screening; your own service (for example, on Cloud Run) with structured output schemas
- **Details:** *(keep the current C paragraph unchanged)*

**D · Route by risk**
**Low-risk cases run automatically; uncertain or high-impact ones go to a named reviewer.**
- **Answers:** 6 Reliability · 7 Accountability
- **Customer gets:** named reviewer sign-off; the routing threshold and its measured precision
- **On Google Cloud:** the customer's review queue, with sign-offs logged to Cloud Logging
- **Details:** *(keep the current D paragraph unchanged)*

**E · Log every step**
**Every input, source, model version, check, and sign-off is recorded, so any decision can be replayed.**
- **Answers:** 7 Accountability
- **Customer gets:** a trace ID that replays any decision
- **On Google Cloud:** Cloud Logging, Cloud Trace
- **Details:** *(keep the current E paragraph unchanged)*

**F · Evaluate and pin**
**A golden set built with their experts gates every change, and the model version moves only when it passes.**
- **Answers:** 2 Predictability · 8 Version Stability · 9 Quality
- **Customer gets:** golden-set results, pass^k consistency (a case passes only if all k runs succeed; Yao et al., ICLR 2025), and failure slices; a pinned model ID and a regression report before each cutover
- **On Google Cloud:** Agent Platform evaluation service; pinned model version IDs; evaluation pipeline in CI
- **Details:** *(keep the current F paragraphs unchanged, including the pinning paragraph)*

**G · Roll out gradually**
**Shadow mode first, automation only when the numbers clear the bar, with a kill switch.**
- **Answers:** 6 Reliability
- **Customer gets:** shadow-mode comparison results; a kill switch
- **On Google Cloud:** Agent Platform evaluation service for shadow comparisons; a feature flag in the serving layer
- **Details:** *(keep the current G paragraph unchanged)*

**Note after the cards:**

> Concern 4, Model Weights, is not a layer but an architecture choice: self-hosted open weights (such as Gemma or Llama) pinned by checksum, available on Google Cloud through Model Garden (Option 4, Section 3). Per-decision explanations still come from the layers above.

---

## 5. Figure 3 stays, as the section's close

Keep Figure 3 (the Google Cloud version) directly after the cards and the Option 4 note. Add one lead-in sentence before it:

> Figure 3 puts the "On Google Cloud" lines from the cards into the same picture as Figure 2.

## 6. Remove Table 2 and renumber

- Delete Table 2 ("What Each Layer Gives the Customer, and the Google Cloud Service Behind It"); the cards now carry its content.
- Renumber the later tables: Table 3 → 2, Table 4 → 3, Table 5 → 4. Update every in-text reference, including "Option 3 (Hybrid) in Table 3", the Figure 4 caption and legend, the "(TABLE 3)" label inside the Figure 4 SVG, and Table 1's Accountability row "(Table 4)" → "(Table 3)".

## 7. Medium version of Section 2

- **Table 1** → an image (light theme, 2x), captioned "Table 1 · Nine 'black box' concerns and the layer that answers each". Add the alt text: "Table of nine customer concerns, each with what the customer says, the team that usually raises it, the business risk behind it, and the layer letters A–G that answer it."
- **Figures 2 and 3** → PNGs from the standalone SVGs.
- **Layer cards** → plain text: an H3 heading per layer ("A · Data perimeter"), the bold one-liner, the four labeled lines, then the details paragraph.
- Drop the "Hover or click any row" hint on Medium.
