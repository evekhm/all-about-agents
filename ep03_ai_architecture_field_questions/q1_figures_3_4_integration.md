# Question 01: Figures 3 and 4, integration kit

## Files

| File | Use |
|---|---|
| `fig_q1_options.html` | Figure 3 for the web page: a `diagram-frame` block with SVG, caption, and legend. Uses the page's CSS, so it follows the light/dark toggle. |
| `fig_q1_worked.html` | Figure 4 for the web page, same structure. |
| `fig_q1_options_standalone.svg` | Figure 3 with colors and fonts built in (light theme, white background), for PNG conversion. Renders at 1840×1020. |
| `fig_q1_worked_standalone.svg` | Figure 4, same. |

Both figures were rendered inside the page in light and dark themes, and the standalone SVGs were converted with `rsvg-convert` (no browser). All four came out clean.

Numbering: Figures 1 and 2 already exist. Figure 3 goes in Section 4 and Figure 4 in Section 5, so no existing numbers change.

## Placement

**Figure 3 (six-options map)**
- Section 4, immediately **after Table 2** and **before** the paragraph that starts "Question (3), which regulations apply…".
- In the sentence just before Table 2, change "…against structural transparency (Table 2):" to **"…against structural transparency (Table 2, Figure 3):"**

**Figure 4 (risky vs. verifiable design)**
- Section 5, immediately **after** the paragraph "Code then does everything that needs to be defensible…" and **before** Table 5.
- In that paragraph, change "…and routes the result (Table 5)." to **"…and routes the result (Figure 4 and Table 5)."**

## Captions (already inside the snippets)

**Figure 3:** The six options are not a straight trade-off. Rules, pure search, and classical ML are transparent but need structured input or refuse to synthesize; pinned open weights handle open-ended language but stay neural inside. The hybrid option reaches the high-stakes sweet spot: the model handles the language, and code makes the decision on verified facts. Positions are qualitative.

**Figure 4:** The same chart and the same model produce different outcomes depending on who decides. When the model decides, its thinking becomes the stored reason and criterion (b) is never checked, so the result is a wrongful denial. When the model only extracts quoted facts and code verifies the quotes and applies the policy's OR rule, the open criterion keeps the case alive and the system requests the missing evidence.

Short captions, for Medium or slides:
- **Figure 3.** The six options mapped by transparency and language flexibility: the hybrid option is the high-stakes sweet spot.
- **Figure 4.** Same chart, same model: when code decides on quoted facts, a wrongful denial becomes a request for the missing evidence.

## Alt text (for PNG versions)

**Figure 3:**
> Chart placing six architectural options by structural transparency (vertical) and language flexibility (horizontal). Deterministic rules, pure search, and classical ML with SHAP sit high on transparency but low on flexibility. Constrained generation sits in the middle. Pinned open weights sit low on transparency and high on flexibility, near an unconstrained LLM baseline. The hybrid option, where the LLM extracts and code decides, sits alone in a highlighted top-right area labeled "high-stakes sweet spot."

**Figure 4:**
> Diagram comparing two designs for the same prior-authorization request. Both start from the same chart and policy. In the risky design, the model decides and returns DENY, its thinking "only 3 weeks of ibuprofen" becomes the stored reason, and the result is a wrongful denial because criterion (b) was never checked. In the verifiable design, the model only extracts facts with verbatim quotes, code verifies the quotes and applies the policy rule "(a) OR (b) approves," finds (a) not met and (b) missing evidence, and returns PEND_FOR_EVIDENCE with a request for neurological exam notes and the PT log if done.

---

## Prompt for the agent

```text
Add two new figures to ep03_q1_enterprise_llm_trust.html.

Inputs (in this folder):
- fig_q1_options.html  → Figure 3
- fig_q1_worked.html   → Figure 4
Each file is a complete <div class="diagram-frame" id="..."> block (SVG, caption,
legend) that uses the page's existing CSS classes and variables. Paste each block
exactly as provided. Do not restyle, rename classes, or edit the SVG.

1. Figure 3: in Section 4, insert the contents of fig_q1_options.html immediately
   after the Table 2 block (the wrapper containing "Table 2 · Six Options Trading
   Transparency Against Flexibility") and before the paragraph that starts
   "Question (3), which regulations apply".
2. In the sentence that introduces Table 2, change
   "against structural transparency (Table 2):" to
   "against structural transparency (Table 2, Figure 3):"
3. Figure 4: in Section 5, insert the contents of fig_q1_worked.html immediately
   after the paragraph that starts "Code then does everything that needs to be
   defensible" and before the Table 5 block ("Table 5 · Who Decides What").
4. In that same paragraph, change "and routes the result (Table 5)." to
   "and routes the result (Figure 4 and Table 5)."
5. Do not renumber Figures 1 and 2 or any table. Change nothing else.

Before finishing:
- Confirm the ids fig-q1-options and fig-q1-worked are unique on the page, and
  that the marker ids (arr-q1o-*, arr-q1w-*) don't clash with existing ones.
- Report the exact insertion points and show a diff of every change.
- If the page has a PDF export, regenerate it.
```

For the internal PNG version, convert `fig_q1_options_standalone.svg` and `fig_q1_worked_standalone.svg`, and use the alt text above.
