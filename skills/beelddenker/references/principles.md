# Principles

Each entry: when it fits, what to draw, and what goes wrong. The exact principles come first,
the poetic ones after.

## Exact

### Flow

- **When**: steps in order, with decisions that branch.
- **Draw**: one direction only (top-down or left-right). Rounded boxes for steps, a diamond or
  a box with a question for decisions, labelled exits (yes / no). At most five nodes per picture;
  more becomes overview plus detail.
- **Pitfall**: a feedback arrow that crosses the whole layout. Mark a loop with `↻ back to X`
  at the point where it returns, or use a stepper (see medium.md) when the cycle is the point.

### Function / pipeline

- **When**: something is transformed; the types of what goes in and comes out matter.
- **Draw**: `input type → [ f ] → output type`, the function as a box, the types on the arrows
  or as small tags. A pipeline is a row of these where each output type is the next input type,
  so a mismatch is visible as two different tags meeting. Side effects (disk, network, screen)
  as a separate coloured lane under the pipeline.
- **Pitfall**: boxes named after nouns ("database") instead of verbs ("read rows"). A function
  box carries a verb; data carries a noun.

### Commuting diagram

- **When**: two routes lead to the same result. Equivalent formulations, a refactor that keeps
  behaviour, "first A then B equals first C then D", caching (compute vs look up), a translation
  that respects structure (a functor), a natural transformation between two ways of doing
  something.
- **Draw**: objects at the corners, morphisms as labelled arrows (`f`, `g`, or a short verb).
  The square or triangle carries `↻` in its middle and the equation underneath:
  `h ∘ f = k ∘ g`. For a functor, draw the source category on the left and its image on the
  right, with dashed arrows mapping each object. For a natural transformation, two parallel
  arrows F, G between the same pair and a double arrow `⇒` between them.
- **Pitfall**: claiming commutation that only holds up to something (rounding, ordering, an
  extra condition). Then mark the cell `≈` or `≠` in red and say in one line what breaks it.
  That gap is often the most interesting part of the answer.

### Group action (symmetry, invariant)

- **When**: operations that compose and can be undone; symmetries; "what stays the same when
  you change X"; rotations, reflections, permutations, undo/redo, equivalence classes.
- **Draw**:
  - Cayley graph: elements as small labelled dots, one arrow colour per generator (rotation r
    in one colour, reflection s in another). For a cyclic group the ring is meaningful: draw it.
  - Orbit: one object and its images under the group, arranged around it; the invariant written
    in the middle ("distance to the centre stays the same").
  - Quotient: the orbits as coloured blobs, each blob becoming one point in a smaller picture.
- **Pitfall**: more than about eight elements. Draw the generators and one orbit, not the group.

### State machine

- **When**: a system with modes and events that switch between them (a ticket, a session,
  a review process, a mood).
- **Draw**: states as rounded boxes, transitions as arrows labelled with the event. Start state
  with a small filled dot pointing in, end states with a double border. Colour by kind of
  state (waiting, active, done, failed).
- **Pitfall**: drawing actions as states. A state is something you are in; an event is something
  that happens.

### Nesting / layers

- **When**: things inside things; layers that build on each other (a stack, an architecture,
  scopes, a cell).
- **Draw**: nested rounded rectangles, the outermost lightest; or a vertical stack of slabs
  with the foundation at the bottom. Each region gets a name and at most five words on what
  happens there. At most three levels of nesting.
- **Pitfall**: arrows between deep inner boxes across containers. Route them along the edge or
  split the picture.

### Order (Hasse diagram, DAG)

- **When**: "is more general than", "depends on", "builds on", "implies", prerequisites.
- **Draw**: bottom to top (general or foundational at the bottom) without arrowheads for a
  partial order, or with arrows for dependencies. Only the covering relations: leave out what
  follows by transitivity.
- **Pitfall**: drawing every relation; the picture turns into a hairball.

### Matrix / 2×2

- **When**: options against criteria; choosing.
- **Draw**: a 2×2 with two named axes and the options placed as dots, or a small table where
  colour encodes the score (one ramp, light = weak, dark = strong). Mark the recommendation.
- **Pitfall**: axes that are not independent. If the two axes move together, it is a spectrum.

### Spectrum

- **When**: a trade-off along one dimension (speed vs. accuracy, freedom vs. structure).
- **Draw**: one horizontal axis with the two poles named at the ends, the options as markers on
  it, and where we stand (or should stand) as a highlighted marker.
- **Pitfall**: hiding a second dimension. Then use the 2×2.

### Causal loop

- **When**: causes that feed back; growth, saturation, vicious and virtuous circles.
- **Draw**: variables as words (no boxes), arrows marked `+` (same direction) or `−` (opposite).
  Mark each loop `R` (reinforcing) or `B` (balancing) in its middle. Warm colour for the
  reinforcing loop, cool for the balancing one. Delays as `‖` on the arrow.
- **Pitfall**: mixing events and variables. Every node must be something that can go up or down.

### Timeline / swimlanes

- **When**: several actors over time; who does what when; hand-overs.
- **Draw**: one horizontal lane per actor, time left to right, hand-overs as vertical arrows
  between lanes. Today as a vertical line.
- **Pitfall**: more than four lanes.

## Poetic

A metaphor works like a functor: the relations in the image must mirror relations in the idea.
Before drawing, list the correspondence (thinking only): image element ↔ concept, image
relation ↔ concept relation. If an important relation in the idea has no counterpart in the
image, choose another image. Under the picture, one quiet line may name the mapping
("the river = the argument, the side channels = the objections it does not follow").

Style: few shapes, flat colours, suggestive rather than complete; space around the image.
A short caption in a serif voice is allowed. Colour still means something: warm where the
energy or tension is, cool where it settles, gray for the ground.

### Landscape / journey

- **When**: a line of thought, a search, a learning path, a project with phases.
- **Images**: a path through a landscape (switchbacks for iterating, a ridge for a point of no
  return, fog for what is unknown); a river with its delta (one source, choices that branch and
  do not merge again); a staircase or mountain with camps; stepping stones over water.

### Tension field

- **When**: two poles that pull at each other; a dilemma; a dialectic.
- **Images**: two weights on a balance with the considerations as small stones on each side; two
  magnets with field lines and the position in between; thesis and antithesis as two curves that
  meet in a synthesis one level higher (a spiral, not a circle: the return is never to the same
  place).

### Metamorphosis

- **When**: something changes in nature, not only in amount: a role, an understanding, a design
  paradigm.
- **Images**: caterpillar, cocoon, butterfly as three simple shapes; ice, water, steam; a seed,
  a sprout, a tree with its roots showing the origin. Mark what is preserved through the change
  (the invariant) in one colour across all stages.

### Constellation

- **When**: loosely related ideas without hierarchy; a field of associations; inspirations.
- **Images**: ideas as stars of different size (importance) on an empty field, faint lines
  between those that belong together, one constellation named. Or an archipelago: islands of
  thought, shallow water where they almost touch.

### Other images worth reaching for

| Image | Carries |
|---|---|
| lens, focus | perspective, what one frame shows and hides |
| sieve, filter | selection, what passes and what stays behind |
| sediment, layers of rock | accumulated history, legacy |
| weaving, threads | combining strands into something stronger |
| knot | entanglement, a problem that tightens when pulled |
| bridge | connecting two domains, translation |
| tide | slow periodic change, patience |
| compass | orientation without a fixed route |
| lighthouse | a fixed principle seen from far away |
| scaffolding | temporary structure that makes something permanent possible |
