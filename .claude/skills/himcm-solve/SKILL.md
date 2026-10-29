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

## Stage 4: `model.md`

For each question:
- **Why this model**: name one simpler alternative and say why yours is better, or why simple
  is enough. Judges reward a well-explained, well-justified model over a complex black box.
- **Formulation**: equations, objective and constraints, or the algorithm step by step, in
  LaTeX math. Define every symbol, and keep notation consistent with `assumptions.md`.
- **Parameter estimation**: how each parameter gets its value.
- **Outputs**: exactly what the code will produce for this question.
- **Validation**: limiting cases, comparison with real data, sanity checks.
- **Relationships**: if a question asks how two quantities are related, cover strength,
  functional form, timing (lag) and direction, including feedback: test whether Y helps predict
  X as well as X → Y. Say which of these you tested.
- **Choosing the best model**: if a question asks which model is best or most accurate, compare
  the candidates out of sample at the horizon where the answer will be used, or show accuracy
  against horizon and say where the ranking changes. If one candidate uses inputs the others
  lack, say so and answer in two parts: best given that input, and best without it.
- **Scenarios**: if an answer depends on what people decide (policy, investment, adoption,
  prices), include at least one scenario built from real, dated, cited commitments or plans
  next to the stylized cases. Where data allow, drive it through levers a decision-maker
  controls (for example, activity level × intensity) rather than a bare trend.
- **How many / how much**: if a question asks for a number of units to supply (hives, staff,
  vehicles, beds, stock), show what each added unit buys (a marginal curve) next to what it
  costs: a cited price, and any harm from oversupply (crowding, competition, waste). Recommend a
  point on that curve, say why, then give the reliability it buys. A reliability target alone is
  not a decision a reader can weigh.
- **One closed-form anchor**: derive at least one result by hand from the model's equations: an
  equilibrium or long-run average, a threshold (break-even, collapse, tipping point) or a scaling
  law. Use it to explain the main sensitivity ranking in one line, as a limiting-case `assert` in
  `model.py`, and in one summary sentence.
- **Show the dynamics**: for a dynamic model, plot one run over the full horizon from a stated
  starting state, transient included, and show whether the long-run answer depends on that start.
  If the model has a qualitatively different regime (collapse, extinction, saturation), plot runs
  on either side of the threshold on one figure.
- **Open cases**: when the statement leaves the case open (which crop, city, product), go deep on
  one well-documented case, then run three to five named alternatives with sourced inputs through
  the same model and report them in one table.
- **Sensitivity plan**: which parameters and assumptions get varied, and over what ranges.

## Stage 5: `model.py`

- One script, organized by question. Paths are relative to the script
  (`HERE = Path(__file__).parent`) so it runs as `python3 solutions/<name>/model.py`.
  Use numpy, scipy, pandas and matplotlib, plus the files in `data/`. Fix all random seeds.
- It must write `figures/*.png` at dpi 200 or more, with labeled axes and units, a legend
  where needed, and a style readable in grayscale. It must write `results.json`, holding every
  number the paper will cite, nested by question. It must also write `model_output.txt`, a
  readable log of the run.
- **Sensitivity analysis is required.** Vary each key parameter ±10–20% or across its
  plausible range one at a time, and show the effect on each headline result (a tornado chart
  or sensitivity curves). Test at least one assumption by swapping in an alternative. Rerun at
  least one headline answer on another version of the input data (a different source, sampling
  frequency or subset) and report how far it moves. If the model is stochastic, use Monte Carlo
  and report spread, not single runs.
- Include validation checks such as `assert`s on conservation laws, bounds and limiting cases.
- **Run it and fix it until it works**: `python3 solutions/<name>/model.py`. Repeat until it
  exits cleanly. Then open the figures with Read and check them as an image, fixing clipped
  labels, unreadable axes and empty plots. Check that the results are plausible in the real
  world; implausible numbers mean a bug or a bad assumption, so fix the cause.

## Stage 6: `paper.tex`

