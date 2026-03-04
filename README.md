# logicbox

A LaTeX package that provides **theorem-style boxes** (definition, theorem, lemma, proof, etc.) with smooth rounded corners, consistent colors, and light decoration. Built with **tcolorbox** and **TikZ**.

## Preview

Rendered from `examples/vimtex_logicbox.tex`:

**Page 1 — Definitions and title**
<img width="458" height="623" alt="Screenshot 2026-03-04 at 12 33 15 AM" src="https://github.com/user-attachments/assets/3c55dd7c-e144-4c2e-9e73-85cf524d76af" />

**Page 2 — Theorems, lemmas, corollaries, propositions**
<img width="458" height="545" alt="Screenshot 2026-03-04 at 12 33 36 AM" src="https://github.com/user-attachments/assets/a7091fb8-7830-4ee9-8c6a-ebc744c5dde9" />

**Page 3 — Proof (with multi-line math)**
<img width="451" height="320" alt="Screenshot 2026-03-04 at 12 33 45 AM" src="https://github.com/user-attachments/assets/22176463-ec1a-451f-bd85-771a0458f71a" />

## Features

- **Environments**: `definition`, `theorem`, `lemma`, `corollary`, `axiom`, `proposition`, `property`, `remark`, `example`, `exercise`, `solution`, `conjecture`, and `proof`.
- **Rounded corners** and padding so content (including displayed math) stays inside the frame.
- **Color palette** aligned with [dangbox](https://github.com/MrCherub/dangbox) and **epibox**: `blue!40!black`, `green!50!black`, `red!50!black`, `orange!50!black`, `purple!50!black`, `gray!50!black`.
- **Optional QED symbol** at the end of proofs via the `qed` package option.
- **Breakable** boxes across pages; small diamond/circle overlays on unbroken boxes.

## Requirements

- **tcolorbox** (with libraries: `breakable`, `skins`, `theorems`)
- **TikZ** and libraries: `shapes.geometric`, `calc`
- **xcolor**, **amsmath**/**amssymb**, **etoolbox**

## Installation

1. Clone or download this repo.
2. Put `logicbox.sty` where LaTeX can find it, for example:
   - `TEXMFHOME/tex/latex/logicbox/logicbox.sty`, or
   - Same directory as your `.tex` file.
3. Run `texhash` if you use a custom TEXMF tree.

## Usage

```latex
\documentclass{article}
\usepackage{logicbox}

\begin{document}

\begin{definition}{Vector Space}{def:vs}
  A vector space over a field \(F\) is a set \(V\) with addition and scalar multiplication...
\end{definition}

\begin{theorem}{Pythagorean Theorem}{thm:pyth}
  In a right triangle, \(a^2 + b^2 = c^2\).
\end{theorem}

\begin{proof}
  By induction. \ldots
\end{proof}

\end{document}
```

**Syntax**: For theorem-like environments use two arguments:

- `\begin{<env>}{<Title>}{<label>}`  
  Use an empty title `{}` if you don’t want a custom title. The second argument is the label for references.

**Package option**:

- `\usepackage[qed]{logicbox}` — adds a QED symbol (`\square`) at the end of every `proof` environment.

## Customization

Adjust the shared box style with:

```latex
\logicboxset{colback=gray!3, boxrule=0.4mm}
```

Any **tcolorbox** options accepted by the theorem style can be passed here.

## Examples

The `examples/` folder contains a sample document (`vimtex_logicbox.tex`) that uses definitions, axioms, theorems, lemmas, corollaries, propositions, and a proof with multi-line math.

## License

Use and modify as you like. If you redistribute, keeping the author/package name is appreciated.

## Author

Part of the dangbox / epibox family; colors and style chosen to match **calc.tex** and **epibox**.
