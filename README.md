# IEEE Access — Modular LaTeX Template

A clean, ready-to-use **IEEE Access** paper template with a **modular file
structure**: every part of the paper (title, abstract, each section,
references, biographies) lives in its own file under `sections/`, so the main
file stays short and the paper is easy to navigate and version-control.

This template ships with the official IEEE Access document class
(`ieeeaccess.cls`) and all required fonts, so it compiles out of the box — no
extra downloads needed.

---

## Folder structure

```
IEEE-Access-Modular-Template/
├── access.tex              # MAIN file — wires everything together (compile this)
├── sections/
│   ├── 00_title.tex        # title, authors, affiliations, funding footnote
│   ├── 00_abstract.tex     # abstract + index terms (keywords)
│   ├── 01_introduction.tex
│   ├── 02_related_work.tex
│   ├── 03_method.tex       # equation / figure / table / algorithm examples
│   ├── 04_results.tex      # full-width figure & table examples
│   ├── 05_conclusion.tex
│   ├── 06_acknowledgment.tex
│   ├── 07_references.tex   # manual thebibliography (or switch to BibTeX)
│   └── 08_biographies.tex  # author biographies
├── images/                 # put all figures/photos here
├── ieeeaccess.cls          # IEEE Access document class
├── IEEEtran.cls / .bst     # support for biographies & BibTeX
├── spotcolor.sty
└── t1-*.pfb / .tfm / .fd   # bundled fonts (Formata, Giovanni, Times)
```

## Requirements

You only need a **LaTeX distribution** — there is nothing else to install.

- **Overleaf** — works immediately, nothing to set up. Just upload the folder.
- **TeX Live (full)** — works out of the box.
- **MiKTeX** — works too; if it reports a missing package on the first compile,
  let it install on the fly (MiKTeX downloads missing packages automatically),
  or enable it once with:
  `initexmf --set-config-value "[MPM]AutoInstall=1"`.

**Bundled with this repo (no installation needed):** the document class
(`ieeeaccess.cls`), `IEEEtran.cls`/`.bst`, `spotcolor.sty`, and all fonts
(`t1-*.pfb/.tfm/.fd/.map`).

**Standard CTAN packages used** (all included in a full TeX Live / Overleaf,
auto-installed by MiKTeX): `cite`, `amsmath`, `amssymb`, `amsfonts`,
`algorithm`, `algorithmic`, `graphicx`, `textcomp`, `booktabs`, `multirow`,
`array`, `pifont`, `placeins`, `bm`, `stfloats`, `etoolbox`, `hyperref`.

## How to build

Compile **`access.tex`** (not the section files — those have no preamble).

Run **pdflatex twice** so cross-references and the page layout settle:

```bash
pdflatex access.tex
pdflatex access.tex
```

or simply:

```bash
latexmk -pdf access.tex
```

Works with TeX Live and MiKTeX. In an editor (VS Code + LaTeX Workshop,
TeXstudio, Overleaf, …) set **`access.tex` as the root/main document**. Each
section file already carries a `% !TEX root = ../access.tex` magic comment.

> **Overleaf:** upload the whole folder and set `access.tex` as the main file.

## How to edit

- **Add a section** — create `sections/09_foo.tex`, then add
  `\input{sections/09_foo}` to `access.tex` at the right spot.
- **Figures** — put the image in `images/` and use
  `\includegraphics[width=\columnwidth]{name}` (one column) or
  `width=\textwidth` inside `figure*` (both columns). `\graphicspath{{images/}}`
  is already set.
- **Tables** — see `03_method.tex` (single column) and `04_results.tex`
  (full width). They use `tabular*{\columnwidth}` / `tabular*{\textwidth}` with
  `@{\extracolsep{\fill}}` so the table stretches to the margins.
- **References** — edit `07_references.tex` (manual `\bibitem` list) or switch
  to BibTeX (instructions inside that file; `IEEEtran.bst` is included).

## What's preconfigured (in `access.tex`)

- **Clickable blue hyperlinks** for `\ref` and `\cite` (`hyperref`).
  For the print/camera-ready version, swap to
  `\usepackage[hidelinks]{hyperref}` to keep links active but uncolored.
- **Tighter author-biography spacing** — removes the large default gaps
  between `IEEEbiography` entries.
- **Float/whitespace tuning** — relaxed float placement and `\raggedbottom`
  to reduce awkward gaps.
- **Bold-math setup** required by the IEEE Access class.

## Submission notes

For the **initial submission**, leave the publication metadata as the
placeholders — IEEE fills these in at production:

- `\history{Date of publication xxxx 00, 0000, ...}` in `00_title.tex`
- `\doi{10.1109/ACCESS.2017.DOI}` in `00_title.tex`
- The `VOLUME xx, year` footer (set inside `ieeeaccess.cls`)

## License

The IEEE Access class and fonts (`ieeeaccess.cls`, `IEEEtran.*`, `spotcolor.sty`,
the `t1-*` fonts) are property of IEEE and distributed under their own terms;
they are included here for convenience. The skeleton/example content in
`sections/` and this README are free to use, modify, and redistribute.
