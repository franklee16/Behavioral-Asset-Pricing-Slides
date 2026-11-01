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
| `references.bib` | Verified entries (all citations across Ch. 1–5; CrossRef re-verification synced 2026-11-01) |
| `figures/` | Deck-only figures copied from `../LectureN_LaTeX/figures/` plus fallback copies of script-generated figures (their masters live in `../../Output/Figures/` in the private working tree, resolved first via `\graphicspath` in `main.tex`; changed 2026-10-30 — the fallback copies keep this public folder compiling standalone). Note: Lectures 4 and 5 share some filenames with different content — the plain filename holds the Lecture 4 version; Lecture 5 versions live under `l5_`-prefixed names (referenced only by `chapter5_bounded.tex`) |
| `main.pdf` | Compiled book (Ch. 1–5) |

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
- Deliberate corrections relative to the slides (verified 2026-09-15, extended 2026-09-25):
  - Short-term reversal cites Jegadeesh (1990), not "Jegadeesh 1991".
  - Berk and Green is 2004 (AER), not 2005.
  - Quality Minus Junk cited as Asness, Frazzini, and Pedersen (2019, RAST).
  - Barber and Odean (2000) sample stated precisely as 66,465 households.
  - McLean/Pontiff/Reilly (2025) = "Taking Sides on Return Predictability,"
    JFE 173, 104158; Lewellen (2011) = "Institutional Investors and the Limits
    of Arbitrage," JFE 102(1), 62–80.
  - Guo/Li/Wei (JFE 2020) cited in published author order Guo, Li, and Wei,
    correcting the deck's "Li, Guo, and Wei" (added 2026-09-25).
- **CrossRef re-verification (2026-11-01):** 13 entries corrected in the
  root `books/references.bib` and synced here the same day (wrong journal or
  wrong paper in `diether2003`, `barberis1998`, `barberodeanzhu2009`,
  `chendahuang2018`, `shenyuzhao2017`, `li2016`, `jinli2024`, `wang2020`,
  `sui2025`, `goldman2025`, `hong2016`,
  `antonioudoukassubrahmanyam2016`, `licuipangxie`) — see the root
  `books/README.md` for the full list. The two bib copies are byte-identical
  since 2026-11-01 (`bali2026`/`bordalo2025` now live in both; the root book
  ported Chs. 3–4 from here the same day).
- Chapters were re-synced to the 2026-09-25 slide revisions (paper-quality
  figures replace legacy screenshots; LTCM case study, index effect, learning
  costs, and *My Research* sections added in Ch. 2–5).
- Chs. 3–4 re-synced to the 2026-10-12 slide revisions: Ch. 3 gains the
  Barberis–Mukherjee–Wang (2016) conceptual framework (TK construction and
  pricing equation), corrected Wang–Yan–Yu (2017) Figures 2–3 (moved to the
  risk–return subsection; the earlier caption described prices not in the
  figure), and the asymmetric-correlation explanation of market skewness;
  Ch. 4 gains Bordalo–Gennaioli–La Porta–Shleifer (2025, JFE) expectations-
  based returns and Bali–Kelly–Mörke–Rahman (RFS 2026, forthcoming) machine
  forecast disagreement.
- Ch. 5 synced with the 2026-10-31 deck revisions (2026-11-01): the
  Hong--Stein (`sec:att3`) exposition now carries the momentum-trader signal
  $F_t = A + \phi\Delta P_{t-1}$, the equilibrium fixed point for $\phi$, and
  the hump-shaped impulse-response figure (`fig:hsir`, inline pgfplots); the
  comparative statics were already in prose. The Bybee (2025) LLM-beliefs
  subsections (`sec:sentiment`) were already complete. Same edits applied to
  the root `books/` copy, so Ch. 5 differs between the two builds only in the
  section-running-head mechanism (this build's `\markright` shortening is
  required: the full De Long title overflows the letter-page running head,
  which the root build's chapter-only header never shows).
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
