# Book/ — Lecture-to-Book Chapter Conversions

PhD-level book chapters converted from the EF8083 Beamer lectures. Chapters 1–5
are complete (Introduction, Limits to Arbitrage, Preferences Under Uncertainty,
Biased Beliefs, Bounded Rationality); Chapter 6 (Lecture 6 — Memory) can be
added later as `chapter6_*.tex` and `\input` into `main.tex`.

## Files

| File | Description |
|------|-------------|
| `main.tex` | Book master file (11pt, letter, book class, biblatex/biber, CityUBlue links) |
| `chapter1_introduction.tex` | Ch. 1 — Introduction, converted from `../Lecture1_LaTeX/Lecture1_Intro.tex` |
| `chapter2_limits2arb.tex` | Ch. 2 — Limits to Arbitrage, converted from `../Lecture2_LaTeX/Lecture2_Limits2Arb.tex` |
| `chapter3_preferences.tex` | Ch. 3 — Preferences Under Uncertainty, converted from `../Lecture3_LaTeX/Lecture3_Preferences.tex` |
| `chapter4_beliefs.tex` | Ch. 4 — Biased Beliefs, converted from `../Lecture4_LaTeX/Lecture4_Beliefs.tex` |
| `chapter5_bounded.tex` | Ch. 5 — Bounded Rationality and Psychology-free Models, converted from `../Lecture5_LaTeX/Lecture5_BoundedRationality.tex` |
| `references.bib` | Verified entries (all citations across Ch. 1–5; ~204 entries as of 2026-09-15) |
| `figures/` | Figures copied from `../LectureN_LaTeX/figures/` (original slide assets) |
| `main.pdf` | Compiled book (127 pages, Ch. 1–5) |

## Build

```bash
cd Book
pdflatex main && biber main && pdflatex main && pdflatex main
```

Requires a TeX distribution with `pdflatex` and `biber` (TeX Live, MiKTeX, or MacTeX).

## Conversion conventions

- Slide bullets become running prose; figures become floats referenced as
  `Figure~\ref{...}`, each caption carrying a verified source line.
- Every figure is visually inspected before captioning; numbers stated in the
  text (PGR/PLR, Dichev gaps, EIK long–short spreads, MPR trading spreads,
  MAX t-stats, decile bar values) come from the figure images themselves, not
  from memory.
- Table-images (e.g., the Ch. 1 characteristics slide 25) are re-typeset as
  booktabs tables instead of embedding the screenshot.
- Deliberate corrections relative to the slides (verified 2026-09-15):
  - Short-term reversal cites Jegadeesh (1990), not "Jegadeesh 1991".
  - Berk and Green is 2004 (AER), not 2005.
  - Quality Minus Junk cited as Asness, Frazzini, and Pedersen (2019, RAST).
  - Barber and Odean (2000) sample stated precisely as 66,465 households.
  - McLean/Pontiff/Reilly (2025) = "Taking Sides on Return Predictability,"
    JFE 173, 104158; Lewellen (2011) = "Institutional Investors and the Limits
    of Arbitrage," JFE 102(1), 62–80.
- `slide38_chart.png` exists in the Lecture 1 figures folder but is not used
  by the current Lecture 1 `.tex`; it was not copied.

## Adding a chapter (e.g., Lecture 6)

1. Copy that lecture's figures into `figures/`.
2. Create `chapterN_*.tex` starting with `\chapter{...}`.
3. Add `\input{chapterN_*}` in `main.tex` after the previous chapter.
4. Append new entries to `references.bib`; rebuild with the command above.
5. **Label uniqueness:** chapters share the same `\label{}` namespace
   (`sec:contested`, `sec:ahead`, `fig:syy`, `fig:pead` collide). Prefix
   later-chapter labels with a chapter tag (e.g., `sec:attcontested`,
   `fig:attpead`, `fig:attsyy`) when re-using an earlier-chapter label.
