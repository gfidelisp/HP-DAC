# `hpdac_tables.tex` — LaTeX table standard

Seven ready-to-edit table templates for the Hp-DAC project, plus the preamble
that makes them work. Companion to the [plot standard](../src/hpdac/utils/README.md).

**Self-contained: upload to Overleaf and press Recompile.** The PDF shows
every template rendered; the source beside each banner is what you copy.

```
1. Copy the PREAMBLE block into your manuscript preamble.
2. Copy the template closest to what you need.
3. Edit the caption, label, column format and data.
```

No Python, no build step. You edit the `.tex` directly.

---

## Templates

| # | Template | Use it for |
|---|---|---|
| 1 | Basic results table | The default. Use it unless you need one of the others. |
| 2 | Decimal alignment | Any column whose numbers have different digit counts |
| 3 | Uncertainties | Measured values reported as `5.27 ± 0.15` |
| 4 | Grouped headers | Measured vs. predicted, or any two-level header |
| 5 | Parameters with notes | Model inputs, boundary conditions, assumptions |
| 6 | Multi-page table | A test matrix too long for one page |
| 7 | Landscape page | A table too wide for the text block |

Plus a quick-reference table of column types at the end of the document.

---

## Requirements

Nothing to install on Overleaf — everything below is already there. On a
local TeX installation you need a reasonably complete distribution.

| Package | Why |
|---|---|
| `booktabs` | `\toprule`, `\midrule`, `\bottomrule`, `\cmidrule` |
| `siunitx` | Decimal alignment, uncertainties, unit typesetting |
| `threeparttable` | Table notes that match the table width (template 5) |
| `longtable` | Tables that break across pages (template 6) |
| `pdflscape` | Landscape pages (template 7) |
| `lmodern` | Same font family as the figures |
| `array`, `caption` | Column tuning and caption spacing |

On a minimal Debian or Ubuntu install:

```bash
sudo apt install texlive-latex-recommended texlive-latex-extra \
                 texlive-science lmodern
```

`siunitx` v3 is assumed (`\unit{}`, `\qty{}`, `\num{}`). The v2 spelling
`\si{}` still works but is deprecated.

---

## The preamble

Copy this block into your manuscript. It is the whole standard on the LaTeX
side.

```latex
\usepackage{booktabs}
\usepackage{array}
\usepackage{siunitx}
\usepackage{threeparttable}
\usepackage{longtable}
\usepackage{pdflscape}
\usepackage{caption}

\sisetup{
  per-mode                = power,
  exponent-product        = \times,
  separate-uncertainty    = true,
  detect-all,
  table-align-uncertainty = true,
  group-digits            = integer,
  group-minimum-digits    = 5,
}

\captionsetup[table]{skip=6pt}
```

Two settings carry most of the weight:

**`per-mode=power`** makes `\unit{\watt\per\metre\per\kelvin}` typeset as
W m⁻¹ K⁻¹ instead of W/m/K. Without it, tables written with `siunitx` units
disagree with the figure axes, which use negative exponents.

**`group-minimum-digits=5`** stops four-digit numbers being split: `1219`
stays `1219` rather than becoming `1 219`. The siunitx default of 4 reads
oddly for engineering values.

---

## Conventions

### Rules

`booktabs` only: one `\toprule`, one `\midrule` under the header, one
`\bottomrule`.

**No vertical rules, ever. No `\hline`.** A vertical rule is almost always a
sign that the table should be split or transposed. For a group spanning
several columns use `\cmidrule(lr){2-3}` — the `(lr)` trims the rule so
adjacent groups do not touch. Never put a full-width `\midrule` in the body.

### Captions

**Above** the table. Figures take the caption below; tables above. One
declarative sentence, sentence case, ending in a full stop:

> **Table 2** — Measured coefficient of performance with expanded
> uncertainty ($k = 2$).

### Headers

Symbol, then unit in **square brackets**, dimensionless as `[--]`. Same unit
convention as the figure axes: negative exponents, never a solidus, because
a solidus is ambiguous with two denominators — `W/m K` reads two ways.

