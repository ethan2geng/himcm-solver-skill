# HiMCM Judging Guide

Distilled from the HiMCM judges' commentaries and contest-director articles for 1999–2022,
plus the IM2C expert-panel commentaries for 2015–2022.
It is deliberately **generic**: it contains no problem-specific judge remarks, so it is safe
to read while solving any problem, including a backtest of a pre-2023 one. The solver
reads it in Stage 1. The judge scores with the rubric in Part 4.

---

## Part 1: How papers are judged

- **No answer key.** "We do not compare your responses to an official answer key. Modeling
  problems rarely have a single solution approach or answer." Papers are scored on their own
  merits for completeness, creativity, and good modeling practice. Widely different
  numerical answers are all acceptable *if they are justified by the assumptions*.
- **Two rounds.** Two preliminary judges read and score each paper and rank it Finalist,
  Meritorious, Honorable Mention, or Successful Participant. Finalists go to a final panel,
  which picks the "best of the best" as Outstanding. Judging is blind, so no names or
  schools appear on the paper.
- **The summary decides the first cut.** It is the first page every judge reads, and judges
  "place considerable weight on the summary, especially in the first round of judging when the
  first 'cut' is made".
- **Base rates (2022, 833 judged papers):** Outstanding about 1%, Finalist about 6%,
  Meritorious about 15%, Honorable Mention about 24%, Successful Participant about 50%. The top
  20–25% earn Meritorious or above.
- **Appendices are skimmed at most.** "We may refer to an appendix to check a reference or a
  step in your computer code, but otherwise may not examine or read an appendix". Anything that matters must be in the body.

## Part 2: What separates the best papers

The judges' own definition, repeated almost word for word every year from 2017 to 2022:

> Competitive papers include a comprehensive summary and address all requirements through
> developing and applying a mathematical model, and write a clear letter or memo if required.
> Better papers do all of the above in an articulate, well-supported, well-organized and
> well-presented manner. The best papers combine complete mathematical and logical analysis
> and explain their work in an organized presentation beyond simply addressing the
> requirements. They are easy to read, flow logically, are creative, and include sections on
> assumptions with justifications, the modeling process, results, strengths and weaknesses,
> sensitivity, conclusions, and references.

The principles that come up again and again:

1. **Understood mathematics beats impressive mathematics.** "We are not looking for papers
   that use the most advanced mathematics." Teams that use advanced tools they "do not
   understand, explain clearly, or use appropriately ... do not do well". Simple models that
   are well explained are "often among our Outstanding designees". "Teams should
   not throw out several model forms hoping to WOW the judges, as this does not work".
2. **Model development is the most important part.** "Take the reader on a journey": explain
   why you chose this model, how it is built from the assumptions, and how you adapted it.
   Presenting a model without its development does poorly.
3. **State the final model explicitly.** "Do not make the judges have to look for your final
   model." Never introduce one model and then silently use another. Several models should
   build on each other, and the paper must say which one answers each question.
4. **Answer every requirement, specifically.** Better papers give concrete answers (named
   locations, counts, schedules, a ranked list), not "it depends". The best papers then go
   beyond the bare requirement and handle nuances: tradeoffs, edge cases, and real-world
   constraints the statement only implies.
5. **Find the unwritten requirements.** Some problems have tasks that are only implied, such
   as the need to build a dataset, a candidate list, or a definition before the stated
   question can be answered. Competitive papers notice these. Define the problem's key
   terms ("best", "fair", "efficient", the event being predicted) precisely and early.
6. **Read the requirements literally.** When the problem says *describe* what you would need
   rather than *build* it, don't spend pages building it at the expense of the parts it does
   ask for. Deliver what is asked, in the format asked for.
7. **Stay in touch with reality.** Sanity-check magnitudes and units, test worst realistic
   cases rather than only averages, and compare results with outside benchmarks where they
   exist. When results disagree with the benchmarks, discuss why.
8. **Explore the data before modeling.** Look at the provided data by group and subgroup, and
   notice discrepancies and missing values. Handle missing values thoughtfully, for example by
   comparing with similar cases or using correlation or regression, not by plugging in the
   mean or dropping rows.
9. **Mix text, tables, figures and math.** Avoid "pages and pages of text or pages and pages
   of graphs". Discuss every figure in the text. A flowchart of the overall approach is
   repeatedly praised.
10. **Creativity is rewarded, but it has to work.** Modifying or chaining existing models
    beats lifting one from the Internet. Never simply re-present a published model
   .

## Part 3: Section-by-section expectations

### Summary sheet (page 1)
- Write it **last**, as one page that stands alone.
- Use three to five paragraphs: the problem restated in your own words, the methods (in
  words, not equations), the model, and **the actual numerical results and recommendations
  in context**.
- The most common failure, flagged every year, is a summary that describes the process but
  leaves out the results. "Teams should include results and not just a discussion of their
  approaches".
- It should make the reader want to read the paper. The best IM2C summaries also mention
  strengths and weaknesses.

