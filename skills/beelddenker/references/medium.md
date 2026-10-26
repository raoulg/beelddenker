# Medium

Pick the first that is available and fits.

## 1. Inline visual (Claude desktop app, claude.ai)

When a tool for inline visuals is available, use it. In the Claude desktop app it is
`mcp__visualize__show_widget` (possibly deferred: load it with ToolSearch). Before the first
widget in a conversation, call `mcp__visualize__read_me` without mentioning it, with the
modules that fit:

| Register | Modules |
|---|---|
| exact schema | `diagram` |
| poetic metaphor | `art`, `diagram` |
| something to operate (rotate a group, step through a cycle, move a slider) | `interactive`, `diagram` |
| numbers | `chart` |

Then follow its rules (680-wide viewBox, its colour classes, dark mode, sentence case). Use:

- One picture per call; a line of text between two pictures.
- Clickable nodes with `sendPrompt('...')` for detail, so labels can stay short.
- A stepper (HTML, one panel per stage, Next wraps around) for cycles, instead of a ring of boxes.
- Interactive for group actions and dynamics: a button per generator that rotates or reflects
  the object, a slider for the parameter of a trade-off.

## 2. Artifact

When the user wants to keep, share or present the picture, when the picture set is too large
for inline, or when no inline tool exists (claude.ai chat without inline visuals): an SVG or
HTML artifact with inline SVG, following the artifact tool's own rules. Flat colours, one
semantic colour dimension, readable in light and dark mode.

## 3. Obsidian

When the picture goes into an Obsidian vault:

- Mermaid in a fenced `mermaid` block for flows, state machines, sequence and dependency graphs
  (Obsidian renders it).
- A JSON Canvas (`.canvas`) for constellations, maps and anything spatial.

## 4. Paper or LaTeX

`tikz-cd` for commuting diagrams, TikZ for the rest, so the picture lives in the source.

## 5. Plain terminal

No visual tools: draw with Unicode box characters in a ```` ```text ```` fence. Keep it under
about 70 columns. Colour is not available, so encode with line style instead: `──▶` main path,
`┄┄▶` secondary, `═══` emphasis, and say so in a legend line.

Function and pipeline:

```text
         ┌──────────┐         ┌──────────┐
 str ───▶│ tokenize │──[tok]─▶│  embed   │───▶ ℝⁿ
         └──────────┘         └──────────┘
```

Commuting square:

```text
   A ────f───▶ B
   │           │
   g     ↻     h          h ∘ f = k ∘ g
   ▼           ▼
   C ────k───▶ D
```

Cayley graph of C₄ (rotation r):

```text
    e ───r───▶ r
    ▲          │
    r          r
    │          ▼
   r³ ◀───r─── r²
```

Causal loop:

```text
     users ──(+)──▶ value
       ▲               │
      (+)      R      (+)
       │               ▼
   reputation ◀─(+)── contributions
```

Spectrum:

```text
  freedom ●────────○──────◉──────────● structure
                  wiki    now
```
