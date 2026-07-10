---
name: tssuite-40-theorems
description: Use tssuite theorem and framed theorem environments with the package's configured theorem styles.
license: MIT
compatibility: opencode
metadata:
  package: tssuite
  topic: theorems
---

# tssuite: Theorems And Framed Theorems

## When To Use

Use theorem support to declare theorem-like environments through `keytheorems`
with shorter package commands. Use framed theorem support to wrap theorem-like
environments in `mdframed` boxes.

## Required Setup

Theorem helpers only:

```latex
\usepackage[theorems]{tssuite}
```

Theorem helpers plus framed wrappers:

```latex
\usepackage[framedtheorems]{tssuite}
```

`framedtheorems` implies `theorems`.

## Theorem Declaration Commands

### `\NewNumberedTheorem{<env>}{<display name>}[<keytheorems options>]`

Creates a numbered theorem-like environment.

```latex
\NewNumberedTheorem{theorem}{Theorem}
\NewNumberedTheorem{sectiontheorem}{Section Theorem}[parent=section]
```

### `\NewStarredTheorem{<env>}{<display name>}[<keytheorems options>]`

Creates an unnumbered theorem-like environment.

```latex
\NewStarredTheorem{remark}{Remark}
```

### `\NewDocumentTheorem{<env>}{<display name>}[<common opts>][<numbered opts>][<starred opts>]`

Creates both `<env>` and `<env>*`.

```latex
\NewDocumentTheorem{definition}{Definition}
\NewDocumentTheorem{claim}{Claim}[style=definition]
```

## Framed Theorem Commands

### `\framesetup{<title>}`

Configures the next frame style. An empty title creates a plain frame; a
non-empty title creates a TikZ title node on the frame.

```latex
\framesetup{Important}
```

### `\MakeFramedTheorem{<framed env>}{<base env>}`

Creates a framed environment wrapping an existing theorem-like environment.

```latex
\NewNumberedTheorem{theorem}{Theorem}
\MakeFramedTheorem{ftheorem}{theorem}
```

Generated framed environment syntax:

```latex
\begin{ftheorem}
  Body.
\end{ftheorem}

\begin{ftheorem}[Frame title]
  Body.
\end{ftheorem}

\begin{ftheorem}[Frame title][label=thm:example,note=Extra note]
  Body.
\end{ftheorem}
```

## Commands From keytheorems

Because theorem helpers use the external `keytheorems` package, generated
environments accept ordinary `keytheorems` keys such as:

- `label=<label>`
- `note=<text>`
- `store=<name>`
- `parent=<counter>`
- `sibling=<env>`
- `style=<style>`

Useful external commands include:

- `\getkeytheorem{<stored name>}`
- `\listofkeytheorems[<options>]`

## Memoize Interaction

When `framedtheorems` is active and the external `memoize` package is loaded,
`tssuite` disables memoize while framed theorem boxes render.

## Example

```latex
\NewNumberedTheorem{theorem}{Theorem}
\NewDocumentTheorem{definition}{Definition}
\MakeFramedTheorem{ftheorem}{theorem}

\begin{theorem}[label=thm:one,note=Basic]
If $a=b$ and $b=c$, then $a=c$.
\end{theorem}

\begin{ftheorem}[Cancellation]
If $a+c=b+c$, then $a=b$.
\end{ftheorem}
```

## Rules

- Declare theorem environments in the preamble.
- Create framed wrappers only after the base theorem environment exists.
- Pass theorem keys through the optional argument of the generated environment.
