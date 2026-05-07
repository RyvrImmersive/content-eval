# content-eval — Thought Leadership Quality Scorer

[![skills.sh](https://skills.sh/b/RyvrImmersive/content-eval)](https://skills.sh/RyvrImmersive/content-eval)

A [Claude Code skill](https://skills.sh) that evaluates thought leadership content and returns a structured quality report: a weighted scorecard, evidence-backed dimension analysis, and a prioritised improvement plan.

Works on **whitepapers, case studies, blog posts, articles, op-eds, and long-form reports**.

---

## What It Does

Scores content across **8 dimensions** on a 0–10 scale, produces a weighted overall score out of 100, surfaces specific weaknesses with verbatim quotes from the text, and delivers ranked, actionable recommendations.

| Dimension | Weight | What It Measures |
|-----------|--------|-----------------|
| Clarity | 15% | Is the writing easy to follow? Are sentences crisp? |
| Credibility | 15% | Are claims backed by data, citations, or named sources? |
| Originality | 12% | Fresh angle, proprietary insight, or contrarian take? |
| Structure | 12% | Logical flow, effective headings, good pacing? |
| Audience Alignment | 15% | Right tone, vocabulary, and framing for the intended reader? |
| Executive Value | 13% | Would a busy senior leader find this worth their time? |
| Evidence Quality | 10% | How strong and specific is the supporting evidence? |
| CTA Effectiveness | 8% | Clear, motivated next step that feels earned? |

**Grades:** A (85–100) · B (70–84) · C (55–69) · D (40–54) · F (<40)

---

## Installation

```bash
npx skills add ryvrimmersive/content-eval -g
```

Or install from the [Skills registry](https://skills.sh):

```bash
npx skills find content-eval
```

---

## Usage

Once installed, invoke it inside Claude Code:

```
/content-eval <paste text | file path | URL>
```

**Examples:**

```
# Score a pasted article
/content-eval [paste your article here]

# Score a local file
/content-eval /path/to/whitepaper.pdf

# Score a live URL
/content-eval https://yourcompany.com/blog/post-title
```

Accepts `.txt`, `.md`, `.pdf`, `.docx`, and any fetchable URL.

---

## Sample Output

```
#### Scorecard

| Dimension          | Score /10 | Weight | Weighted |
|--------------------|-----------|--------|----------|
| Clarity            | 8         | 15%    | 1.20     |
| Credibility        | 8         | 15%    | 1.20     |
| Originality        | 9         | 12%    | 1.08     |
| Structure          | 7         | 12%    | 0.84     |
| Audience Alignment | 9         | 15%    | 1.35     |
| Executive Value    | 8         | 13%    | 1.04     |
| Evidence Quality   | 7         | 10%    | 0.70     |
| CTA Effectiveness  | 3         | 8%     | 0.24     |
| **OVERALL**        | —         | 100%   | **77/100** |

**Grade:** B
**One-line verdict:** Sharp contrarian argument and strong audience calibration —
held back by an absent CTA and a slightly under-resolved structure.
```

Followed by:
- Dimension-by-dimension analysis with verbatim quotes as evidence
- 4–7 priority-ordered recommendations with specific rewrites
- Quick wins (word/sentence-level fixes)

---

## Content Type Adjustments

The skill applies different emphasis depending on content type:

- **Whitepaper** — Credibility and Evidence Quality weighted higher in commentary
- **Case Study** — Audience Alignment and Evidence Quality lead; specificity of metrics matters most
- **Blog Post** — Clarity and Originality lead; CTA should feel natural
- **Op-Ed / POV** — Originality and Credibility dominate; author voice must be unmistakable
- **Article (journalism)** — Structure and Evidence Quality are paramount

---

## Calibration Philosophy

- A **10** is rare — anchored to Fortune 500 CMO whitepapers and major analyst reports
- A **7** means genuinely good
- A **5** means mediocre but functional
- A **3** means significant problems
- A **1** means nearly absent

Scores are intentionally honest. The tool is designed to surface real gaps, not to validate.

---

## Files

```
content-eval/
├── SKILL.md                      # Skill definition and scoring rubrics
├── references/
│   └── scoring-examples.md       # Annotated calibration examples per dimension
└── evals/
    └── evals.json                 # 3 test cases (weak blog, strong case study, CEO op-ed)
```

---

## Evals

Three test cases are included to verify skill performance:

| ID | Content | Expected Score Range |
|----|---------|---------------------|
| 0 | Generic AI blog post (weak) | < 65 |
| 1 | Fintech case study with metrics (strong) | 75–90 |
| 2 | CEO LinkedIn op-ed with Edelman data (strong) | 75–88 |

Run evals with:

```bash
npx skills eval content-eval
```

---

## Author

Built by [RYVR Immersive](https://github.com/ryvrimmersive).
Feedback and PRs welcome.
