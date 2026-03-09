# logicbox Product Spec

## Goal

`logicbox` should become a clean authoring layer for structured math notes, not just a visual theorem-box package.

The package should help users:
- write theorem-heavy notes faster
- keep theorem-like content visually consistent
- attach useful metadata to content
- generate filtered outputs from one source document

## Positioning

`logicbox` should not compete directly with lower-level packages that already do one job well.

Already-solved areas:
- box rendering and styling: `tcolorbox`, `coloredtheorem`
- theorem declarations, restating, lists: `thmtools`, `keytheorems`
- references: `cleveref`, `zref-clever`, `theoremref`
- theorem-proof links: `linkedthm`
- exercises and solution workflows: `xsim`, `exframe`, `exercise`, `exercises`
- lecture-note classes: `lectures`, `lecturenotes`, `whatsnote`

`logicbox` should instead be the elegant front door that combines the useful parts of that ecosystem for note writers.

## Non-goals

Do not turn `logicbox` into:
- a generic replacement for `tcolorbox`
- a theorem engine that reimplements `keytheorems`
- a full exam system that competes with `xsim` or `exframe`
- a full document class in the first phase

## Product Shape

The project should eventually have three layers:

1. `logicbox-core`
- Visual theorem and proof environments
- Shared counters
- Custom environment registration
- Stable default styles

2. `logicbox-notes`
- Metadata on theorem-like blocks
- Filtered theorem and definition catalogs
- Output modes for note-taking workflows
- Smart defaults for course notes

3. `logicbox-exercises`
- Exercise and solution metadata
- Hide/show solution modes
- Problem-set and review-sheet outputs
- Optional interoperability with external exercise packages

## Main Product Bet

The strongest gap in the ecosystem is a package that combines:
- attractive theorem boxes
- structured metadata
- filtered generated lists
- multiple output modes
- minimal setup

That is the feature cluster `logicbox` should own.

## First-Class Metadata

The package should support semantic keys on theorem-like content.

Initial metadata targets:
- `topic`
- `difficulty`
- `importance`
- `source`
- `tags`

This metadata should be available on:
- `definition`
- `theorem`
- `lemma`
- `corollary`
- `proposition`
- `example`
- `exercise`
- `solution`

## Output Modes

One source document should be able to produce several useful views.

Initial modes:
- `notes`
- `handout`
- `problems`
- `solutions`
- `summary`

Expected behavior:
- `notes`: full content
- `handout`: no solutions, reduced commentary
- `problems`: exercises only
- `solutions`: exercises with solutions
- `summary`: important definitions and theorems only

## Generated Views

The metadata layer should drive generated sections and indexes.

Initial generated views:
- key definitions
- important theorems
- examples by topic
- exercises by topic
- exercises by difficulty

The package should make these views easy to insert into a document without forcing users to manage ad hoc lists manually.

## UX Requirements

The package should stay elegant from a user perspective.

Requirements:
- simple default syntax
- optional metadata, not mandatory metadata
- readable source files
- sane defaults with minimal configuration
- clear behavior when metadata is absent

## Syntax Direction

The current environment syntax should remain supported:

```latex
\begin{theorem}{Title}{thm:label}
  ...
\end{theorem}
```

Metadata should be added in a way that does not make documents ugly.

Preferred direction:

```latex
\begin{theorem}[topic={groups}, importance=high, tags={algebra,core}]{Lagrange's Theorem}{thm:lagrange}
  ...
\end{theorem}
```

If this proves too invasive with the current implementation, provide parallel environment forms or helper commands rather than breaking the current API.

## Technical Strategy

Recommended strategy:
- keep the current style layer in `logicbox.sty`
- avoid rewriting low-level theorem internals unless necessary
- build metadata and generated-list features incrementally
- interoperate with established packages rather than replacing them

Potential integration targets:
- `keytheorems` for theorem management
- `zref-clever` or `cleveref` for references
- `linkedthm` for theorem-proof navigation
- `exframe` or `xsim` for future exercise workflows

## Milestones

### Milestone 1

Ship a stable core package with:
- current styled environments
- shared counters
- custom environment registration
- polished README and examples

### Milestone 2

Ship metadata support for theorem-like content:
- parse metadata keys
- store metadata in auxiliary data
- expose simple filtered lists

### Milestone 3

Ship output modes:
- notes
- handout
- summary

### Milestone 4

Ship exercise workflow support:
- exercise metadata
- hide/show solutions
- exercises-only outputs

## Immediate Next Step

Do not add more styling features first.

The next high-value implementation target should be:
- theorem metadata
- auxiliary-data storage
- one generated list, such as "Important Theorems"

That is the first step that turns `logicbox` from a box package into a note-writing tool.
