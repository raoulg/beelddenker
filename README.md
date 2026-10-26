# beelddenker

*Beelddenker* is Dutch for **visual thinker**: someone who takes in a picture faster than a
page of text. This is a skill for Claude that turns a long answer into a picture: a flow, a
commuting diagram, a group action, or a visual metaphor, whichever fits the thought.

<p align="center">
  <img src="assets/hero.svg" alt="Answer, reduced to a skeleton, drawn as a picture. Looking at the picture gives the same insight as reading the answer." width="800">
</p>

The skill works when the diagram commutes: looking at the picture has to give you the same
insight as reading the whole answer, only faster.

## An example

You ask whether to cache an API call and get four paragraphs back. Type `/beelddenker` and you
get this:

<p align="center">
  <img src="assets/example.svg" alt="A block of text on the left; on the right a commuting square: request, fetch, origin data, render, response, against request, lookup, cached copy, render, response. The square commutes only while the cache is fresh." width="800">
</p>

The picture shows more than the text did. The two routes give the same response only *up to*
staleness, so the question you actually have to answer is how stale a response may be.

## How it decides what to draw

1. **Skeleton.** Claude reduces the answer to its objects, its arrows (what goes in, what comes
   out), its order, its laws (what is equal, what stays invariant, what pulls against what),
   and the one claim the picture has to make obvious.
2. **Register.** If the content has structure that can be wrong, the picture is *exact*. If it
   is about meaning, judgement or a line of thought, the picture is *poetic*. Sometimes you get
   both: the exact schema first, then a small metaphor for the why.
3. **Principle.** It picks one of fifteen visual principles that matches the shape of the
   skeleton:

<p align="center">
  <img src="assets/principles.svg" alt="Exact principles: flow, function or pipeline, commuting diagram, group action. Poetic principles: tension field, metamorphosis, landscape or journey, constellation. Seven more: state machine, layers, order, matrix, spectrum, causal loop, timeline." width="800">
</p>

4. **Colour.** One colour means one thing per picture, and a legend says what.
5. **Medium.** It uses the best medium available: inline visuals in the Claude apps, an
   artifact, Mermaid or JSON Canvas for Obsidian, tikz-cd for LaTeX, and Unicode diagrams in a
   plain terminal.

A metaphor has to preserve structure, the way a functor does: each relation in the image must
mirror a relation in the idea. Otherwise it is only decoration. The full method is in
[SKILL.md](skills/beelddenker/SKILL.md), and the catalogue of principles is in
[principles.md](skills/beelddenker/references/principles.md).

## Install

<p align="center">
  <img src="assets/install.svg" alt="Three install routes: claude.ai or the Claude app, Claude Code, or any other agent." width="800">
</p>

### claude.ai and the Claude app

Free, Pro, Max, Team and Enterprise plans all support skills.

1. Turn on code execution: **Settings › Capabilities › Code execution and file creation**.
   In the newer settings layout the switch is called **Create and edit files**.
2. Download **[beelddenker.zip](https://github.com/raoulg/beelddenker/releases/latest/download/beelddenker.zip)**.
   Do not unpack it.
3. Go to **Customize › Skills**, click **+**, then **+ Create skill**.
4. Choose **Upload a skill** and pick `beelddenker.zip`.
5. Check that the skill is switched on in your skills list.

On Team and Enterprise plans, an owner has to allow skills first, under **Organization settings
› Plugins & skills**.

### Claude Code

Run these two commands inside Claude Code:

```text
/plugin marketplace add raoulg/beelddenker
```

```text
/plugin install beelddenker@beelddenker
```

Then run `/reload-plugins` or start a new session. The skill is called
`/beelddenker:beelddenker`, and Claude also picks it up when you say "make it visual".

You can also install it from your shell:

```bash
claude plugin marketplace add raoulg/beelddenker && claude plugin install beelddenker@beelddenker
```

### Any other agent that reads skills

Copy the skill folder into your skills directory. For Claude Code without the plugin system,
that directory is `~/.claude/skills/`:

```bash
git clone https://github.com/raoulg/beelddenker /tmp/beelddenker && cp -R /tmp/beelddenker/skills/beelddenker ~/.claude/skills/
```

## Use

- Right after a long answer, type `/beelddenker`.
- Ask in your own words: "make it visual", "draw it", "I lost the overview", "give me a
  metaphor". Dutch works too: "maak het visueel", "teken het".
- Give it a topic to get a visual answer from the start: `/beelddenker how does TCP work`.

It answers in the language you write in.

## License

MIT
