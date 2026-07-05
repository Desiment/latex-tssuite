# tssuite: Draft Todos

## When To Use

Use draft mode when margin todo notes should appear in a widened PDF page while
the logical text block remains centered.

## Required Setup

```latex
\usepackage[draft,todoextension=5cm]{tssuite}
```

`todoextension` is optional and defaults to `5cm`, but it is valid only together
with `draft`.

## Commands

### `\todo[<options>]{<text>}`

The command comes from the external `todonotes` package loaded by `tssuite`.
When `draft` is active, notes are visible. When `draft` is inactive, `todonotes`
is loaded with `disable` and notes are suppressed.

```latex
\todo{Rewrite this paragraph later.}
\todo[color=yellow!30]{Check terminology.}
```

## Page Extension Behavior

Draft mode:

- Extends the physical paper width by `2 * todoextension`.
- Centers the original logical page in the wider physical page.
- Adjusts `\marginparsep` and `\marginparwidth` so right-side todo notes have room.
- Updates page dimensions at shipout.
- Recomputes margins after `\newgeometry` and `\restoregeometry` when those hooks exist.

## Memoize Interaction

If the external `memoize` package is loaded, `tssuite` wraps `\todo` so memoize
is disabled while todo notes render.

## Rules

- Use `draft` when todo notes should be visible.
- Do not use `todoextension` without `draft`.
- Keep todo notes out of final builds by removing `draft`.

## Avoid

```latex
\usepackage[todoextension=4cm]{tssuite}
```

Prefer:

```latex
\usepackage[draft,todoextension=4cm]{tssuite}
```
