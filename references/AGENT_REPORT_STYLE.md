# Agent Report Style

Use this file whenever an agent writes prose for a human reader. It covers voice, anti-slop rules, and (when needed) report shapes.

The goal is fast understanding in sharp, human writing. A reader should be able to stop after the opening and know the result, continue through the core argument to understand why, and use the appendix only when they need to verify the work.

## Scope

**Apply the writing rules in this file to every document an agent makes** — investigations, findings, code/diff explainers, decision reports, plans, QA notes, MR/PR descriptions, Jira comments that are substantive prose, Cloud Agent `## Explanation` handoffs, and any other markdown or long-form writeup.

Full report shapes (Findings / Code explainer / Decision / Cloud-agent MR) still apply only when the deliverable is that kind of document. Ordinary plans, UAT CSVs, runbooks, `LEARNINGS.md` entries, and code comments keep their existing formats for structure — but the **No AI slop** rules still apply to any prose in them. Cloud-agent MRs use the [Cloud-agent MR description](#cloud-agent-mr-description) (default or slim).

Skip this file for routine chat, progress updates, clarification questions, acknowledgements, and machine-readable output.

## Load rule (cloud agents)

When `bash .cursor/cloud-agent/scripts/detect-mode.sh` prints `CLOUD`, read this file in full at session start together with [`CLOUDAGENTS.md`](CLOUDAGENTS.md) and [`.cursor/cloud-agent/WORK_LOOP.md`](.cursor/cloud-agent/WORK_LOOP.md). Do not wait until the writeup moment to discover the style.

## Where the report lands

Pick one surface. Do not also commit a duplicate writeup under `docs/investigations/` (or similar) unless the user explicitly asks for a repo file.

| Situation | Put the report here |
|---|---|
| Cloud-agent code/metadata MR (ordinary or investigate→fix) | **MR description** — [Cloud-agent MR description](#cloud-agent-mr-description) (default or slim). Put the writeup on the live Gearset replacement MR |
| Investigation or answer with no MR | Final agent response (`## Explanation` for cloud-agent terminal handoffs). Optional downloadable artifact only if the caller needs one |
| User explicitly asks for a standalone report file | Tracked path they name (cloud: category dir; local: `docs/**/drafts/`) |
| Local / human MR without a cloud-agent explainer need | Short factual MR ([`.cursor/rules/gitlab-mr-creation.mdc`](.cursor/rules/gitlab-mr-creation.mdc)) — still follow No AI slop |

Cloud agents: the durable place for an investigate→fix writeup is the **live Gearset replacement MR**, not a committed markdown file. See [`CLOUDAGENTS.md`](CLOUDAGENTS.md) → *Explanation handoff* and *MR lifecycle*.

## Core standard

Write the smallest document that fully explains the subject.

- Lead with the finding, change, or recommendation and why it matters.
- Add only the background the intended reader needs.
- Support material claims with concrete evidence.
- Distinguish observed facts, reasoned inferences, and recommendations.
- Explain mechanisms with examples, not abstractions alone.
- Put reproducibility details and exhaustive evidence in an appendix (or a collapsed `<details>` block on an MR).
- Stop when additional words no longer improve understanding or decisions.

Length is a constraint, not a goal. Most findings and decision reports should stay under about 800 words, and most code explainers under about 1,200 words, excluding appendices. Go longer when compression would omit necessary context, evidence, or examples. There is no minimum.

---

## No AI slop

Write like a sharp human editor and colleague. Make the prose clearer and more alive. Remove AI patterns without turning every paragraph into the same generic polished voice.

When the user asks you to edit or audit a draft they wrote, preserve their point and personal voice. When you are the author, still avoid the patterns below — direct, concrete, and specific beats tidy-sounding filler.

### Two jobs (when the user hands you a draft)

**Edit (default).** The user shares a draft to fix. Make the minimum effective edit with the rules below and return the edited draft plus a What changed section.

**Detect.** The user asks whether a piece is AI slop, or asks to audit, scan, or flag a draft without rewriting. Name each pattern from this file that appears, quote the line, and give the fix in a few words. Do not rewrite, score the draft, or guess whether AI wrote it. AI detectors guess. Named patterns are evidence the user can check. Offer to edit the draft after.

If the user has not provided a draft for an edit/detect request, ask them to paste it. If audience or format is unclear, ask one question: Who is this for and where will it be published? If the goal is unclear, ask what the reader should think, feel, or do after reading it.

### Writing principles

- **Keep a real voice.** Notice vocabulary, cadence, bluntness, humor, uncertainty, digressions, and level of polish. When editing a human draft, keep the traits that feel personal to the writer. Do not make every paragraph equally tidy or rewrite distinctive lines merely for consistency.
- **Make the minimum effective edit.** Fix AI patterns, errors, repetition, and unclear passages. Leave strong human sentences alone. A rough draft with a real voice should still sound like the same person after editing.
- **Lead with the point when the setup adds nothing.** Cut generic throat-clearing. Keep a personal aside, story, or admission when it creates context, tension, or character.
- **Front-load only when it improves clarity.** Put conclusions early when that helps the reader. Do not force every section and paragraph into the same point-detail-background shape.
- **Keep the meaning.** Don't invent claims, examples, stats, or opinions. If something is unclear, ask.
- **Open it up, don't dumb it down.** Keep the substance, nuance, and precision. Strip out only what makes it hard to read: jargon, long sentences, abstract nouns, and tangled structure.
- **Use active voice.** "The team shipped it Tuesday" beats "the decision emerged." Never let inanimate things do human verbs.
- **Make every sentence earn its place.** Cut empty qualifiers and throat-clearing. Keep phrases such as "I think," "maybe," or "to be honest" when they express real uncertainty, self-awareness, or spoken rhythm.
- **Untangle sentences without flattening the cadence.** Split sentences and paragraphs when they are genuinely hard to follow. Keep longer spoken sentences, fragments, and changes in pace when they are clear and characteristic.
- **Be concrete and specific.** Abstraction is where writing goes to die. "The integration improved efficiency" becomes "The integration cut deploy time from 40 minutes to 4." Names, numbers, dates, mechanisms, and examples beat abstractions.
- **Protect the specific fact.** Don't smooth a useful detail into generic importance. "The tool significantly improves engineering productivity" becomes "The tool cut review time from 30 minutes to 8."
- **Make verbs do the work.** Replace weak verb phrases with direct verbs. "Made a decision" becomes "decided." "Has the ability to" becomes "can."
- **Know the job.** Before structure or word choice, know what the piece is trying to do and who it is for.
- **Preserve useful edge and character.** Keep strong opinions, blunt language, humor, self-interruptions, and honest admissions when they belong. Don't replace them with safer or more professional wording.
- **Keep structure unless it's hurting the piece.** Preserve progression and detours when they carry meaning. If you reorganize a human draft, say why in the What changed section.

Technical language is appropriate for a technical audience. Do not replace an accurate term such as `deploy`, `trigger`, or `queueable` with a vague plain-language substitute.

### Words to cut

Banned outright: delve, foster, leverage, utilize, facilitate, empower, streamline, robust, cutting-edge, paradigm shift, game changer, this is huge, this changes everything, tapestry, realm, beacon, multifaceted, meticulous, intricate, paramount, transformative, elevate, embark, supercharge, harness, ever-evolving.

Often-empty adverbs: just, literally, honestly, simply, actually, truly, fundamentally, importantly, crucially, inherently, inevitably. Cut them when they add nothing. Keep them when they carry emphasis, uncertainty, contrast, or natural spoken rhythm.

Often-empty phrases: it's worth noting, it's important to note, at the end of the day, when it comes to, at its core, in today's world, in the age of, in the world of, the reality is, the truth is, in terms of, with regard to, in order to, going forward, in this article, let's dive in. Cut them when they delay the point. Keep an occasional phrase when it is part of a recognizable voice and the sentence still earns its place.

| Avoid | Write instead |
|---|---|
| "This report provides an overview of…" | Start with the finding or change. |
| "It is important to note that…" | Delete it and state the fact. |
| "In order to" | "To" |
| "Utilize" or "leverage" | "Use" |
| "Could potentially" | "Could" |
| "Various" or "several" | Name or count the items. |
| "Robust," "seamless," or "comprehensive" | Name the behavior or measurable outcome. |
| "It was observed that the test failed" | "The test failed." |

### Patterns to cut

**Binary contrasts.** "This is not X. It's Y." / "The question isn't X, it's Y." / "It's not just X but Y." State Y directly. "The question isn't the model. It's the eval." becomes "The eval matters more than the model."

**Throat-clearing openers.** "Here's the thing," "Here's what I mean," "Let me be clear," "I'll be honest," "The uncomfortable truth is." Cut them and state the point.

**Faux-insight setups.** "This is the part most people skip," "What most people get wrong," "Here's what nobody tells you," "The part everyone misses." These flatter the writer as the lone expert. Cut the setup and make the claim stand on its own. "The part everyone misses: distribution is the real moat" becomes "Distribution is the moat."

**Colon reveals.** A noun phrase, a colon, then a lowercase dramatic reveal: "The detail that makes it work: a separate agent grades it." "The best part: it learns." Rewrite as a plain sentence ("A separate agent does the grading, which is what makes it work"). Use colons for lists, labels, and quotes, not fake drama. Prefer sentence case after a colon unless grammar, a proper noun, a title, or code requires otherwise.

**Superficial analysis.** Cut trailing `-ing` clauses that pretend to explain meaning: "highlighting," "underscoring," "reflecting," "showcasing." "The launch adds file search, highlighting the team's commitment to better workflows" becomes "The launch adds file search, so users can find old drafts without leaving the editor."

**Importance puffery.** "Stands as a testament," "marks a pivotal moment," "plays a vital role," "solidifies its position," "underscores its significance." State the fact and let the reader judge whether it matters. "The launch marks a pivotal moment for the company" becomes "The launch is the company's first paid product."

**Weasel attribution.** "Experts agree," "industry reports suggest," "many argue," "widely regarded as," "studies show." Name the source or cut the claim. If there is no source, ask instead of inventing one.

**Fake-strong verbs.** Prefer "is" and "has" when they are clearer. "The app serves as a centralized hub for sponsor management" becomes "The app tracks sponsors, drafts, due dates, and approvals in one place."

**Synonym cycling.** If the clear word is right, repeat it. Don't rotate terms for style. "The agent reviews the draft. The assistant scores the piece. The tool suggests fixes" becomes "The agent reviews the draft, scores it, and suggests fixes."

**Negative listing.** "Not a X. Not a Y. A Z." Just say Z.

**Dramatic fragmentation.** "X. And Y. And Z." or "That's it. That's the whole thing." Use complete sentences.

**Robotic rhythm.** Avoid repeated sentence shapes, identical paragraph structures, and stacked punchy fragments. Vary the shape only when it helps the point.

**Rhetorical setups.** "What if I told you...", "Think about it:", "Plot twist:", and self-answered "Question? Answer." pairs. Drop them and make the point.

**Fake-profound kickers.** Cut the final "deep" line when it turns the point into a cute metaphor, aphorism, or mic-drop sentence. Do not rewrite it into a better metaphor. Do not preserve the rhythm. Delete it, then end on the clearest concrete sentence already in the draft. If the ending needs more closure, add a plain takeaway or next action.

**Summary-recap endings.** "In conclusion," "Ultimately," "Overall," or a final paragraph that restates the piece. The reader was just there. End on the last concrete point, takeaway, or next action instead.

**Formatting slop.** Emoji in headings, bold sprinkled mid-sentence for emphasis, bullet lists where two sentences of prose would read better, and headers over two-sentence sections. Format should follow the content, not decorate it.

**Em dashes.** Do not use them as a default rhythm crutch. In short copy, use none. In longer drafts, 1-2 are fine if they clearly beat commas, periods, or parentheses. Remove clusters and decorative dashes.

### Edit / detect workflow

When editing or auditing a draft (or when polishing your own writeup before delivery):

1. Read the full draft before editing.
2. Identify the core point and 3-5 voice signals to preserve (vocabulary, cadence, bluntness, humor, uncertainty, digressions). Keep this note internal. If you cannot identify the core point, ask.
3. For a detect request, return the findings described under Two jobs and stop.
4. For an edit or agent-authored doc, make the minimum effective changes, then self-check against **Words to cut**, **Patterns to cut**, and the **Review rubric** below.
5. If any check fails, fix the draft and run the checks again.
6. For a user-requested edit, output the full edited draft and a short **What changed** section.

---

## Choose one report shape

Use the closest shape when the deliverable is a findings report, code explainer, decision report, or cloud-agent MR. Omit sections that do not help. Do not combine templates merely to make a report look complete.

For cloud-agent MRs (including investigate→fix), use **Cloud-agent MR description** below — not a pasted Findings report plus Code explainer. Fold finding / evidence / cause into Background (and the opening) when the MR exists because of an investigation.

Cloud-agent terminal handoffs use the shorter WORK_LOOP `## Explanation` shape (Background + Intuition). When it helps, add one short **consumer** beat (who feels the change) and one **maintainer** beat (what the next owner inherits). The durable explainer for merged work is the MR body. Expand into the full Code explainer only when the user asks for a walkthrough or the change is hard to understand from Background + Intuition alone.

### Cloud-agent MR description

Canonical MR body for cloud agents. House adaptation of [Explain Diff](https://gist.github.com/geoffreylitt/a29df1b5f9865506e8952488eac3d524): Background, Intuition, behavior-grouped Changes, Testing proof — **no quiz**, no HTML explain-diff page as the MR body, no duplicate committed investigation writeup.

**Default** — use when a reviewer needs more than the title + diff to understand the change:

```markdown
<1–2 sentence behavioral result + why it matters>

## Background

<details>
<summary>System primer (skip if familiar)</summary>

What this area of the system does: entry points, main objects/services, data flow.
Only enough for a new reviewer to follow the change.

</details>

Narrow context: the existing behavior or constraint this MR touches.

## Intuition

Essence in 1–2 sentences.

Before → after with toy data (one concrete example).
Mermaid only if sequence or data flow is hard to see in prose.

## Changes

- Metadata type: `ApiName` — what it does now (behavior, not a file tour)
- …

Group by responsibility when there are more than ~3 components.
Call out surprising choices and edge cases inline.

## Testing proof

Org: `AGENT_DEV` (or note if N/A).

- Tests: X/X pass; coverage for each changed class/trigger (≥80% when Apex)
- Functional checks / queries / scenarios
- Screenshots when the evidence rubric requires them:

<img alt="…" src="/absolute/path/to/screenshot.png" />
```

**Slim** — agent-judged. Use only when a reviewer can understand the MR from the title + diff alone (typical: formula field, FLS, label, layout field add, one-line fix). If the agent needed more than a sentence of “why,” use the default template.

```markdown
<1–2 sentence result>

## Changes
- Metadata type: `ApiName`

## Testing proof
- …
```

**Investigate → fix:** same spine. Put Finding / Evidence / Cause under **Background** (or briefly in the opening). Put Recommendation into **Intuition** + **Changes**. Do not paste Findings report and Code explainer end to end.

**Length budget**

| Section | Default | Slim |
|---|---|---|
| Opening | ≤50 words | ≤40 |
| Background | primer optional; narrow ≤150 words | omit |
| Intuition | ≤120 words + one example | omit |
| Changes | bullets; walkthrough only if non-obvious | bullets only |
| Testing proof | strongest evidence; Apex numbers when Apex changes | required |

**Non-goals:** quiz; HTML explain-diff as the MR body; `## Behavior` as a separate section (that content belongs in Intuition / Changes); duplicate `docs/investigations/` writeup unless the user asked for a repo file.

Pointers: [`.cursor/rules/gitlab-mr-creation.mdc`](.cursor/rules/gitlab-mr-creation.mdc), [`CLOUDAGENTS.md`](CLOUDAGENTS.md) → *What to deliver*, screenshot rubric in [`CLOUDAGENTS.md`](CLOUDAGENTS.md) → *Evidence rubric*.

### Findings report

Use for root cause analyses, investigations, audits, and QA findings — including standalone investigation writeups with **no** MR. When an investigation produces a fix MR, use **Cloud-agent MR description** and fold findings into that spine instead of this full template.

Borrow the explain-diff spirit without copying its quiz: give enough system context that a new reader can follow the cause, and teach the mechanism with a concrete example—not only a list of facts.

1. **Finding and impact** — State what happened, who or what it affects, and its significance. Keep the opening under 100 words.
2. **Evidence** — Give the few facts that establish the finding. Quantify scope when possible. Name environments and dates for mutable prod observations.
3. **Cause** — Explain the causal chain from trigger through mechanism to outcome. Separate the root cause from symptoms and contributing conditions. When the mechanism is non-obvious, fold in:
   - a short **Background** (skippable system primer, then the behavior directly in play)
   - an **Intuition** beat with a before/after toy example (and a Mermaid diagram only if it clarifies sequence or data flow better than prose)
4. **Recommendation** — State the fix, decision, or next action. Say when no action is needed. On an investigate→fix MR, fold this into Intuition + Changes on the Cloud-agent MR spine instead of ending here.
5. **Appendix, if needed** — Put queries, commands, raw results, detailed reproduction steps, and exhaustive examples here (or in `<details>` on an MR).

If the cause is unknown, say so. Report what the evidence rules in or out and what would resolve the uncertainty.

### Code explainer

Use for a standalone walkthrough of a diff, branch, pull request, or existing system when the reader needs more depth than the Cloud-agent MR spine (or when there is no MR). For ordinary cloud-agent MRs, prefer **Cloud-agent MR description**. This is the house adaptation of [Explain Diff](https://gist.github.com/geoffreylitt/a29df1b5f9865506e8952488eac3d524): layered background, intuition with toy data, and a behavior-grouped walkthrough—without a quiz.

1. **Change and impact** — Explain the behavioral change and why it matters.
2. **Background** — Start with a beginner-friendly primer on the surrounding system, then narrow to the existing behavior directly relevant to the change. Explore enough adjacent code to explain entry points, responsibilities, data flow, and dependencies. Mark the primer as skippable for experienced readers.
3. **Intuition** — State the essence of the change in one or two sentences. Show a concrete before/after example with realistic toy data. Add a Mermaid (or other) figure when it materially clarifies a nontrivial relationship, sequence, or data flow.
4. **Before and after** — Trace the important behavior or data flow on both sides of the change.
5. **Code walkthrough** — Group changes by behavior, responsibility, or data flow—not by file order unless that is the clearest dependency order. Call out surprising choices and tricky edge cases.
6. **Risks and verification** — Identify meaningful edge cases, tradeoffs, and the evidence that the change works.

Use Markdown. Do not add an interactive quiz or generate HTML unless the user explicitly requests either. Add a diagram only when it makes a relationship materially easier to understand than prose or a small example.

### Decision report

Use when a standalone report must drive a technical or operational choice. Ordinary implementation plans keep their existing format — still under No AI slop.

1. **Recommendation** — State the proposed decision and expected outcome.
2. **Problem and constraints** — Explain the current condition, evidence, and limits that shape the choice.
3. **Options and tradeoffs** — Compare only credible alternatives. Make the reason for rejecting each alternative explicit.
4. **Proposed approach** — Describe the important implementation or operating model.
5. **Risks and open questions** — Include real uncertainties and the decision or evidence needed to close them.

## Write for fast understanding

### Put the answer first

The title should identify the subject. The opening should state the result, decision, or behavioral change—not announce that a report exists.

Do not repeat the opening as a conclusion. End with the recommendation, unresolved question, or implication that moves the reader forward.

### Make evidence easy to judge

- Attach every material conclusion to code, a query, a test, a log, observed behavior, or another named source.
- Give a denominator, comparison, or baseline for numbers when one is needed to interpret them.
- Date mutable observations and name the environment where they were observed.
- Cite code with stable identifiers such as file paths, classes, methods, flows, or components. Add line numbers only when the reference is tied to a specific revision.
- Summarize evidence in the body. Put long commands, raw output, and full reproduction steps in the appendix.
- State uncertainty directly. Use words such as "likely" only when the report explains the evidence behind that judgment.

### Explain with concrete examples

Use the smallest example that exposes the mechanism. Prefer a before/after case, a short data-flow trace, or a compact table over a broad hypothetical. Use synthetic or non-sensitive data.

An example supports the explanation; it does not replace evidence that the real system behaves the same way.

### Design for scanning

- Use descriptive, sentence-case headings.
- Keep one main idea per paragraph.
- Use bullets for discrete items and numbered lists for sequences.
- Use a table when readers need to compare three or more items across the same attributes.
- Bold only the words a scanning reader must notice.
- Skip a table of contents unless the report is long enough to need navigation.
- Avoid decorative callouts, diagrams, emojis, and repeated status markers.

## Editing rule

Apply the removability test to every paragraph:

> If removing this paragraph would not change the reader's understanding, confidence, or next action, remove it.

Then check the opposite risk: if removing context would cause a reasonable reader to misunderstand the finding or make the wrong decision, restore the smallest explanation or example that closes the gap.

## Review rubric

Score each dimension from 0 to 2:

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Answer first | Result or purpose is missing | Result appears, but late or without impact | Opening states the result and why it matters |
| Reader context | Assumes too much or explains unrelated background | Enough context, with minor gaps or excess | Gives exactly the background needed |
| Evidence and certainty | Material claims are unsupported or overstated | Evidence exists but is incomplete or hard to judge | Claims are traceable; fact, inference, and uncertainty are clear |
| Reasoning and examples | Lists facts without explaining the mechanism | Explains the mechanism abstractly | Shows the causal or behavioral model with a concrete example |
| Structure | Dense, repetitive, or difficult to scan | Understandable with avoidable friction | Progressive detail, descriptive headings, and purposeful formatting |
| Compression | Contains windup, process diary, or repeated points | Mostly concise with some removable text | Every paragraph changes understanding, confidence, or action |
| Closure | Leaves the implication or next step unclear | Implied recommendation or conclusion | States the decision, action, unresolved question, or final implication |
| No AI slop | Banned words, puffery, or pattern stack present | Minor throat-clearing or empty adverbs remain | Voice is direct; concrete facts; no banned patterns |

A report is ready at 14 of 16 points, with no zero in **Answer first**, **Evidence and certainty**, **Reasoning and examples**, or **No AI slop**. Do not add filler to raise a score; revise or remove weak material.

For short non-report docs (plans, slim MRs, QA notes), apply the No AI slop dimension and the removability test. Skip dimensions that do not fit the format. Default cloud-agent MRs use the Cloud-agent MR description shape above.

## Influences

This style adapts principles rather than copying any source format:

- No AI slop (editing skill): banned filler, pattern cuts, minimum effective edit, preserve real voice.
- [Explain Diff](https://gist.github.com/geoffreylitt/a29df1b5f9865506e8952488eac3d524): layered background, intuition, concrete examples, and behavior-oriented code walkthroughs.
- [Amazon narrative documents](https://workingbackwards.com/concepts/narratives-decision-making/): complete reasoning, evidence, and disciplined length in place of presentation fragments.
- [Axios Smart Brevity](https://www.axioshq.com/hubfs/smart-brevity-101.pdf): audience-first writing, the important point first, and scannable structure.
- [18F Content Guide](https://guides.18f.org/content-guide/): plain language, active voice, descriptive headings, and the inverted pyramid.
