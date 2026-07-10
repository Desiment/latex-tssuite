---
name: tssuite-10-lists-fields
description: Use tssuite list helpers and text field commands for compact lists and interactive document fields.
license: MIT
compatibility: opencode
metadata:
  package: tssuite
  topic: lists-fields
---

# tssuite: Lists And Text Fields

## When To Use

Use core `tssuite` features for compact list styling and reusable document
metadata fields.

## Required Setup

```latex
\usepackage{tssuite}
```

## List Keys

These keys are defined through `enumitem` and can be used with `itemize`,
`enumerate`, or `description` where appropriate.

### `compact`

Removes vertical spacing between list items.

```latex
\begin{itemize}[compact]
  \item first item
  \item second item
\end{itemize}
```

### `widemargins`

Increases left margin and label indentation for readability.

```latex
\begin{enumerate}[widemargins]
  \item A longer item with more structure.
\end{enumerate}
```

### `inline`

Formats list items inline with `\quad` joins. This key is intended for inline
list contexts supplied by the document's `enumitem` setup.

```latex
% Use with an inline list environment made available by your document setup.
\begin{<inline-list>}[inline]
  \item first
  \item second
\end{<inline-list>}
```

## Text Field Commands

### `\CreateTextField{<setter>}{<field>}`

Creates a setter command and an internal storage field.

```latex
\CreateTextField{\AuthorName}{author}
\AuthorName{Alice Example}
```

### `\PrintTextField{<field>}`

Prints the current value stored in a field.

```latex
Author: \PrintTextField{author}
```

## Rules

- Create fields in the preamble.
- The setter command must not already exist.
- The field name must not already exist.
- A field initially stores its own name until the setter is called.
- Calling the setter again updates the value globally.

## Errors

The package reports errors for:

- duplicate field names
- setter command names that already exist
- printing an unknown field

## Example

```latex
\CreateTextField{\ProjectTitle}{project}
\ProjectTitle{Lecture Notes}

\begin{document}
Project: \PrintTextField{project}
\ProjectTitle{Revised Lecture Notes}
Project: \PrintTextField{project}
\end{document}
```