| Write | Not |
|---|---|
| `$\dot{m}_\mathrm{f}$ [kg h$^{-1}$]` | `mdot [kg/h]` |
| `$k$ [W m$^{-1}$ K$^{-1}$]` | `k [W/m K]` |
| `$COP$ [--]` | `COP []` |
| `$T_\mathrm{sink}$ [$^{\circ}$C]` | `T_sink [C]` |

A table header uses the **symbol**; an axis label uses the **full name**. The
caption and the running text supply the words. Keep the symbol identical to
the one in the figures and the nomenclature list.

### Numbers

Match the decimals to what the measurement justifies, and keep a column
internally consistent: `5.27` and `4.32`, never `5.27` and `4.3`. Report an
uncertainty with the same decimals as its value. Missing entries are `--`,
never blank.

### Labels

`tab:` prefix, hyphenated: `\label{tab:mean-values}`.

---

## `siunitx` column formats

| Format | Use for |
|---|---|
| `l` | Text: case names, versions, descriptions |
| `c` | Numbers already of equal width |
| `S[table-format=4.1]` | Align on the decimal point: 4 integer digits, 1 decimal |
| `S[table-format=+2.1]` | A column containing **negative** numbers |
| `S[table-format=1.2(2)]` | Value with uncertainty — write `5.27(15)` in the source |
| `S[table-format=2.1e1]` | Scientific notation |
| `p{30mm}` | Wrapped text of fixed width |

**Count the digits before writing `table-format`.** It is a declaration, not
a hint: if a column reaches 120.0 it is `3.1`, not `2.1`.

---

## Troubleshooting

**`Missing number, treated as zero`.** A header inside an `S` column is not
wrapped in braces. Write `{$COP$ [--]}`, not `$COP$ [--]`. Without the braces
`siunitx` tries to parse the header as a number. This is the most common
error with `S` columns.

**`Overfull \hbox` inside a table.** Almost always one of two things:

* the column contains negative numbers but `table-format` has no `+`, so no
  slot is reserved for the minus sign — use `+2.1`;
* the declared digit count is too small for the largest value — a column
  reaching 120.0 needs `3.1`.

Fix the format. Do **not** reach for `\resizebox` or `\small`.

**A row silently gained vertical space, or LaTeX complains about an
undefined length.** A line ending in `\\` was followed by a line starting
with `[`, so LaTeX read it as `\\[length]`. This is easy to hit now that
units live in square brackets. Keep the bracket on the same line as the
content before it, or write `\\{}` to close the row explicitly.

**A `%`, `&`, `#` or `_` broke the compile.** These are LaTeX special
characters: write `50\%`, `A\&B`, `\#`, `\_`.

**The uncertainty is printed as `5.27(15)`.** `separate-uncertainty=true` is
missing from `\sisetup`.

**Digits are being grouped as `1 219`.** `group-minimum-digits` is 4, the
siunitx default. Set it to 5.

**The table is wider than the text block.** Do not shrink the font. Split
the table, transpose it, or use template 7 (landscape). A table that needs
`\resizebox` has too many columns.

---

## What not to do

* `|` between columns, or `\hline`
* `\resizebox` or `\small` to make a table fit
* A caption below the table
* A solidus in a unit: `[kg/h]`
* Blank cells where a value is missing — use `--`
* Retyping a number that also appears in the running text: it will drift

---

## Repository notes

* **One table, one file** if the table is generated or long:
  `\input{tables/mean_values.tex}` in the manuscript, with the file named
  after its label.
* **Keep this file compiling.** It is the reference: if someone adds a
  template, it must build clean — no errors, no overfull boxes. That is the
  only test the standard has.
* **Same numbers everywhere.** A value appearing in both a table and the text
  should come from one source, not be retyped.
* **Changing the standard changes every table.** Open an issue, recompile
  this file, and note the change in `CHANGELOG.md` — tables already submitted
  to a journal will no longer match the ones in the repository.
