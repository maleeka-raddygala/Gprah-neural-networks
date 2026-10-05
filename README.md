# CS224W: Machine Learning with Graphs — Lecture Notes (Fall 2026)

Compact LaTeX recall notes, one chapter per lecture. Built for Overleaf (pdfLaTeX, the default compiler).

## Import into Overleaf
1. Overleaf → **New Project → Upload Project** → choose the `.zip`.
2. `main.tex` is the main document. Compiler: **pdfLaTeX** (Menu → Settings).
3. Compile. Overleaf automatically handles the `\include` files and the cross-references.

## Layout
```
main.tex            % title page, TOC, \include list
preamble.tex        % packages, page layout, colours, box environments, \slides, \lecture
macros.tex          % notation (\vz, \mA, \R, \tp, \Nb, \ENC, ...)
lectures/
  _template.tex     % copy this to start a new lecture (it is not compiled)
  lec01-intro.tex
  lec02-node-embeddings.tex
  lec03-gnn1.tex
  lec04-gnn2.tex
appendix/
  notation.tex      % symbol tables, one section per lecture
```

## Adding a lecture
1. Copy `lectures/_template.tex` to `lectures/lecNN-short-name.tex`.
2. Edit the first line: `\lecture{NN}{Title}{Day, Month DD, 2026}\label{ch:lecNN}`.
3. Add `\include{lectures/lecNN-short-name}` to `main.tex` (lectures section, in order).
4. Add any new symbols to `appendix/notation.tex`. Put new shared macros in `macros.tex`.

To compile faster while editing one lecture, uncomment `\includeonly{...}` in `main.tex`.

## Style (keep this when you edit)
Compact **recall notes**: everything on the slides, in slide order, as short bullets; bold key terms;
every formula displayed; small TikZ figures only where the picture is the content. Nothing new unless
needed to read a slide.

- **Slide refs:** `\slides{12--15}` on the line right after a `\section`/`\subsection` (PDF page numbers
  of the posted deck; prints "Slide 12" or "Slides 12--15" in the margin).
- **Terms:** `\term{...}` for newly introduced terms.
- **Boxes (sparingly):** `definition` (core definitions), `keyidea` (takeaways the slides highlight),
  `example` (worked examples from the slides), `caution` (slide errata, 1–2 lines).
  Optional subtitle: `\begin{keyidea}[Shallow encoders]`.
- **End of every lecture:** the "Lecture NN at a glance" box (see the template) — one line per main idea.
- **Labels:** prefix with the lecture: `sec:lec02-...`, `eq:lec02-...`, `fig:lec02-...`;
  `\cref{ch:lec02}` prints "Lecture 2".
- **Notation:** bold lowercase vectors (`\vz`), bold uppercase matrices (`\mA`), `\tp` for transpose;
  slide notation wherever possible. New symbols go in `appendix/notation.tex`.
- **Figures:** TikZ with the shared styles in `preamble.tex` (`vertex`, `vtx`, `target`, `hl`, `edge`,
  `dedge`, `arrow`, `block`, `nnbox`). Images, if you add any, go in a `figures/` folder.