### Table of contents
- Finalist and Outstanding papers "preview their paper with an organized Table of Contents"
 .

### Introduction, background and restatement
- Keep the background brief. Restate the problem and the specific questions, and preview the
  approach, ideally with a diagram of the modeling process. "Do not simply repeat the summary"
 .

### Assumptions with justifications
- Include only assumptions that the model actually needs; ask "do we need this to develop or
  support our model?" Long "laundry lists", "smoke screens" and irrelevant assumptions (such
  as "no catastrophe destroys the system") count against the paper.
- **Facts given in the problem are not assumptions**.
- Every assumption gets a short justification, with a citation where possible.
  Avoid over-simplifying to the point where the problem can no longer be fully solved.
- List them together, up front, and note where each is used ("A7 is used in Model 4")
 . Link the key ones to the sensitivity analysis: "if you assumed a value, how
  would changing it affect your conclusions?".

### Variables and notation
- Give a table of symbol, meaning and units. Keep the set manageable, don't define variables
  you never use, and remind the reader of definitions and units where the variables are used
 .

### Mathematical model
- Show the development, the reasons for the choices, and how it follows from the assumptions.
  Present the full final model, and connect any sub-models logically.
- If code is used, describe its logic in the paper with an algorithm or flowchart; "judges
  expect to see an algorithm or flow chart from which the code was developed". A simulation must run many trials, and its inputs must be varied.
- Cite any existing model or equation at the point where it is used.
- Keep discussion of models that were tried and then dropped brief.
- Each hint in the statement ("information to consider", the causes its background names)
  should be carried by a mechanism in the model, or its omission explained. A hint handled only
  as a parameter multiplier is partial coverage.
- Where the model allows it, derive one result in closed form (an equilibrium, a threshold, a
  scaling law) and use it to explain what the simulation shows. It is the clearest evidence that
  the authors understand their model.

### Results and answers to every requirement
- Apply the model to the actual scenario and data. Give specific answers to every question,
  with numbers, units and interpretation. Better papers make tradeoffs explicit and back
  every decision with analysis.
- When a question asks how two quantities are related, its implied requirements include
  direction (and any feedback) and timing, not only strength and form. When it asks which model
  is best, the comparison should use equal information and the horizon at which the model is
  later used.
- When the answer is a quantity to provide (units, staff, stock), better papers show what each
  extra unit buys and what it costs or harms, and choose a point on that curve. A reliability
  target alone leaves the reader without the tradeoff.

### Sensitivity analysis and validation
- A "very important part of the modeling process" that "tests" the assumptions and parameter
  values, for instance by changing them ±10% and discussing what happens to the answer.
  In ranking or weighting models it is critical: how sensitive is the winner to the weights?
 . Judges have repeatedly called it the discriminator that "few papers" did well
 .
- Validate the model, "even if by numerical example or intuition". "Model
  testing is not the same as testing arithmetic".

### Strengths and weaknesses (limitations)
- Be open and honest: under what conditions does the model work best, and where does it
  fail? Connect weaknesses back to assumptions, and propose extensions or what you would do
  with more time.

### Required non-technical deliverable (letter, memo, article, blog, infographic)
- Write for the stated reader, who has no math background: results, recommendations, and why
  they matter to that reader, with **no equations**. Graphics and flowcharts help.
- Follow the requested format and purpose exactly. A memo meant to help someone decide must
  be usable for that decision, not a summary of the mathematics.
- Bring the specific recommendations here.
- Match the medium as well as the audience: a web infographic or blog is a designed page, with
  the answer numbers in large type, labelled visual cards and one chart whose title states its
  message. It is not a page of the paper.

### Conclusion
- State explicitly the answer to each requirement or scenario question. This is not a second
  summary.

### Citations and references
- Cite in line at the point of use for every outside model, equation, data value, figure and
  table, and include a reference list at the end. "Lack of documentation will result in a
  lower designation." Prefer primary sources over Wikipedia. Unreferenced
  diagrams copied from the web are a recurring complaint.

### Presentation and rules
- Stay within the page limit with at least 12-point font, and don't shrink fonts or margins
  to fit more. Papers that do "are unlikely to score well". The current limit is 25
  pages including the summary, contents, references and appendices. The COMAP "Report on Use
  of AI" is appended after the references and does not count.
- Put no student or school names in the paper. Put the team control number on every page.
  Use English for all symbols in tables and graphs. Spell-check and proofread.
- Graphs need labeled axes, units and legends, must "make sense", and should be readable in
  grayscale, using line styles and markers rather than color alone.
- Tell a story in a logical sequence, so that each section leads into the next.
- Captions and results headings state the finding first, then what is shown. Volume is not
  quality: robustness tables that change no answer dilute the message.

## Part 4: Scoring rubric (used by the judge)

Score each section **1–10** against the anchors below. **Be strict.** Half of all real
submissions are Successful Participant and about 1% are Outstanding, so start from the
assumption that a paper is ordinary and make it earn every point above 6.

