---
name: beelddenker
description: Turn an answer into a picture for a visual thinker. Use when the user types /beelddenker, or says things like "make it visual", "draw it", "show me a diagram", "too much text", "I lost the overview", "give me an image or metaphor", "maak het visueel", "teken het", "maak er een schema van", "te veel tekst", or asks for a picture of what was just said. Reduces the answer (by default the previous assistant reply, otherwise the text, file or topic given as argument) to its skeleton, picks one or two visual principles, exact (flow, function signature, commuting diagram, group action, state machine, order lattice, matrix, causal loop) or poetic (visual metaphor, tension field, metamorphosis, constellation), and renders them with the best visual medium available.
---

# Beelddenker

*Beelddenker* is Dutch for a visual thinker: someone who takes in a picture faster than a page
of text. The picture replaces the text. The user should grasp the structure at a glance and
read only what the picture cannot hold. Reply in the language of the conversation.

## Input

- No argument: the most recent substantive assistant answer in this conversation (skip short
  acknowledgements and tool chatter).
- Text or a file path: that content.
- A topic or question: answer it, visually from the start.

## Procedure

### 1. Skeleton

Reduce the answer to its skeleton before drawing anything. Work this out in thinking, not in
the reply:

- **Objects**: the nouns that matter. At most about seven.
- **Arrows**: transformations, causes, steps, dependencies. For each: what goes in, what comes out.
- **Order**: sequence, hierarchy, containment, partial order, or none.
- **Laws**: what is equal (two routes, one result), what stays invariant under a change, what
  pulls against what.
- **The claim**: the one sentence the picture must make obvious.

Drop everything that does not serve the claim. When more than about seven objects survive,
split into an overview picture plus one detail picture per interesting part.

### 2. Register: exact, poetic, or both

- **Exact** when the content has structure that can be wrong: procedures, code, architecture,
  proofs, decisions, comparisons. The picture must be checkable.
- **Poetic** when the content is about meaning, judgement, a line of thought, values, a dilemma,
  a philosophical position; or when the exact structure is trivial and the insight lies in how
  it feels. The picture must be evocative, not complete.
- **Double image** (both) when an exact answer has a deeper why: first the exact schema, then
  one small metaphor that carries the why. Two pictures at most, except for overview plus detail.

### 3. Principle

Pick by the shape of the skeleton. Each principle, with what to draw and its pitfalls, is in
[references/principles.md](references/principles.md); read the entry before drawing.

| Shape of the skeleton | Principle |
|---|---|
| steps and decisions | flow |
| a transformation with typed input and output; a chain of them | function / pipeline |
| two routes that should give the same result; an equivalence; a refactor that keeps behaviour | commuting diagram |
| operations that combine and undo; symmetry; what survives a change | group action (Cayley graph, orbit, invariant) |
| modes and the events that switch between them | state machine |
| things inside things; layers | nesting / layers |
| "more general than", "depends on", "builds on" | order (Hasse diagram, DAG) |
| options against criteria | matrix / 2×2 |
| a trade-off along one dimension | spectrum |
| causes that feed back | causal loop (+ / −) |
| actors over time | timeline / swimlanes |
| a line of thought, a search, a journey of understanding | metaphor: landscape / journey |
| two poles that pull at each other | tension field |
| something changing in nature, not just in amount | metamorphosis |
| loosely related ideas without a hierarchy | constellation |

When two rows fit, prefer the one that makes the claim visible. When none fits, draw the
skeleton's objects and arrows as they are; do not force a principle.

### 4. Colour

- Colour encodes one dimension per picture: category, or intensity, or state. Never decoration.
- Say what it encodes in a one-line legend.
- Keep a concept's colour across the pictures in one conversation.
- Gray is structure and the neutral; warm (amber, coral) is active, costly, attended to;
  cool (teal, blue) is stable, calm, resolved; red only for wrong or broken.

### 5. Medium

Use the best medium available here, as set out in [references/medium.md](references/medium.md):
an inline visual in the Claude apps, an artifact when the picture is to be kept or shared or
no inline tool exists, Unicode diagrams in a plain terminal, Mermaid or JSON Canvas for
Obsidian, tikz-cd in a paper.

### 6. Text around the picture

- One line before: what the picture shows.
- At most three short lines after: what the picture cannot hold (a number, a caveat, the next
  step). Do not retell the picture in prose.
- Labels of at most five words. Detail goes into click-through nodes where the medium has them.

### 7. Check before sending

- Can the claim be read from the picture alone?
- Does every colour mean something, and is it in the legend?
- Does every arrow have a clear source, target and meaning?
- Is anything drawn that is not in the skeleton? Remove it.
- Commuting diagram: do both paths really give the same result? If not, draw it as
  non-commuting and mark where they differ.
- Metaphor: does each relation in the image mirror a relation in the idea (see the metaphor
  section in principles.md)? A pretty image that maps nothing is noise.
