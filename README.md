# HiMCM Solver Skill for Claude Code

A [Claude Code](https://claude.com/claude-code) skill that works a HiMCM (or IMMC / MidMCM-style)
math modeling problem end to end: problem analysis → justified assumptions → model → working
Python with sensitivity analysis → a LaTeX paper under 25 pages → rounds of strict, independent
judging and revision → PDF.

## What's inside

```
.claude/
  skills/himcm-solve/
    SKILL.md              # the 8-stage workflow Claude follows
    paper-template.tex    # 12pt paper skeleton (summary sheet, sections, AI report)
  agents/
    himcm-judge.md        # adversarial judge subagent used in Stage 7
judging-guide.md          # what HiMCM judges reward/penalize + the weighted scoring rubric
```

## Setup

1. Copy `.claude/` and `judging-guide.md` into the root of the folder you run Claude Code in
   (or clone this repo and work inside it).
2. Install Python packages: `pip install numpy scipy pandas matplotlib`
3. Install LaTeX to get a PDF: `brew install tectonic` (macOS) or any TeX distribution with
   `latexmk`.

## Usage

```
/himcm-solve path/to/problem.pdf --name 2024-A
```

Everything lands in `solutions/<name>/`:

| File | What it is |
|---|---|
| `analysis.md` | restatement, every question as a checklist, statement hints, coverage table |
| `assumptions.md` | numbered assumptions with justifications, variables table, data sources |
| `model.md` | the model per question, why it beats a simpler alternative, sensitivity plan |
| `model.py` | the code; writes `figures/`, `results.json`, `model_output.txt` |
| `paper.tex` / `paper.pdf` | the final paper |
| `reviews/` | each judge round's review, revision log and snapshot |
| `review.md` | score table across rounds + final review |
| `STATUS.md` | stage checklist; rerun the command to resume from where it stopped |

## How it works

| Stage | Output |
|---|---|
| 0. Set up | solution folder, problem text, data |
| 1. Learn the standard | read the judging guide (and similar past winning papers, if you have them) |
| 2. Analysis | every explicit and implied requirement, mapped to paper sections |
| 3. Assumptions | A1, A2, … each justified and linked to a sensitivity test |
| 4. Model | formulation, validation, one closed-form result, scenarios |
| 5. Code | `model.py` with sensitivity analysis, asserts and checked figures |
| 6. Paper | one-page summary, finding-first captions, plain-language explanations, 12pt only |
| 7. Judge → revise | a fresh judge each round; 2–3 revisions; a revision may not lengthen the paper |
| 8. Compile | PDF under 25 pages |

Key rules the skill enforces:

- **Every number in the paper comes from running the code.** No typed-in results.
- **No solution-hunting.** Web search is for data and facts only.
- **Real citations only.** Estimated data is labeled as an estimate.
- **Write for a non-specialist math teacher.** Explain each method in plain words or cut it.

## The judge

`himcm-judge` scores 12 sections from 1 to 10 with weights (model development and results ×3,
summary and sensitivity ×2, …), applies score caps (e.g. a summary with no numbers caps at 5),
and gives a designation estimate from Successful Participant to Outstanding contender. It's
intentionally stricter than real panels, so read the estimate as a relative score, not a
prediction of the award.

## Academic honesty

HiMCM requires a Report on Use of AI, and the template includes one. Check your contest's
current rules on AI use before submitting anything this produces.
