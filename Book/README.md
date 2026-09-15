# Book — Lecture-to-Chapter Conversions

PhD-level book chapters converted from the EF8083 Beamer lectures. Chapter 1 is
complete; Chapters 2–6 (Lectures 2–6) can be added later as `chapterN_*.tex`
and `\input` into `main.tex`.

## Files

| File | Description |
|------|-------------|
| `main.tex` | Book master file (11pt, letter, book class, biblatex/biber, CityUBlue links) |
| `chapter1_introduction.tex` | Ch. 1 — Introduction, converted from `../Lecture1_LaTeX/Lecture1_Intro.tex` |
| `references.bib` | ~60 verified entries (all citations in Ch. 1) |
| `figures/` | 25 figures copied from `../Lecture1_LaTeX/figures/` (original slide assets) |
| `main.pdf` | Compiled book (38 pages incl. TOC/LoF/LoT/bibliography) |

## Build

```bash
cd Book
pdflatex main && biber main && pdflatex main && pdflatex main
```

Requires MiKTeX (pdflatex + biber). Auto-install is enabled on this machine.

## Conversion conventions

- Slide bullets become running prose; figures become floats referenced as
  `Figure~\ref{...}`, each caption carrying a verified source line.
- Every figure was visually inspected before captioning; numbers stated in the
  text (PGR/PLR, Dichev gaps, EIK long–short spreads, MPR trading spreads,
  decile bar values) come from the figure images themselves, not from memory.
- Table-image from slide 25 was re-typeset as a booktabs table (Table 1.2)
  instead of embedding the screenshot.
- Deliberate corrections relative to the slides (verified 2026-09-15):
  - Short-term reversal cites Jegadeesh (1990), not "Jegadeesh 1991".
  - Berk and Green is 2004 (AER), not 2005.
  - Quality Minus Junk cited as Asness, Frazzini, and Pedersen (2019, RAST).
  - Barber and Odean (2000) sample stated precisely as 66,465 households.
  - McLean/Pontiff/Reilly (2025) = "Taking Sides on Return Predictability,"
    JFE 173, 104158; Lewellen (2011) = "Institutional Investors and the Limits
    of Arbitrage," JFE 102(1), 62–80.
- `slide38_chart.png` exists in the lecture figures folder but is not used by
  the current Lecture 1 `.tex`; it was not copied.

## Adding a chapter (e.g., Lecture 2)

1. Copy that lecture's figures into `figures/`.
2. Create `chapter2_limits_to_arbitrage.tex` starting with `\chapter{...}`.
3. Add `\input{chapter2_limits_to_arbitrage}` in `main.tex` after chapter 1.
4. Append new entries to `references.bib`; rebuild with the command above.
