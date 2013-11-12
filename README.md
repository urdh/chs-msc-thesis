# Chalmers Univeristy of Technology thesis package (unofficial)

This is an unofficial package that defines macros for the layout of the preamble of Master's theses at Chalmers University of Technology, according to the guidelines presented at Studentportalen. It also makes a few stylistic changes to the table of contents and sectioning macros, among other things. Hopefully it's useful to people other than myself.

Although master's theses are to be written in english, the class supports `babel` and provides english and swedish translations of the preamble. The package should work with any document class and font stack, as well as with other packages, but it is tailored for the `scrbook` KOMA-script document class along with Minion Pro and Cronos Pro fonts.

The actual package, consisting of the files `chs-msc-thesis.sty` and `chs-msc-thesis-logos.sty` (excepting the trademarked logo defined in the latter), is available under the MIT license (see `LICENSE`). The sample file `chs-msc-thesis-test.tex` is in the public domain. The logotypes in the two PDF files `chs-msc-avancez-logo.pdf` and `chs-msc-gu-logo.pdf` is trademarked by their respective owners (Chalmers University of Technology and Gothenburg University), so take appropriate measures before using them. They have been reverse-engineered from material publically available from Studentportalen at Chalmers (see links at the end of this document).

## Usage

Install the package by putting the `chs-msc-avancez-logo.pdf`, `chs-msc-gu-logo.pdf`, `chs-msc-thesis-logos.sty` and `chs-msc-thesis.sty` files either in your `TEXMFHOME` directory (recommended) or the same directory as your thesis.

First, load the package (`chs-msc-thesis`).
Then, issue the `\SetupMetadata` macro:

```
\SetupMetadata{
	% Required metadata
	title = {Thesis title},
	author = {Author name(s) (comma separated)},
	year = {Year},
	subject = {Subject},
	department = {Department},
	keywords = {key, word, list},
	abstract = {Arbitrarily long abstract},
	% Optional metadata
	subtitle = {Optional subtitle},
	publisher = {Optional publisher},
	series = {Optional series number},
	% Supply either both or none of these
	cover-caption = {Optional cover caption},
	cover-image = {\includegraphics{...}}
}
```

Then, issue the `\makefrontmatter` macro, with the optional argument accepting the value `gu-logo` indicating the Göteborg University variant of the front page (used at the Department och Mathematical Sciences) or no optional argument for the regular Chalmers-only front page, e.g.

```
\begin{document}
	\frontmatter
	\makefrontmatter[gu-logo]

	\cleardoublepage
	\tableofcontents
	
	\mainmatter
	...

	\backmatter
	...
\end{document}
```

## See also

* The example file `chs-msc-thesis-test.tex`
* [Micket/chalmers](https://github.com/Micket/chalmers), a seemingly less unofficial document class for theses at Chalmers
* The [Master's thesis guidelines at Studentportalen](https://student.portal.chalmers.se/en/chalmersstudies/masters-thesis/Pages/design-and-publish-masters-thesis.aspx)
