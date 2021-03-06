# Chalmers Univeristy of Technology thesis package (unofficial)

This is an unofficial package that defines macros for the layout of the preamble of Master's theses at Chalmers University of Technology, according to the guidelines presented at Studentportalen. It also makes a few stylistic changes to the table of contents and sectioning macros, among other things. Hopefully it's useful to people other than myself.

Although master's theses are to be written in english, the class supports `babel` (or `polyglossia`) and provides english and swedish translations of the preamble. The package should work with any document class and font stack (it has been tested with `book`, `tufte-book` and `memoir`), as well as with other packages, but it is tailored for the `scrbook` KOMA-script document class along with Minion Pro and Cronos Pro fonts.

The actual package, consisting of the files `chs-msc-thesis.sty` and `chs-msc-thesis-logos.sty` (excepting the trademarked logo defined in the latter), is available under the MIT license (see `LICENSE`). The sample file `chs-msc-thesis-test.tex` is in the public domain. The logotypes in the four PDF files `chs-msc-full-chalmers-logo.pdf`, `chs-msc-full-chalmers-gu-logo.pdf`, `chs-msc-avancez-logo.pdf` and `chs-msc-gu-logo.pdf` is trademarked by their respective owners (Chalmers University of Technology and Gothenburg University), so take appropriate measures before using them. They have been reverse-engineered from material publically available from Studentportalen at Chalmers (see links at the end of this document).

## Usage

Install the package by putting the `chs-msc-full-chalmers-logo.pdf`, `chs-msc-full-chalmers-gu-logo.pdf`, `chs-msc-avancez-logo.pdf`, `chs-msc-gu-logo.pdf`, `chs-msc-thesis-logos.sty` and `chs-msc-thesis.sty` files either in your `TEXMFHOME` directory (recommended) or the same directory as your thesis.

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
	issn = {0000--0000},
	examiner = {Examiner name}, % required by CSE dept.
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

Additionally, the `\maketitle` macro accepts a `style` key-value option. At the moment, there are two styles: `grid` which mimics an older cover page template, and `line` which mimics the templates issued by Chalmers on 2014-06-04. The default is `grid`, in order to preserve compatibility with older documents.

Finally, the `legal-text` option may be supplied to force the inclusion of a legal waiver on the colophon which is required by some departments.

## Options

The package provides a few options to control the setup of style elements, which may not be desirable is the package is only used to generate the title pages. There are five boolean key-value options, all initially set to `true`, and one regular option:

* `headers=false` disables style changes to the page header, in particular changes applied to the `\chaptermark` and `\sectionmark` commands.
* `titles=false` disables style changes to the sectioning commands.
* `toc=false` disables changes to the table of contents style.
* `figures=false` disables changes to the styling of figure (and table) captions.
* `footnotes=false` disables loading of the `footmisc` package with a few predefined options (note: use `\PassOptionsToPackage` if you just want to pass additional options to `footmisc`).
* `nothing` disables all of the above.

When using the package with `tufte-book`, the `nothing` option is automatically applied. When using the package with `memoir`, the `toc=false` option is automatically applied.

## See also

* The example file `chs-msc-thesis-test.tex`
* [Micket/chalmers](https://github.com/Micket/chalmers), a seemingly less unofficial document class for theses at Chalmers
* The [Master's thesis guidelines at Studentportalen](https://student.portal.chalmers.se/en/chalmersstudies/masters-thesis/Pages/design-and-publish-masters-thesis.aspx)
* Sources for the `chs-msc-full-*-logo.pdf` files: [Chalmers](http://www.chalmers.se/sv/om-chalmers/profil-och-identitet/sidor/logotyp.aspx) and [Göteborgs Universitet](http://bildbank.gu.se/logotyperochmallar/).
