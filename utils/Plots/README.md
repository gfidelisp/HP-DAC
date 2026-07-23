# `hpdac.utils` — plot standard

Shared plotting standard for the Hp-DAC project. One import applies the
house style to every figure: colours, markers, fonts, ticks, margins, size
and export quality.

There is no API to learn. You write ordinary matplotlib.

```python
from hpdac.utils.plotstyle import COLORS, MARKERS, MM

fig, ax = plt.subplots()
ax.plot(x1, y1, ls="none", label="Series 1")   # blue circles, automatically
ax.plot(x2, y2, ls="none", label="Series 2")   # orange squares, automatically
ax.set_xlabel("Mass flow rate [kg h$^{-1}$]")
ax.set_ylabel("Coefficient of performance [-]")
ax.legend(loc="upper right")
ax.grid(True, which="minor", linestyle=":", linewidth=0.4, color="gray")
fig.savefig("figures/cop_versus_flow.pdf", bbox_inches="tight")
```

![Example figure](../../../docs/five_series.png)

---

## Contents

| File | Purpose |
|---|---|
| `plotstyle.py` | The whole standard. Importing it applies the style. |
| `../../../notebooks/hpdac_plot_standard.ipynb` | Runnable reference with three worked examples |

`plotstyle.py` exports three names: `COLORS`, `MARKERS` and `MM`. Everything
else it does happens on import, through `plt.rcParams`.

---

## Quick start

1. `from hpdac.utils.plotstyle import COLORS, MARKERS, MM` at the top of the
   script. That is the whole setup — there is nothing to call.
