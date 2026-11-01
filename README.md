# The paper (restarted 31 Oct 2026, after the 29 Oct call with Jérôme)

| file | what |
|---|---|
| `main.tex` + `sections/` | **The paper you write.** Overleaf compiles `main.tex`. Every section has its heading, its figures in place, and grey `[notes]` saying what goes there (from the call, with transcript times) and which numbers are available, with their sources. |
| `draft.tex` + `draft/` | A reference draft of the whole paper, same structure and figures. To read it: Overleaf Menu → Main document → `draft.tex` (switch back afterwards). Every number has a `% src:` comment. Not meant to become the final text. |
| `preamble.tex` | Shared by both: ICML 2026 kit (`preprint` option: names shown, "Preprint" footer), packages, notation, `\note{}` and `\pending{}`. |
| `figures/` | Every figure, drawn at its printed size. |
| `references.bib` | The old paper's 157 entries; add new ones here. |
| `icml2026.sty`, `icml2026.bst`, `fancyhdr.sty` | The ICML 2026 kit (provisional until the venue is decided). |
| `old/` | The 6 Oct ICML paper, kept for reference. Not compiled, nothing points to it; delete it when you no longer need it. |

## Writing aids
- `\note{...}`: grey guidance text. `\shownotesfalse` (top of `main.tex`) hides every note.
- `\pending{...}`: a result still on the cluster (E55, E56) or not yet run, printed in orange.

## Jérôme's rules (call of 29 Oct)
- Story in four parts: Gaussian chain (diffusion breaks locality) → chain + noise = tree, BP exact → Laplace chain,
  EM, comparison with CNN (local) and MLP (not local), breaking Markovianity (the largest section) → Allen–Cahn.
- 8–10 pages. Less is more: little background, `\cite{}` placeholders are fine, **no proposition/proof style**.
  BP at the level of his hierarchical-filtering paper §2.4. EM explained as following the gradient of an expectation.
- Figures: a box on all four sides, LaTeX font, label size ≈ text size, **no background grid**, log scales, minor
  ticks, dots for experiments and lines for theory. The factor graph goes in. Slide 14 is one plot.
- The error decomposition goes to the appendix.

## Figures
Include each figure **without a width**, `\includegraphics{fig_x}`: it is drawn at 3.25 in (one column, `figure`) or
6.75 in (full width, `figure*`), so its 10 pt labels match the body text. The two diagrams are TikZ
(`figures/*.tikz`), `\input` directly, so they are set in the body font and can be edited here.

All plots come from the research repository `markov-score-diffusion-icml`:

    .venv/bin/python tools/paper_figs/make_paper_figures.py --layout twocol     # writes reports/paper-figures/twocol/
    tools/overleaf_paper.sh figures                                              # copies them here and pushes

then in Overleaf: Menu → GitHub → Pull GitHub changes into Overleaf. Figures waiting for data
(`fig_families`, `fig_families_error`, the EM curve in `fig_em_dynamics`) fill in when E56's outputs are fetched.

## Before submission
- Table 1 (Allen–Cahn) is typed from `~/Code/Thesis/jerome-call-2026-10-29-slide15.md` (frozen E33/E43 rows). It
  should come from a generator reading the frozen outputs, like every other table.
- The EM step counts (80 / 229 / 638 updates, thesis exp_27) were taken from notes, not from a reader script.
- Overleaf compiles with pdfLaTeX in Times, which is what the figures use. A local tectonic build falls back to Latin
  Modern and shows "Title Suppressed Due to Excessive Size" in the running head; Overleaf's PDF is the faithful one.

## Sync
Overleaf ↔ GitHub: Overleaf Menu → GitHub. Pull before you start working in Overleaf if figures were pushed; push from
Overleaf before anyone pushes figures from the research repository.
