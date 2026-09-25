# EF8083 — Behavioral Asset Pricing

Beamer lecture decks for **EF8083 Behavioral Asset Pricing**, a PhD course at the City University of Hong Kong.

Instructor: Frank Weikai Li (weikaili@cityu.edu.hk)

## Lectures

| # | Topic | Source |
|---|-------|--------|
| 1 | Introduction — asset pricing anomalies, investor behavior | [Lecture1_LaTeX/Lecture1_Intro.tex](Lecture1_LaTeX/Lecture1_Intro.tex) |
| 2 | Limits to Arbitrage — noise trader risk, short-sale constraints | [Lecture2_LaTeX/Lecture2_Limits2Arb.tex](Lecture2_LaTeX/Lecture2_Limits2Arb.tex) |
| 3 | Preferences — prospect theory, loss aversion, disposition effect | [Lecture3_LaTeX/Lecture3_Preferences.tex](Lecture3_LaTeX/Lecture3_Preferences.tex) |
| 4 | Beliefs — overconfidence, over-extrapolation, heterogeneous beliefs | [Lecture4_LaTeX/Lecture4_Beliefs.tex](Lecture4_LaTeX/Lecture4_Beliefs.tex) |
| 5 | Bounded Rationality — limited attention, investor sentiment | [Lecture5_LaTeX/Lecture5_BoundedRationality.tex](Lecture5_LaTeX/Lecture5_BoundedRationality.tex) |
| 6 | Memory and Markets — associative memory, memory-based beliefs | [Lecture6_LaTeX/Lecture6_Memory.tex](Lecture6_LaTeX/Lecture6_Memory.tex) |

Each folder contains the LaTeX source, the compiled PDF, and figure assets. Lectures 2–5 include *My Research* frames that connect the instructor's own published papers and working papers to the topic on the surrounding slides.

## Compilation

```bash
cd LectureN_LaTeX
pdflatex LectureN_*.tex
pdflatex LectureN_*.tex   # second pass resolves references
```

Requires a TeX distribution with `pdflatex` (TeX Live, MiKTeX, or MacTeX). Decks use the Beamer Madrid theme with CityU color accents (CityUBlue, RGB 0,51,102).

## Book

Chapter versions of the lectures, re-typeset as a single book (11pt, letter, `book` class, biblatex/biber). Chapters 1–5 (from Lectures 1–5) are complete — 146 pages; Chapter 6 (Memory) can be added later. Chapter content is kept in sync with the lecture decks (last synced 2026-09-25), including the *My Research* sections in Chapters 2–5.

- Source: [Book/main.tex](Book/main.tex)
- Compiled PDF: [Book/main.pdf](Book/main.pdf)
- See [Book/README.md](Book/README.md) for build instructions and conversion conventions.

## Data

Lecture 1 uses the Open Source Asset Pricing (OSAP) database:

> Chen, Andrew Y., and Tom Zimmermann. "Open source cross-sectional asset pricing." *Critical Finance Review* (2022). <https://www.openassetpricing.com/>

## Citation

If you use these slides, please cite:

> Li, Frank Weikai. (2026). *EF8083 — Behavioral Asset Pricing: Lecture Decks*. City University of Hong Kong. <https://github.com/franklee16/Behavioral-Asset-Pricing-Slides>

## License

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) — free to share and adapt for non-commercial use with attribution.

## Acknowledgments

Developed for the EF8083 PhD course at CityU HK.