2. Plot with `ax.plot(...)`. Do not pass colours or markers.
3. Add the minor grid: one line per axes (see [Grid](#grid)).
4. Save with `fig.savefig(path, bbox_inches="tight")`.

If you are working in a notebook outside the package, copy the body of
`plotstyle.py` into the first cell instead. It is self-contained.

---

## How the property cycle works

Colour, marker and dash pattern are zipped into a single `axes.prop_cycle`,
so consecutive `plot` calls advance through all three together. Two
independent channels identify each series, which means the figure survives
greyscale printing and colour vision deficiency.

| You write | You get |
|---|---|
| `ax.plot(x, y, ls="none")` | Markers only — the scatter case |
| `ax.plot(x, y, marker="none")` | Line only — the model case |
| `ax.plot(x, y)` | Both, joined markers |
| `ax.errorbar(x, y, yerr=e, ls="none")` | Marker and colour from the cycle |
| `ax.scatter(x, y)` | Colour only — `scatter` ignores the marker cycle |

Prefer `plot(..., ls="none")` over `scatter` unless you need per-point sizes
or a colour mapping.

**Reusing a colour.** To draw a model curve over the data it reproduces, name
the colour explicitly rather than letting the cycle advance:

```python
for i, (label, (x, y)) in enumerate(data.items()):
    ax.plot(x, y, ls="none", label=label)                      # measured
    ax.plot(xs, model[i], color=COLORS[i], ls="--", marker="none")   # model
```

Then give the legend two extra entries — one marker handle labelled
*Measured*, one dashed line labelled *Model* — instead of listing every
series twice.

**Palette.** Okabe–Ito, eight entries, in order:

| # | Colour | Hex | Marker |
|---|---|---|---|
| 1 | blue | `#0072B2` | `o` |
| 2 | vermillion | `#D55E00` | `s` |
| 3 | bluish green | `#009E73` | `^` |
| 4 | reddish purple | `#CC79A7` | `D` |
| 5 | orange | `#E69F00` | `v` |
| 6 | sky blue | `#56B4E9` | `P` |
| 7 | grey | `#666666` | `X` |
| 8 | black | `#000000` | `*` |

For a continuous third variable use `cmap="cividis"` — perceptually uniform
and colour-blind safe. Do not use `jet` or `rainbow`: they create apparent
banding that is not in the data, and referees notice.

---

## Grid

Matplotlib has a single set of grid settings, so major and minor gridlines
cannot both be configured through `rcParams`. The style sets the major grid;
add the minor grid per axes:

```python
ax.grid(True, which="minor", linestyle=":", linewidth=0.4, color="gray")
ax.grid(True, which="major", linestyle="--", linewidth=0.6, color="black")
```

The second line restates the default and is optional. The first is the one
that matters — without it the minor grid inherits the major style and
competes with the data.

For a multi-panel figure, loop:

```python
for ax in axes.flat:
    ax.grid(True, which="minor", linestyle=":", linewidth=0.4, color="gray")
```

---

## Figure size

The default is **190 × 120 mm**, the full text width of an Elsevier
two-column article, which is what *International Journal of Refrigeration*
uses.

The rule that matters: **keep the fonts fixed and change only the box.**
A figure drawn at 190 mm and placed with `\includegraphics[width=\linewidth]`
appears at 1:1, so its 13 pt axis labels are 13 pt on the printed page and
match the manuscript body text. As soon as `\includegraphics` rescales a
figure, its fonts no longer match — this is the single most common reason
figure text looks inconsistent across a thesis.

Sizes are written in millimetres using the `MM` constant:

```python
fig, ax = plt.subplots(figsize=(90 * MM, 57 * MM))   # single column
```

| Use | Size (mm) |
|---|---|
| Single column | 90 × 57 |
| One and a half columns | 140 × 88 |
| Full text width *(default)* | 190 × 120 |
| Two panels side by side | 190 × 80 |
| Slide | 240 × 135 |

The 0.63 aspect ratio is close to 1/φ and keeps a full-width figure under
half the text block height, so the caption and some body text still fit on
the same page.

---

## Axis labels

Two rules. Neither can be enforced by code, because you type the strings.

**1. Never abbreviate.** The axis label carries the full quantity name.

| Write | Not |
|---|---|
| `Mass flow rate [kg h$^{-1}$]` | `mdot [kg/h]` |
| `Coefficient of performance [-]` | `COP` |
| `Heat sink outlet temperature [$^{\circ}$C]` | `T_sink` |

Add the symbol only when the text refers to it:
`r"Mass flow rate, $\dot{m}_\mathrm{f}$ [kg h$^{-1}$]"`.

**2. Negative exponents, never a solidus.** A solidus is ambiguous the moment
there is more than one denominator — `W/m K` can be read two ways.

| Write | Not |
|---|---|
| `[kg h$^{-1}$]` | `[kg/h]` |
| `[W m$^{-1}$ K$^{-1}$]` | `[W/m K]` |
| `[GJ t$^{-1}$]` | `[GJ/t]` |
| `[-]` for dimensionless | `[]` or blank |

Exponents need math delimiters and an `r` prefix on the string:

```python
ax.set_ylabel(r"Thermal conductivity [W m$^{-1}$ K$^{-1}$]")
```

The same convention applies in LaTeX tables. If you use `siunitx`, add
`\sisetup{per-mode=power}` to the preamble — without it,
`\si{\watt\per\metre\per\kelvin}` typesets as W/m/K and the tables stop
agreeing with the figures.

---

## Saving

Every figure is saved twice: vector PDF for the manuscript, 600 dpi PNG for
slides and previews.

```python
fig.savefig("figures/name.pdf", bbox_inches="tight")
fig.savefig("figures/name.png", dpi=600, bbox_inches="tight")
```

`constrained_layout` (on by default) arranges the elements inside the figure
so labels never collide; `bbox_inches="tight"` trims the saved border down to
`pad_inches = 0.08`. Both are already set in `rcParams` and are passed
explicitly above only so the intent is visible in the code.

Fonts are embedded as Type 42 so the PDF is editable and passes publisher
preflight checks.

---

## What the style sets

| Item | Value |
|---|---|
| Series colours | Okabe–Ito, 8 entries, colour-blind safe |
| Series markers | `o s ^ D v P X *`, advancing with the colour |
| Marker edges | Black, 1.1 pt |
| Font | Latin Modern Roman; 11 pt body, 13 pt axis labels, 12 pt ticks |
| Maths | `cm` mathtext, so `$\dot{m}$` matches the text font |
| Axis frame | 1.8 pt, all four spines |
| Ticks | Inward, all four sides, minor ticks visible |
| Major grid | Black dashed, 0.6 pt, behind the data |
| Minor grid | Grey dotted, 0.4 pt — **added per axes** |
| Margins | 6 % horizontal, 9 % vertical inside the axes |
| Save border | 0.08 in |
| Size | 190 × 120 mm |
| Layout | `constrained_layout` inside, `bbox_inches="tight"` on save |
| Export | Vector PDF plus 600 dpi PNG, Type 42 fonts |

---

## Overriding

Any keyword you pass wins, as always:

```python
ax.plot(x, y, color="black", marker="none", lw=1.2)
```

To change the style for one figure only — a presentation version, say — use
`rc_context` so the change does not leak into later cells or figures:

```python
with plt.rc_context({"font.size": 14, "axes.labelsize": 17,
                     "xtick.labelsize": 16, "ytick.labelsize": 16,
                     "legend.fontsize": 16}):
    fig, ax = plt.subplots(figsize=(240 * MM, 135 * MM))
    ...
```

Do not edit `plotstyle.py` to suit one figure. If a change is right for the
whole project, change it there and regenerate everything; if it is right for
one figure, use `rc_context`.

---

## Caption and table conventions

Not enforced by code. Applied by hand, consistently.

**Captions.** One declarative sentence, operating conditions in parentheses,
full stop:

> **Figure 3** — Coefficient of performance as a function of the mass flow
> rate for the three prototype versions ($T_\mathrm{sink}$ = 90 °C,
> $T_\mathrm{source}$ = 25 °C). Experimental data.

**Tables.** `booktabs` rules only — no vertical rules, no `\hline`. The
header carries the symbol and the unit, following the same exponent rule as
the axes:

```latex
\begin{table}[!htb]
  \centering
  \caption{Mean performance of each prototype version.}
  \label{tab:mean-values}
  \begin{tabular}{lccc}
  \toprule
    Version & $\dot{m}_\mathrm{f}$ (kg h$^{-1}$) & $COP$ (--) & $\eta_\mathrm{II}$ (--) \\
  \midrule
    1 &  834 & 5.27 $\pm$ 0.15 & 0.50 \\
    2 &  845 & 4.32 $\pm$ 0.15 & 0.60 \\
  \bottomrule
  \end{tabular}
\end{table}
```

Report a value and its uncertainty with matching decimals:
`5.27 $\pm$ 0.15`, not `5.2712 $\pm$ 0.15`.

---

## Troubleshooting

**The minor grid is as dark as the major grid.** You did not add the
`which="minor"` line. See [Grid](#grid).

**Two series came out the same colour.** More than eight series on one axes,
so the cycle wrapped. Split the figure into panels — eight is already more
than a reader can track.

**`scatter` ignored the marker.** `scatter` does not consume the marker
cycle. Use `plot(..., ls="none")`, or pass `marker=MARKERS[i]` explicitly.

**The font is not Latin Modern.** The font is not installed; matplotlib fell
back to DejaVu Serif. Install `lmodern` (TeX Live) or `cm-super`, then clear
the cache with `matplotlib.font_manager._load_fontmanager(try_read_cache=False)`.

**Labels are cut off in the saved file.** `bbox_inches="tight"` is missing
from the `savefig` call, or a manually placed colour bar is fighting
`constrained_layout`. For that specific figure, pass `layout="none"` to
`plt.subplots` and position by hand.

**Figures changed after a `pip install`.** Matplotlib minor releases move
default tick placement. Pin the version — see below.

---

## Repository notes

* **Pin matplotlib** in `requirements.txt` (`matplotlib==3.10.*`). Otherwise
  figures shift between machines and across time.
* **Add `nbstripout` to pre-commit.** Committed notebook outputs are base64
  PNGs; without stripping, the repository grows fast and every diff is noise.
  The versioned artefact is the file in `figures/`, not the cell output.
* **Regenerate rather than edit.** Figures in `figures/` are build products
  of the scripts in `cases/`. If a figure needs to change, change the script.

---

## Changing the standard

`plotstyle.py` is shared by every figure in the project, so a change to it
changes every figure in every report and paper. Before editing:

1. Open an issue describing what is wrong with the current output.
2. Regenerate the figures in `cases/` and compare before and after.
3. Note the change in `CHANGELOG.md`, since figures already submitted to a
   journal will no longer match the ones in the repository.
