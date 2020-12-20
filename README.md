# xindy-sanskrit-workaround
hacky xindy stylesheet for sorting Sanskrit indices (romanized according to IAST)

## Dependencies
xindy

## a rather suboptimal and tedious solution
[Xindy](http://www.xindy.org/) is a feature-rich indexing processor with support for many languages, but Sanskrit is not supported and looking at the [remnants of past attempts]() does not inspire much confidence it ever will be. With xindy not having received updates for such a long time, I was reluctant to devote much to creating a language support as intended by the developers and resorted to an easy stylesheet inspired by [Dominik Wujastyk's “kludge”](https://cikitsa.blogspot.com/2016/07/getting-xindy-to-work-for-iast-encoded.html) to suit my needs. Maybe it too can be useful for others; it beats manually sorting indices.

## Usage
1. In the preamble of your LaTeX file load an indexing package that has xindy-support, like `\usepackage[xindy]{imakeidx}`,
2. compile `some.tex`,
3. let xindy write the final index with `xindy -M iast.xdy -C utf8 some.idx`,
4. (optional) style the index file `some.ind`,
5. compile `some.tex` again.

## indexing with reference systems other than page numbers
1. Define an empty command in the preamble of your LaTeX file with `\newcommand{\indexentry}[2]{}` and index according to the syntax `\indexentry{lemma}{reference}`,
2. extract raw index with `grep -o \\\\indexentry{[^}]*}{[^}]*} some.tex > some.idx`,
3. let xindy write the final index with `xindy -M iast.xdy -C utf8 some.idx`,
4. (optional) style the index file `some.ind`,
5. compile `some.tex`.