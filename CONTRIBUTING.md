# Contributing

This package follows the shared suite convention used by `flsuite`, `refsuite`,
and `tssuite`: each package has a small hub file, optional implementation
modules under `code/`, and runnable documentation under `examples/`.

## Layout

```text
tssuite/
├── tssuite.sty
├── code/
│   └── tssuite.<module>.code.tex
├── examples/
│   ├── example.tex
│   ├── latexmkrc
│   └── .build/
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

## Build Examples

Run example builds from the `examples/` directory:

```sh
cd examples
latexmk -r latexmkrc example.tex
```

The build convention is:

```perl
$aux_dir = '.build';
$out_dir = '.';
ensure_path('TEXINPUTS', '..//');
```

Auxiliary files belong in `examples/.build/`. Final PDFs belong directly in
`examples/`, not in `.build/` or a package-level `build/` directory.

## Package Structure

- Keep `tssuite.sty` as the hub for dependencies, option processing, validation,
  and conditional module loading.
- Keep implementation in `code/tssuite.<module>.code.tex` files.
- Load third-party packages from `tssuite.sty`, not from module files, unless a
  module is intentionally standalone.
- Keep public commands in PascalCase, for example `\CreateTextField`.
- Keep internal LaTeX2e commands package-prefixed, for example
  `\@tssuite@todoextension`.
- Keep expl3 internals package-prefixed, for example `\tssuite_field_set:nn`.

## Comments

Comments should explain package structure and non-obvious behavior. Prefer:

- A short file header explaining the module purpose.
- Section dividers for major blocks such as options, messages, internals, and
  user commands.
- Doc comments before public commands and complex internal helpers.
- Short rationale comments for option implications or engine-specific behavior.

Avoid comments that merely restate the next line of code.

## README And Examples

- Keep `README.md` usable as the first point of reference.
- Keep `examples/example.tex` compilable and explanatory.
- Examples should demonstrate the package workflow, not only exercise commands.
- If an option changes build requirements, document it in both the README and
  the example.

## Verification

Before considering a change complete, compile the example that covers the edited
feature. If a build cannot be run because a TeX dependency is unavailable, note
the missing dependency in the change summary.
