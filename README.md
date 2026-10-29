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