Start from `.claude/skills/himcm-solve/paper-template.tex` and copy it to
`solutions/<name>/paper.tex`. The paper must stay **under 25 pages including the summary sheet**.
The "Report on Use of AI" at the end does not count toward that limit. Budget roughly: summary
1, contents 1, introduction 1–2, assumptions 1–2, models and results 10–13, sensitivity 2–3,
strengths and weaknesses 1, required letter or memo 1, references 1.

1. **Summary sheet**, exactly one page and written last. It covers the problem, the approach for
   each question, the key quantitative results (actual numbers), the recommendation, and
   keywords. Judges read it first, and triage judges may read nothing else. Give each question
   its headline answer in one or two numbers; leave backtest errors, fitted parameters and
   intervals to the body unless they are the answer. Name each method by what it does, in
   words. No model codes (M1, Model B), symbols or test names on this page.
2. **Introduction**: background, the restatement, an overview of the approach (a small
   flowchart or roadmap is welcome).
3. **Assumptions and justifications**: the A1… list, condensed from `assumptions.md`.
4. **Notation** table.
5. **Model sections**, one per question: development, then solution, then results. Use the real
   figures from `figures/` and numbers from `results.json`, and interpret every figure in the text.
6. **Sensitivity analysis and model validation.**
7. **Strengths and weaknesses**: specific and honest, with each weakness tied to a possible
   improvement. Before writing it, sort the improvements you plan to propose. Any that public
   data and about an hour of coding can deliver (adding an omitted variable, a scenario from
   real plans, an alternative dataset), do in `model.py` as a robustness check, rerun, and
   report as a result. Keep here only improvements that are out of reach, and say why.
8. **Required deliverables** (a letter, memo, etc.) if the problem asks for any, written for the
   stated audience in plain language. Make it look like the medium asked for: an infographic or
   web blog is a designed page, not a page of the paper. Give it a headline, the two or three
   answer numbers in large type, short labelled cards for the top factors or actions (each with
   its value and direction), one chart whose title states its message, and a sketch if the answer
   is spatial. Build it as a full-page figure from `model.py` (so every number is computed) or
   with LaTeX boxes, smallest text 12 pt at print size, under about 150 words for an infographic
   and 350 for a blog.
9. **Conclusion** with a direct answer to every question. For every yes/no or agree/disagree
   question, write one verdict sentence and use it word for word in the summary, the body, the
   conclusion and any letter or article.
10. **References**: real sources, cited in the text.
11. **Report on Use of AI**, starting on its own page after the references. Disclose honestly that
    the paper was produced with Claude via Claude Code, and how. The template explains what to
    include.

**Write for a mathematics teacher who is not a specialist.** The first time the paper uses a
named method, test or statistic (a bootstrap, an information criterion, a unit-root test,
cross-validation), explain in one to three plain sentences what it does and why this problem
needs it. If it cannot be explained that briefly, or it changes no answer, cut it. When a
paragraph would list more than four numbers, put them in a table or figure and use the prose to
say what the table or figure shows.

**Lead with the finding.** Every figure and table caption opens with its takeaway in one sentence
("Egg-laying rate moves colony size more than any other factor."), then says what is plotted.
Title results subsections by what they found where you can. After each key equation, say in one
plain sentence what it does. The summary sheet holds at most four numbers per paragraph and about
twelve on the page (numbers copied from the statement excluded). In the body, keep only the
robustness checks that move or bound a headline answer, and collect the rest in one table.

**Keep floats next to their text.** Place each table and figure with `[H]` or `[htbp]` right
after the paragraph that introduces it, never before its own section heading. After compiling,
look at the PDF pages: no heading may be left empty, and no page may be more than a third blank
except the last page of a section that ends early.

**12-point type everywhere.** Never use `\small`, `\footnotesize`, `\scriptsize`, `\tiny`,
`\fontsize` or `\linespread`: not in the summary sheet, tables, letter or captions. Judges
penalize shrunken type. If something does not fit, cut words.

When the draft is complete:
1. Walk the coverage table in `analysis.md` and confirm every requirement is answered in the paper.
2. Check that every number in the paper traces to `results.json`, `model_output.txt` or a cited
   source. Fix stale numbers and typos.
3. Compile once (see Stage 8) so the judge can see `paper.pdf` and the real page count.

