---
name: content-eval
description: >
  Evaluates thought leadership content — whitepapers, case studies, blog posts,
  articles, op-eds, and long-form reports — and produces a quantitative scorecard
  with dimension-by-dimension analysis and ranked, actionable recommendations for
  improving writing quality. Scores content across 8 dimensions (clarity, credibility,
  originality, structure, audience alignment, executive value, evidence quality, and
  CTA effectiveness) on a 0–10 scale with a weighted overall score out of 100.
  Surfaces specific weaknesses with evidence pulled directly from the text, then
  prioritises the highest-impact fixes.
  Use this skill whenever the user wants to: evaluate a whitepaper, assess a case
  study, review a blog post or article, score content quality, audit thought
  leadership writing, get a writing quality report, improve an article or paper,
  check if content is compelling or credible, or benchmark content against
  B2B/executive-audience standards. Also trigger when the user pastes a long piece
  of writing and asks "what do you think?" or "is this good?" — they almost certainly
  want a structured evaluation.
argument-hint: "<paste text | file path | URL>"
allowed-tools:
  - Read
  - WebFetch
  - Bash
  - Glob
---

# Content Eval — Thought Leadership Quality Scorer

Evaluates written content and returns a structured quality report: a scored
scorecard, evidence-backed dimension analysis, and a prioritised improvement plan.

---

## Step 1 — Ingest the Content

Accept input in any of these forms:

- **Pasted text** in the prompt — use it directly
- **File path** (`.txt`, `.md`, `.pdf`, `.docx`) — read with the Read tool
- **URL** — fetch with WebFetch and extract the main body text, stripping nav/ads/boilerplate

If the content is very long (>3,000 words), read the full text but note the word
count in the report header. Don't truncate — scoring accuracy depends on seeing
the whole piece.

---

## Step 2 — Score Across 8 Dimensions

Score each dimension **0–10** (integers only). Use the rubrics below. Be
calibrated: a 10 is rare, 7 means "genuinely good," 5 means "mediocre but functional,"
3 means "significant problems," 1 means "nearly absent."

### Scoring Rubrics

| Dimension | Weight | What it measures |
|-----------|--------|-----------------|
| **Clarity** | 15% | Is the writing easy to follow? Are sentences crisp? Is jargon explained or avoided? |
| **Credibility** | 15% | Does the author/brand come across as authoritative? Are claims backed by data, citations, or named sources? |
| **Originality** | 12% | Does the piece offer a fresh angle, proprietary insight, or a contrarian take? Or does it rehash generic knowledge? |
| **Structure** | 12% | Is there a logical flow (hook → problem → evidence → solution → CTA)? Are headings, transitions, and pacing effective? |
| **Audience Alignment** | 15% | Is the tone, vocabulary, and framing well-matched to the intended reader (executive, practitioner, buyer, etc.)? |
| **Executive Value** | 13% | Would a busy senior leader find this worth their time? Does it deliver insight, not just information? |
| **Evidence Quality** | 10% | How strong and specific is the supporting evidence? (Original research > analyst citations > generic stats > anecdotes > assertions) |
| **CTA Effectiveness** | 8% | Is there a clear, motivated next step? Does it feel earned, not bolted on? |

Weighted overall score = Σ(score × weight) × 10, rounded to the nearest integer.

---

## Step 3 — Find Evidence for Weak Dimensions

For any dimension scoring **6 or below**, quote at least one specific passage
(verbatim, in quotation marks) that illustrates the weakness. Keep quotes short
(1–2 sentences). If a dimension scores well, you may still note what's working.

---

## Step 4 — Produce the Report

Use this exact report structure:

---

### Content Evaluation Report

**Content title / topic:** [infer from the text, or use the filename/URL]
**Content type:** [Whitepaper / Case Study / Blog Post / Article / Op-Ed / Other]
**Word count:** [approximate]
**Intended audience (inferred):** [e.g., B2B marketing leaders, C-suite, technical practitioners]

---

#### Scorecard

| Dimension | Score /10 | Weight | Weighted |
|-----------|-----------|--------|----------|
| Clarity | X | 15% | X.X |
| Credibility | X | 15% | X.X |
| Originality | X | 12% | X.X |
| Structure | X | 12% | X.X |
| Audience Alignment | X | 15% | X.X |
| Executive Value | X | 13% | X.X |
| Evidence Quality | X | 10% | X.X |
| CTA Effectiveness | X | 8% | X.X |
| **OVERALL** | — | 100% | **XX / 100** |

**Grade:** [A (85–100) / B (70–84) / C (55–69) / D (40–54) / F (<40)]
**One-line verdict:** [e.g., "Solid structure and credibility, but generic framing limits executive impact."]

---

#### Dimension Analysis

For each dimension, write 2–4 sentences:
- What the score reflects
- A specific quote as evidence (for weak dimensions, mandatory; for strong ones, optional but encouraged)
- The core reason for the score (not just a restatement of the rubric)

---

#### Top Recommendations (Priority-Ordered)

List 4–7 recommendations, ranked by impact. Format each as:

**#N — [Short action title]** *(addresses: Dimension Name)*
One paragraph explaining exactly what to change, why it will improve the score, and
ideally a concrete example or rewrite of the problem passage.

---

#### Quick Wins (Optional)

2–3 small, fast fixes (word-level, sentence-level) that would immediately sharpen the piece.

---

## Tone and Calibration Notes

- Be direct and honest — this is a professional quality evaluation, not a pep talk.
  Hedging the scores to avoid seeming harsh reduces the tool's value.
- Anchor scores to real-world benchmarks: a Fortune 500 CMO whitepaper is the
  reference for a "9" on Executive Value. A generic "5 tips" blog is a "4."
- If the content is genuinely strong, say so clearly — false modesty wastes the
  user's time just as much as unwarranted criticism.
- When quoting the text, always use quotation marks so the user can locate the passage.
- Avoid vague recommendations like "add more data." Make them specific:
  "Replace the claim in paragraph 3 ('companies see significant ROI') with a
  specific stat — ideally proprietary research, or cite a named source with year."

---

## Content Type Adjustments

Different content types have different expectations. Apply these adjustments:

- **Whitepaper**: Weight Credibility and Evidence Quality higher in your qualitative
  commentary (not the raw weights). Expect citations, methodology, and depth.
- **Case Study**: Audience Alignment and Evidence Quality matter most — is the
  customer story specific, measurable, and relatable to the target buyer?
- **Blog Post**: Clarity and Originality lead. Executive Value is less critical
  unless explicitly targeting senior leaders. CTA should feel natural.
- **Op-Ed / Point of View**: Originality and Credibility dominate. The author's
  voice and stance should be unmistakable. Evidence supports the argument, not
  the other way around.
- **Article (journalism-style)**: Structure and Evidence Quality are paramount.
  Balanced perspectives, named sources, and factual rigour are expected.

---

## Reference Files

- `references/scoring-examples.md` — Annotated examples of high and low scores per
  dimension, useful for calibrating ambiguous cases.