This rubric is stricter than the real panel. Papers that won real Outstanding awards, scored
blind on it, have landed mostly between about 3 and 6, because real panels forgive gaps that it
caps. Keep scoring strictly; read the designation estimate as a position on this rubric, not a
forecast of the real award.

| Score | Anchor |
|---|---|
| 9–10 | Outstanding level: COMAP could reprint it as the exemplar for this section in the judges' article. No real flaw. |
| 7–8 | Finalist/Meritorious: complete and well executed; minor gaps a careful judge would note. |
| 5–6 | Honorable Mention: present and adequate but generic, thinly justified, or partly missing. |
| 3–4 | Successful Participant: major gaps, errors, or confusion. |
| 1–2 | Missing, wrong, or counterproductive. |

**Sections and what earns 9–10:**

1. **Summary sheet** (weight 2): stands alone; covers problem, methods in words, final model,
   *specific numerical results*, and recommendations; one page; makes the judge want to read on.
   **Cap it at 5 if it has no concrete results.** A summary crowded with intermediate numbers,
   model codes, symbols or test names does not earn 9–10, however complete: each question's
   headline answer should read in words a non-specialist can follow.
2. **Introduction and restatement** (weight 1): brief background, a precise restatement of
   every question, and a roadmap or flowchart; does not repeat the summary.
3. **Assumptions and justifications** (weight 1.5): each assumption is necessary, justified
   (cited where possible), not a fact from the statement, and linked to where it is used and
   to the sensitivity tests. **Cap at 5 for a laundry list or for unjustified assumptions.**
4. **Notation and variables** (weight 0.5): a complete, minimal table with units, and
   consistent use throughout.
5. **Model development** (weight 3): the choice is motivated and compared with an alternative;
   it is built step by step from the assumptions; the final model is stated in full; the logic
   of any code is shown with an algorithm or flowchart; the math is correct and the authors
   clearly understand it; the statement's hints are carried as mechanisms or their omission is
   explained; at least one result is derived in closed form where the model allows. **Cap at 6 if the final model is unclear or switches without
   explanation, and at 4 for an unexplained black box.**
6. **Results and requirement coverage** (weight 3): every requirement (see the coverage table)
   gets a specific, quantified, interpreted answer, including the implied requirements; the
   numbers are consistent with the code outputs; the results pass a reality check. **Cap at 6
   if any requirement is missing or only gestured at.** A "how many" answer shows the benefit
   and the cost or harm of extra units, not only a reliability target.
7. **Sensitivity analysis and validation** (weight 2): key parameters *and* at least one
   structural assumption are varied; the effect on the actual answers is shown and
   interpreted; there is validation against data, limiting cases or benchmarks. **Cap at 4 if
   absent or purely mechanical.**
8. **Strengths and weaknesses** (weight 1): specific, honest, tied to assumptions, with
   concrete improvements. **Cap at 5 if generic** (for example "our model is simple"). An
   improvement listed as future work that public data and an hour's work would have delivered
   is a missed result, not an honest limitation.
9. **Non-technical deliverable** (weight 1.5 if required, otherwise drop it): right audience,
   format and length; no equations; specific recommendations; visuals, and it looks like the
   requested medium (a designed page for an infographic or web blog); usable by the stated
   reader.
10. **Conclusion** (weight 0.5): directly answers each question, without new material.
11. **References and citations** (weight 1): in-line citations for all outside data, models
    and figures; real, specific, primary sources. **Cap at 4 for uncited data or figures, and
    at 2 for any citation that looks fabricated.**
12. **Presentation and rules** (weight 1): within 25 pages; at least 12pt; table of contents;
    figures labeled, discussed, and readable in grayscale; captions that lead with the finding; logical flow; clean prose; each
    named method explained in plain words at first use; lists of numbers in tables or figures
    rather than prose; tables and figures placed with their text; no identifying names; team
    number on every page.

**Overall:** report the weighted mean and a **designation estimate**:

| Weighted mean | Estimate |
|---|---|
| ≥ 8.6 *and* no section below 7 *and* sections 5 and 6 at 9 or above | Outstanding contender |
| ≥ 7.8 | Finalist |
| ≥ 6.8 | Meritorious |
| ≥ 5.3 | Honorable Mention |
| below 5.3 | Successful Participant |

Override rules: if any explicit requirement is unanswered, the estimate is at most
Meritorious; if the summary has no results, at most Honorable Mention; if the paper is over
the page limit, drop one level.

**The judge's review must also contain:**
- A **requirement coverage table** listing every question or requirement with
  *answered / partial / missing* and the page or section.
- **The biggest weaknesses**, ranked by how much they cost the paper. Each needs its location,
  why a judge would penalize it, and a concrete fix the authors can make in one revision pass.
- **Consistency checks**: numbers in the text against `results.json` and the figures;
  variables used but never defined; assumptions never used; figures never discussed.
- **Reality checks**: any result whose magnitude, units or sign looks implausible.
