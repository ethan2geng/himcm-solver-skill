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

