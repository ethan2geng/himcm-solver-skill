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

