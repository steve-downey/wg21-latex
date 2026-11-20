# P2988

<!--
SPDX-License-Identifier: 2.0 license with LLVM exceptions
-->

## Building P2988

Compiling the paper requires a working LaTeX installation. See instructions for configuring your system at [C++ Standard Draft Sources](https://github.com/cplusplus/draft/blob/main/README.rst)

The papers/ subdirectory has the LaTeX sources for P2988 and the supporting macro definitions. To build, run

```shell
make papers
```

A working recent Python 3 is required to format the sources for the paper. A virtual env will be created in the papers subdirectory which the `minted` LaTeX package will use.

## Numbering wording headings

Inside the `wording` environment a heading has no chapter, so its number prints
with a `?` glyph for each part it cannot know. When the paper knows where its
wording goes in the working draft, `\clausenumber` gives the next heading that
number:

```latex
\begin{wording}
\clausenumber{22.10.17.4}
\rSec3[func.wrap.move]{Move-only wrapper}
\end{wording}
```

The heading prints as 22.10.17.4, a nested `\rSec4` after it as 22.10.17.4.1,
and the next `\rSec3` as 22.10.17.5. A number of *n* parts belongs to a heading
*n*−1 levels below `\chapter`, from 1 to 6 parts. A number is only meaningful
against one revision of the draft, so name that revision in the paper.

[beman.specgen](https://github.com/steve-downey/specgen) writes
`\ifdefined\clausenumber\clausenumber{N}\fi` ahead of a generated section when
given `--section-number`, so its fragments build with or without this macro.
