# tssuite: Loading And Options

## When To Use

Use `tssuite` for document text utilities: list presets, reusable text fields,
small-caps shortcuts, todo notes, theorem declarations, and framed theorem
wrappers.

## Required Setup

Core-only loading:

```latex
\usepackage{tssuite}
```

Full feature loading:

```latex
\usepackage[
  shortcuts,
  draft,
  todoextension=5cm,
  theorems,
  framedtheorems
]{tssuite}
```

## Options

- `shortcuts`: enables `\DefineScName` and `\DefineScNames`.
- `draft`: enables visible todo notes and page extension for margin notes.
- `todoextension=<length>`: sets per-side physical-page extension for draft mode. Requires `draft`.
- `theorems`: enables theorem declaration helpers.
- `framedtheorems`: enables framed theorem wrappers and implies `theorems`.

## Always-Available Features

- List presets: `compact`, `widemargins`, `inline`.
- Text fields: `\CreateTextField`, `\PrintTextField`.

## External Dependencies

The package loads `stackengine`, `multicol`, `microtype`, `enumitem`, `xparse`,
and `iftex`. Under LuaLaTeX, it also loads `lua-widow-control`.

When `draft` is not active, the package loads `todonotes` with `disable`, so
ordinary `\todo` calls are suppressed.

## Rules

- Use only the options needed by the document.
- Use `framedtheorems` when framed wrappers are needed; it automatically turns on theorem support.
- Do not use `todoextension` without `draft`.
