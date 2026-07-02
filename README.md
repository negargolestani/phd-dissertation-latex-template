# PhD Dissertation LaTeX Template

A ready-to-use LaTeX template for a PhD dissertation. The master file is thin;
all package/setup code lives in `preamble.tex`, and each chapter is split into
small, easy-to-edit section files inside its own subfolder. It compiles out of
the box with placeholder filler text (`\blindtext`) that you replace.

---

## Folder structure

```
dissertation-template/
├── main.tex                  <- master file; compile THIS one (thin)
├── preamble.tex              <- everything before \begin{document}: document
│                                class, all \usepackage lines, global settings
├── acronyms.tex              <- define all abbreviations here (root level)
├── references.bib            <- bibliography database, BibTeX (root level)
├── README.md                 <- this file
│
├── figures/                  <- all images go here (PDF, PNG, JPG, EPS)
│   └── README.txt
│
└── chapters/                 <- ALL writing lives under here
    │
    │   -- front matter (loose files) --
    ├── title.tex             <- title page
    ├── copyright.tex         <- copyright page
    ├── signatures.tex        <- committee signature / approval page
    ├── abstract.tex          <- abstract
    ├── dedication.tex        <- dedication
    ├── acknowledgements.tex  <- acknowledgements
    ├── chapter_contributions.tex  <- who contributed to each chapter
    │
    │   -- one subfolder per numbered chapter --
    ├── chapter1/             <- Chapter 1 (Introduction)
    │   ├── ch1_intro.tex
    │   ├── ch1_background.tex
    │   ├── ch1_details.tex
    │   └── ch1_second_section.tex
    ├── chapter2/             <- Chapter 2 (a results chapter)
    │   ├── ch2_summary.tex
    │   ├── ch2_intro.tex
    │   ├── ch2_result1.tex
    │   ├── ch2_result2.tex
    │   ├── ch2_discussion.tex
    │   ├── ch2_limitations.tex
    │   ├── ch2_conclusions.tex
    │   └── ch2_methods.tex
    ├── chapter3/             <- Chapter 3 (a second results chapter)
    │   ├── ch3_summary.tex
    │   ├── ch3_intro.tex
    │   ├── ch3_result1.tex
    │   ├── ch3_discussion.tex
    │   └── ch3_methods.tex
    └── chapter4/             <- Chapter 4 (Discussion)
        ├── ch4_overview.tex
        ├── ch4_future_work.tex
        └── ch4_final_thoughts.tex
```

---

## What goes where

| File / folder                       | What it holds                                                                 |
|-------------------------------------|-------------------------------------------------------------------------------|
| `main.tex`                          | Thin master file. It `\input`s the preamble and acronyms, opens the document, and lists every section in order with `\input{chapters/...}`. Add or remove chapters/sections here. |
| `preamble.tex`                      | **Everything before `\begin{document}`**: the `\documentclass`, all `\usepackage` lines, and global settings (margins, fonts, caption format, hyperlink colors, etc.). Add new packages here. |
| `acronyms.tex` (root)               | One `\DeclareAcronym{KEY}{...}` block per abbreviation. Use `\ac{KEY}` in the text; the Abbreviations list is built automatically. |
| `references.bib` (root)             | Your BibTeX entries. Cite with `\cite{KEY}`. |
| `figures/`                          | All image files. The preamble sets `\graphicspath{{./figures/}}`, so reference images by filename only. |
| `chapters/*.tex` (loose files)      | The front matter (title through chapter contributions) that appears before the numbered chapters. |
| `chapters/chapterN/`                | The actual writing for chapter *N*, one file per section/subsection. Short files make sections easy to move around. |

**Golden rule:** headings (`\chapter`, `\section`, `\subsection`) live in
`main.tex`; the prose for each heading lives in its own `\input` file under
`chapters/`.

---

## How to compile

You need a LaTeX distribution (TeX Live, MiKTeX, or MacTeX). Because of the
bibliography, run the standard four-step sequence:

```bash
pdflatex main.tex
bibtex   main
pdflatex main.tex
pdflatex main.tex
```

Or let `latexmk` handle the passes automatically:

```bash
latexmk -pdf main.tex
```

You can also upload the whole folder to **Overleaf** and set `main.tex` as the
main document.

---

## Customizing it

1. **Fill in the front matter.** Open each loose file in `chapters/` and replace
   the `UPPERCASE PLACEHOLDERS` (title, name, year, advisor, committee, institution).
2. **Write your chapters.** Replace every `\blindtext` with your text. Once no
   filler remains, delete the `\usepackage{blindtext}` line in `preamble.tex`.
3. **Add abbreviations** to `acronyms.tex` as you introduce them.
4. **Add references** to `references.bib` and cite them with `\cite{KEY}`.
5. **Drop images** into `figures/` and include them (see `figures/README.txt`).
6. **Add a chapter.** Create a new `chapters/chapterN/` folder with your section
   files, then add a `\chapter{...}` + `\input{chapters/chapterN/...}` block to
   `main.tex`.

### Handy snippets

Figure:
```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{my_figure.png}
    \caption{Caption text.}
    \label{fig:my_figure}
\end{figure}
```

Table:
```latex
\begin{table}[H]
    \centering
    \begin{tabular}{lcc}
        \toprule
        Column A & Column B & Column C \\
        \midrule
        row 1 & 1 & 2 \\
        row 2 & 3 & 4 \\
        \bottomrule
    \end{tabular}
    \caption{Caption text.}
    \label{tab:my_table}
\end{table}
```

Cross-reference: `\ref{sec:ch2_intro}`, `\ref{fig:my_figure}`,
`\cite{Example2025}`, `\ac{DNA}`.

---

## Notes

- The preamble uses `\usepackage[latin1]{inputenc}`. If you write in UTF-8
  (accented characters, etc.), change it to `\usepackage[utf8]{inputenc}` in
  `preamble.tex`.
- The bibliography style is `plainnat` (works everywhere via `natbib`). Swap
  `\bibliographystyle{plainnat}` in `main.tex` for another style (e.g.
  `IEEEtran`, `apalike`, `unsrtnat`) if your program requires it.
- Check your own graduate school's formatting rules (margins, spacing, order of
  front-matter pages) — they vary by institution, and this template is a
  reasonable default, not an official spec.

---

## License

This template is released under the **MIT License** (see the `LICENSE` file).
You are free to use, modify, and share it — including for your own dissertation —
at no cost. The only condition is that the `LICENSE` file (with its copyright
notice) stays included in copies or substantial portions of the template, which
keeps the original authorship credited.

Note: the copyright placeholder *inside* the template's own front matter
(`chapters/copyright.tex`) is separate — that page is for whoever uses the
template to fill in with their own name for their dissertation, so leave it as a
placeholder.

## Credits

Template created by **Negar Golestani**. If you use it, a link back to this
repository is appreciated but not required.
