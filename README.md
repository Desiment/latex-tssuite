# tssuite.sty

`tssuite` is a personal LaTeX package for everyday text and structure helpers:
compact lists, small-caps shortcuts, reusable text fields, draft todo notes, and
theorem declarations.

The package is modular. Core list styles and text fields are always available;
additional features are enabled with package options.

## Features

- `enumitem` list presets: `compact`, `widemargins`, and `inline`.
- Text fields with `\CreateTextField` and `\PrintTextField`.
- Optional small-caps shortcut commands with `\DefineScName` and
  `\DefineScNames`.
- Optional draft mode with `todonotes` and widened physical pages for margin
  notes.
- Optional theorem helpers backed by `keytheorems`.
- Optional framed theorem wrappers backed by `mdframed` and TikZ.
- LuaTeX-only `lua-widow-control` when compiled with LuaLaTeX.

## Usage

Load the features needed by the document:

```latex
\usepackage[shortcuts,theorems]{tssuite}
```

Available options:

- `shortcuts`: enable `\DefineScName` and `\DefineScNames`.
- `draft`: enable visible todo notes and margin-note page extension.
- `todoextension=<length>`: set the per-side page extension used by `draft`.
- `theorems`: enable theorem declaration helpers.
- `framedtheorems`: enable framed theorem wrappers and imply `theorems`.

## Examples

The `examples/` directory contains one full guided document and focused examples
for individual feature groups:

- `example.tex`: all features together in one informal guide.
- `core.tex`: list presets and text fields, with no optional package features.
- `shortcuts.tex`: small-caps command generation through the `shortcuts` option.
- `draft.tex`: todo notes and page extension through the `draft` option.
- `theorems.tex`: theorem declarations, framed wrappers, stored theorems, and theorem lists.

Build examples from the `examples/` directory:

```sh
cd examples
latexmk -r latexmkrc example.tex
latexmk -r latexmkrc core.tex shortcuts.tex draft.tex theorems.tex
```

The build writes auxiliary files to `examples/.build/` and final PDFs directly to
`examples/`.

## Common Commands

```latex
\CreateTextField{\AuthorName}{author}
\AuthorName{Alice Example}
\PrintTextField{author}

\DefineScName[\Cpp]{C++}
\DefineScNames{Python, Rust, LuaLaTeX}

\NewNumberedTheorem{theorem}{Theorem}
\NewDocumentTheorem{definition}{Definition}
\MakeFramedTheorem{ftheorem}{theorem}
```

See `examples/example.tex` for a guided document that explains each feature in
context.

## Repository Layout

```text
tssuite/
├── tssuite.sty
├── code/
│   ├── tssuite.draft.code.tex
│   ├── tssuite.fields.code.tex
│   ├── tssuite.lists.code.tex
│   ├── tssuite.shorthands.code.tex
│   └── tssuite.theorems.code.tex
└── examples/
    ├── core.tex
    ├── draft.tex
    ├── example.tex
    ├── shortcuts.tex
    ├── theorems.tex
    └── latexmkrc
```

## ToDo

- [ ] Document-like typesetting helpers for formal documents.
- [ ] Test-page utility for checking geometry and page sizes.
- [ ] Font-switching helpers.
- [ ] Draft-mode compile-date macro.
- [ ] Epigraph helpers.
- [ ] Standard setup plugins.
