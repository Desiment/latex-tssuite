---
name: tssuite-20-shortcuts
description: Use tssuite small-caps text shortcuts for consistent inline terminology and abbreviations.
license: MIT
compatibility: opencode
metadata:
  package: tssuite
  topic: shortcuts
---

# tssuite: Small-Caps Shortcuts

## When To Use

Use the `shortcuts` option when the same names, tools, languages, or technical
terms should be consistently printed in small caps.

## Required Setup

```latex
\usepackage[shortcuts]{tssuite}
```

## Commands

### `\DefineScName[<cmd>]{<text>}`

Defines one zero-argument command that prints `<text>` in `\textsc`.

Use the optional command argument when the text is not a valid or desirable
command name.

```latex
\DefineScName[\Cpp]{C++}
\DefineScName[\LatexThree]{LaTeX3}

\Cpp{}
\LatexThree
```

Without the optional argument, the command name is derived by concatenating the
space-separated words.

```latex
\DefineScName{GitHub}
\DefineScName{Visual Studio Code}

\GitHub
\VisualStudioCode
```

### `\DefineScNames{<comma-separated text list>}`

Defines multiple generated small-caps commands.

```latex
\DefineScNames{Python, Rust, LuaLaTeX}

\Python, \Rust, \LuaLaTeX
```

## Rules

- Define shortcuts in the preamble.
- Use explicit command names for text containing symbols such as `+`.
- Do not redefine an existing command; the package reports an error instead of overwriting it.
- Generated names preserve the capitalization and spelling of the words after spaces are removed.

## Avoid

```latex
\DefineScName{C++}
```

Prefer:

```latex
\DefineScName[\Cpp]{C++}
```
