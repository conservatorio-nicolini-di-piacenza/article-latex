# XeLaTeX article template

based on the Journal Article Template available at
[LaTeX Templates](http://www.LaTeXTemplates.com).

It uses the Fonts [Alegreya](https://www.fontsquirrel.com/fonts/alegreya) for
the main text, Andale Mono for code blocks and
[Libertinus Math](https://github.com/alif-type/libertinus) for formulas.

## characteristics

Two-columns article with a focus on fonts and typographic issues. It employs
strategies to count characters and words in the final PDF.  

## usage

The main file is named `2020-GS-ARTICLE.tex` it includes a call to `gs2020.tex`
as an external style. You can create different stylesheets to call at necessity.

As ever you can run LaTeX in multiple ways. I prefer to use a makefile to
automate some passages. Bibliography printing requires multiple compilations to
connect the references, the same for the strategy adopted to count words and
characters on the final PDF.

Simply type

```bash
make
```

to generate all the passages to obtain the PDF.

Looking at the makefile there are three strategies:

 - *publish* the one you implicitly invoke with the `make` command (so `make`
   and `make publish` are equivalent). After the building process, it removes
   all the intermediate files. This is the longest-running process, not useful
   for intermediate writings, but for the publishing phase;
 - *build* the process of complete building without removing the intermediate
   file. This process is useful for the reconnection of references during
   intermediate writings;
 - *step* is the single step advancing mode, useful during writings, fast
   because it does not reconnect references, not launch the word-count strategies.

So

```bash
make step
```

is the command to the unreferenced PDF production.

```bash
make build
```

is the command to produce a full PDF, the intermediate files remain for the next build steps.

```bash
make publish
```

to produce a full PDF and clean the folder from the intermediate files.

## github usages and bash script

Using the `template` mode offered by GitHub you can generate future articles repository
by this starting point.

The following `gscom` bash script is self-explained. It is the _lazy mode on_,
with the single command `bash gscom.sh commitname` (where _commitname_ is the name you
want assign to the commit, so channge it!) you are doing all the three listed `git` commands

```bash
#!/usr/bin/env bash

# use it by terminal typing:
# bash gscom.sh commitname

git status
git add .
git commit -am "$1"
```
