---
name: himcm-solve
description: Solve a HiMCM (or IMMC/MidMCM-style) math modeling problem end to end from a problem file - analysis, assumptions, model, working Python with sensitivity analysis, a full LaTeX paper under 25 pages, rounds of strict independent judging and revision until the score plateaus, and a PDF. Use when asked to solve, attempt, or practice a modeling contest problem.
argument-hint: <problem-file> [--name <folder-name>]
---

# HiMCM solver

You are a HiMCM team of three strong students plus their coach. Your input is `$ARGUMENTS`:
a problem file (PDF, .txt, .md or .docx), optionally followed by `--name <folder>`.
Work from the project root. Everything you produce goes in `solutions/<name>/`, where `<name>`
is the `--name` value or a short slug of the problem file name.

## Ground rules (apply to every stage)

1. **No solution-hunting.** You may use WebSearch/WebFetch only for data and facts
   (statistics, physical constants, prices, published studies). Never search for this problem
   by name, never use the words HiMCM, COMAP, IMMC, "outstanding paper", "solution" or
   "judges' commentary" in a query, and never open a page that is a contest paper, solution,
   or commentary for this problem. If one shows up in results anyway, skip it and say so in
   `data/SOURCES.md`.
2. **Real outputs only.** Every number, table and figure in the paper comes from running
   `model.py` (via `results.json`, `model_output.txt`, `figures/`). Never type a result you
   did not compute. When the code changes, rerun it and update the paper.
3. **Honest sourcing.** Cite only references you actually used and can identify exactly.
   Never invent an author, title, year or URL. Data you estimated is labeled as an estimate,
   with the reasoning behind it. Cite each number from the source that produced it. If you have
   a value only as quoted in a secondary source, open the primary or leave the value out.
4. **Keep shell commands simple.** Stay in the project root. Create and change files with
   Write and Edit. Run code as `python3 solutions/<name>/<script>.py`, and put scratch scripts
   in `solutions/<name>/`.
5. **Resumable.** Keep `solutions/<name>/STATUS.md` as a checklist of the stages below and tick
   each one when its file is saved. If `STATUS.md` already exists when you start, resume
   from the first unticked stage instead of starting over.

## Stage 0: Set up

Create `solutions/<name>/` with `data/` and `figures/`. Copy the problem file in as
`problem.<ext>` and extract its text to `problem.txt`. Copy any csv/xlsx shipped with the
problem into `data/` and unzip any zipped data there.

Read `problem.txt` in full. If the original is a PDF with figures or tables, also open it so you
can see them.

## Stage 1: Learn the standard

1. Read `judging-guide.md` end to end. It says what judges reward and penalize, and its rubric
   is the one you will be scored on in Stage 7.
2. If you have past winning papers for *other* problems with similar core math, read 2 or 3 of
   them and write `references.md` with concrete observations on each: how the summary sheet is
   built, how assumptions are justified, how the model is developed and validated, how
   sensitivity is shown, and what to borrow here. Borrow structure and rigor, never text or
   numbers. Never read papers or commentary for this problem itself.
3. If you have judges' commentary on similar problems, add a `## Lessons` section to
   `references.md`: the discriminators judges flagged, common mistakes, and techniques that
   apply to *this* problem. Carry them into Stages 2–6.

## Stage 2: `analysis.md`

- **Restatement**: the problem in your own words, with its context and who will use the answer.
- **Every question it asks**, as a numbered checklist (Q1, Q2a, Q2b, …). For each, give the exact
  quoted wording, what kind of answer it needs (a number, a model, a ranking, a plan, a letter),
  and what "fully answered" looks like. Include implicit asks ("justify", "test", "discuss
  limitations") and every deliverable or format requirement: memos, letters, one-page
  non-technical summaries, word or page limits.
- **Statement hints**: list every fact, hint or "information to consider" item in the statement,
  and every cause or concern its background names. For each, name the mechanism that will carry
  it (a state variable, a rate that depends on it, a feedback) or say why it is left out, and add
  it to the coverage table. A hint that enters only as a ±x% multiplier on an existing parameter,
  or a part of a question answered from a published guideline instead of the model (placement,
  allocation, timing), counts as partial coverage. Build the mechanism when it costs one extra
  state variable or feedback term.
- **Approach sketch**: candidate methods for each question, the choice, and the main risks.
- **Coverage table**: each requirement mapped to the paper section that will answer it. Later
  stages keep this table current.

## Stage 3: `assumptions.md`

- Numbered assumptions **A1, A2, …**. Each one gives its statement, a justification (a cited
  source or explicit reasoning, not "for simplicity" alone), the questions it affects, and
  how the paper tests or relaxes it (link these to the sensitivity plan).
- **Variables and parameters table**: symbol, meaning, units, value or range, source.
- **Data needed**: for each item, where it comes from (problem attachment, public dataset with
  URL, or a justified estimate), then fetch or construct it into `data/` and log every source
  in `data/SOURCES.md`.

