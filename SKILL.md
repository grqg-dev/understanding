---
name: understanding
description: >
  Turn agent-created code, diffs, plans, investigations, architecture, or other
  technical work into a Sideshow explanation optimized for understanding. Use
  when the user invokes /understanding or asks to understand what an agent made,
  how a system works, why a change exists, or what matters in a body of work.
disable-model-invocation: true
---

# Understanding

Create a short Sideshow session that gives the user a durable mental model of
the work. The goal is not coverage. The goal is that the user can explain the
core idea, predict important behavior, and know where to look next.

Do not quiz or test the user.

## Start

1. Run `sideshow agent-howto` once per session.
2. Run `sideshow guide` before the first HTML publish.
3. Follow those documents for connection, publishing, surface selection,
   presentation, updates, and feedback. Do not reproduce their instructions in
   the explanation.
4. Identify the exact work to explain. Ask only when the target is genuinely
   ambiguous.

## Investigate before teaching

Inspect enough source material to understand:

- the problem or goal that caused the work
- the relevant before-state
- the main actors, data, and boundaries
- the happy path and important failure paths
- the decisions, constraints, and trade-offs
- the concrete artifacts where the behavior lives

For code changes, explore surrounding callers, data flow, invariants, tests,
commit or PR context, and the diff. Do not explain hunks in isolation.

Separate observed facts from inference. If intent is not documented, say what
the implementation does without inventing a rationale.

## Build the explanation

Use progressive disclosure. Publish one concept per post and add only posts
that materially improve understanding. Open every post with its single
takeaway in one line; put detail after, so an expert can read first lines
only and still get the model.

Target 3–7 posts. For small work, collapse Background into Orientation.
Never pad to fill the structure.

### 1. Orientation

Open with a headline: the entire work in one sentence of at most ~20 words.
Then answer immediately:

- What is this?
- Why does it exist?
- What changed or was produced?
- Why should the user care?

Give the before-to-after idea in one or two sentences. Name the central concept
before introducing supporting details.

### 2. Background

Provide two layers:

- **Deep background, clearly skippable:** enough for a newcomer to place the
  work in the larger system. Define only the nouns and flow needed later.
- **Narrow background:** the exact before-state, invariant, limitation, or
  failure mode needed to understand this work.

Avoid generic primers, unrelated architecture tours, and project history that
does not unlock the explanation.

### 3. Core intuition

Make the causal model concrete:

1. State: “We used to X; now we Y because Z.”
2. Use one tiny representative example with real-looking toy data.
3. Show old behavior and new behavior explicitly.
4. Name the most likely wrong assumption — “you might expect X; actually Y,
   because Z” — and correct it explicitly. Skip this if no plausible
   misconception exists; never invent one.
5. Include a diagram or figure when the idea concerns flow, state, structure,
   ownership, timing, or transformation.
6. Bridge the idea to the 1–3 most important files, symbols, decisions, or
   outputs.

Choose examples that expose the reason for the work, not merely the happy path.

### 4. Walkthrough

Trace one representative scenario end to end. At each step explain:

- what happens
- why it happens
- what state or data changes
- where it happens

Frame pivotal steps around the question a reader would naturally ask at that
point (“what happens if the lookup misses here?”) and answer it immediately
in the same post. Never leave a question hanging for the user to answer.

For a code change, pair the walkthrough with focused code or diff surfaces.
Show only the lines needed to connect the mental model to the implementation.

### 5. Consequences

Answer three questions, each only as far as the evidence supports:

- **What is now true?** Behavior that is now possible or impossible,
  operational or user-visible impact, and what remains unchanged.
- **What breaks it?** Edge cases, failure behavior, trade-offs and rejected
  alternatives when evidenced, and where the simplified model from the core
  intuition stops matching reality.
- **Where do you go next?** The small set of places to inspect when
  debugging or extending the work, and the tests or evidence that support
  the claims above.

End with a compact “mental model to keep” statement — one or two sentences a
reader could repeat a week later — not a recap of every post.

## Adapt to the artifact

- **Diff or PR:** emphasize before-state, changed control/data flow, invariants,
  and why the patch has its shape.
- **Generated feature:** emphasize user-visible behavior, runtime path, stored
  state, external effects, and validation.
- **Architecture:** emphasize boundaries, ownership, data movement, and failure
  containment.
- **Plan:** emphasize desired outcome, dependencies, sequencing, decision
  points, and irreversible choices.
- **Investigation or report:** organize as claim → evidence → implication →
  action; distinguish facts from hypotheses.

## Quality bar

### Transfer test

Before finishing, answer each question using only the published posts, as if
you had not done the investigation. If an answer is missing, wrong, or
requires the source material, revise the posts. This test is run by you,
silently — the user is never quizzed.

1. **Core idea:** In one sentence, what is this and why does it exist?
2. **Prediction:** For the central example, what happens now that did not
   happen before — and what still fails?
3. **Location:** A bug appears in this behavior tomorrow. Which file or
   symbol do you open first, and which post says so?
4. **Misconception:** What would a reasonable reader wrongly assume, and
   which post corrects it? (Pass vacuously if none exists.)
5. **Limits:** Where does the simplified model stop matching reality, and
   is that visible in the posts?

### Craft checks

- The explanation starts with purpose and causality, not implementation detail.
- Every post opens with its takeaway and teaches one concept that earns its
  place.
- Concrete examples replace abstract prose where possible.
- Visuals reveal a relationship; they are not decorative.
- Actual artifact names anchor the model without overwhelming it.
- An expert can skip background while a newcomer can still follow.
- Feedback is checked and meaningful revisions update existing posts.
