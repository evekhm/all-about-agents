# Question 01 · Merge Sections 2–3 and re-letter the seven layers

This kit replaces the earlier merge prompt; use this one only.

## 1. Old → new letters

The layers are regrouped so each acts at one point, and lettered in the order a request meets them.

| New | Layer | Comes from (old) |
|---|---|---|
| A | Data perimeter and provenance (incl. input screening) | old F + input screening from old D |
| B | Ground in their sources | old A (without the verification step) |
| C | Check every output in code | verification from old A + rules and repeatability from old D |
| D | Route by risk to accountable humans | old E |
| E | Log every step | old C |
| F | Evaluate and pin | old B + version pinning from old D |
| G | Roll out gradually | old G |

## 2. New layer text (replaces the old A–G paragraphs)

Lead sentence (replaces "The nine concerns in Table 1 are covered by seven engineering layers…"):

> The seven layers in detail, in the order a request meets them (Figure 2). Table 1 shows which concern each one answers; Table 3 lists what the customer receives from each and the Google Cloud service behind it:

**A · Secure the Data Perimeter and Document Provenance (Data Governance):** Keep customer data inside enforceable boundaries: contractual zero-training on customer data, regional residency, VPC perimeters, customer-managed encryption keys (CMEK), and explicit retention bounds. Screen every request at the boundary for PII, toxicity, off-topic asks, and prompt injection (Episode 01 covers data boundaries and prompt-injection defenses for agents that reach databases). Document what the customer is running: model cards (intended scope, limitations, benchmark results) and compliance certifications (SOC 2, ISO 27001 / 42001, HIPAA BAA).

**B · Ground Outputs in Their Sources (Explainability):** Pair retrieval with clickable inline citations linked to the customer's own documents, return structured JSON (verbatim_quote, sources, assumptions, answer), and return an explicit "not found in your documents" response whenever evidence is absent (Question 04 covers retrieval and citation design in depth).

**C · Check Every Output in Code (Control):** Verify in server code that cited passages genuinely support each claim, screen outputs for PII and off-policy content, and enforce permissions, dollar caps, and business rules in application code (Anthropic, Dec 2024). Constrain outputs where repeatability matters (structured output schemas, enumerated values, and a pinned thinking level) while keeping sampling parameters at the defaults current reasoning models are tuned for (Google, 2026). No decoding setting makes a hosted model repeatable: even greedy decoding on shared inference servers varies with the batch a request lands in (in one study, 1,000 identical requests to an open-weight model produced 80 distinct outputs; He et al., Sep 2025). Promise measured consistency (pass^k), and put calculations, thresholds, and final decisions in code.

**D · Route by Risk to Accountable Humans (Accountability):** *(the current text of old layer E, unchanged, starting "Match autonomy to error cost…" through "…to confirm reviews are real.")*

**E · Log Every Step (Auditability):** *(the current text of old layer C, unchanged, starting "Log every interaction…" through "…which calls failed and why.")*

**F · Evaluate and Pin with Customer Experts (Quality and Stability):** *(the current text of old layer B, unchanged, starting "Co-create a golden set…" through "…keeps pace with real traffic.")* Then, as a new paragraph, the current pinning paragraph from old layer D, unchanged: "If you fine-tune or run reinforcement learning, keep the reasoning trace out of the reward signal … Self-hosted open weights (Option 4) remove forced retirement altogether."

**G · Roll Out Gradually (Earned Trust):** *(unchanged.)*

## 3. Table 1: add a "Layer" column after "Concern"

| Concern | Layer |
|---|---|
| Explainability | B, C |
| Predictability | C, F |
| Training-Data Provenance | A |
| Model Weights | Option 4 |
| Data Governance | A |
| Reliability | B, D, G |
| Accountability | D, E |
| Version Stability | F |
| Quality | F |

In the Predictability "What Addresses It" cell, change "(Section 3, Layer D)" to "(Layer C, Section 2)". In the Model Weights cell, change "(Section 3)" to "(Section 2)".

## 4. Table 3: rebuild, keyed by layer

Title: **Table 3 · What Each Layer Gives the Customer, and the Google Cloud Service Behind It**

| Layer | What the Customer Receives | Google Cloud Service |
|---|---|---|
| A · Data perimeter and provenance | Zero-training terms, residency region, key ownership; input-screening results; model card and certifications | VPC Service Controls, CMEK (Cloud KMS), Assured Workloads and regional endpoints; Model Armor; published model cards |
| B · Grounding | Verbatim source quotes with links; "not found" when evidence is missing | RAG Engine grounding; structured output schemas |
| C · Output checks in code | Quote-verification results, rule checks, schema validation | Model Armor output screening; application code with structured output schemas |
| D · Risk routing and human review | Named reviewer sign-off; the routing threshold and its measured precision | The customer's review queue, with sign-offs logged to Cloud Logging |
| E · Logs and traces | A trace ID that replays any decision | Cloud Logging, Cloud Trace |
| F · Evaluation and pinning | Golden-set results, pass^k, failure slices; pinned model ID and a regression report before each cutover | Agent Platform evaluation service; pinned model version IDs; evaluation pipeline in CI |
| G · Graduated rollout | Shadow-mode comparison results; a kill switch | Agent Platform evaluation service for shadow comparisons; a feature flag in the serving layer |
| Option 4 · Open weights | Checksum of the self-hosted checkpoint | Model Garden open weights on customer-controlled infrastructure |

## 5. Other letter references to update

| Where | Old | New |
|---|---|---|
| Table 4 · EU AI Act, Layer cell | C, E, F, A | A, B, D, E |
| Table 4 · GDPR | A, E, Option 3 | B, D, Option 3 |
| Table 4 · SR 11-7 / SR 26-2 | B, C | E, F |
| Table 4 · HIPAA | C, F | A, E |
| Table 4 · CMS rule | A, Option 3 (Section 5) | B, C, Option 3 (Section 4) |
| The Cost of Trust paragraph | (Layer E) | (Layer D) |
| Worked example, "Diagnose first" | Layers A, C, and E | Layers B, C, D, and E |
| Worked example, "What the auditor receives" | trace ID … (Layer C); sign-off … (Layer E) | (Layer E); (Layer D) |
| Summary, "Make trust checkable" beat | (Section 3, Section 5) | (Section 2, Section 4) |
| Summary, "Prove it" beat | (Layers B, E, and G) | (Layers D, F, and G) |

## 6. Section merge and renumbering

- Merge Sections 2 and 3 into **"2. From "Black Box" to a Checkable System"** (keep `id="sec-2"`): remove the Section 3 heading so its content continues Section 2.
- Renumber: Scoping → 3 (`sec-3`), Worked Example → 4 (`sec-4`), Summary → 5 (`sec-5`). Update the nav and remove the old Section 3 nav entry.
- Update every other "Section N" reference: old 3 → 2, old 4 → 3, old 5 → 4, old 6 → 5.
