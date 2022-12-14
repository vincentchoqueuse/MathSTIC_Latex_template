# Thesis template for the "MATHSTIC" PhD school.

> This repository is a clone of the inria gitlab repo: https://gitlab.inria.fr/ed-mathstic/latex-template

This repository contains a template for the thesis manuscript supporting all doctoral schools of the [MathTIC](https://www.doctorat-bretagneloire.fr/).

The main goal of this template is to provide both front and back covers of the thesis manuscript entirely written in latex. These covers have been (manually) reproduced from the original M$ Word model provided by doctoral school MathSTIC in 2018, then generalized to all doctoral schools. While the manuscript covers must follow the rules of DBL, the internal layout of the content is more flexible. The content layout provided in this template is therefore given as an exemple rather than as a  mandatory framework.

## Getting Started


#### Structure of the repository

- `main.tex` contains the backbone structure of the document, no content is present in this file
- `these-dbl.cls` contains the package dependencies, bibliography parameters including citation style and overall layout specifications including both front and back cover layouts
- `cover/front.tex` contains the variables that must be filled by the author to complete the front cover, these variables are used in `\maketitle` redefined in `these-dbl.cls`
- `cover/back.tex` contains the variables that must be filled by the author to complete the back cover, these variables are used in the macros defined in `these-dbl.cls`
- The `Makefile` helps you compile the latex and bibliography into a pdf (details below)
- The rest of the directories each contain one chapter of the document


#### Fill the front and back cover

The front cover details must be provided by filling the variables in `Couverture-these/pagedegarde.tex`.
The lines calling the `\ecoledoctorale{}` and `\etablissement{}` (i.e., institution) commands must be modified to adapt the covers to the doctoral school and institution(s) delivering the diplome (by default set to MathSTIC and Université de Rennes 1, respectively).
The file `cover/README.md` lists the supported doctoral schools and institutions, and contains links pointing to lists of domains and labs/faculties, for each doctoral school, that are needed to fill the front cover (commands `\spec{}` and `\uniterecherche{}`).
Modifying the front cover layout defined in `these-dbl.cls` should only be necessary to preserve the original layout using a few `\vspace` after filling the front cover (e.g., domain, jury section).

The back cover variables that must be filled are in `cover/back.tex`.


#### Dependencies

A LaTeX distribution such as texlive is necessary in order to compile your document. Please note some necessary packages are not directly included in a base texlive installation.

Required additional packages:

- Fedora (install using `dnf install`)
	- texlive-abstract
	- texlive-wallpaper
- Other distributions
	- TODO (contributions welcome)


#### Compile latex into pdf

A `Makefile` is provided to help you compile your document. It uses `pdflatex` and`biber` to generate the pdf file and can display it by using `evince` on Linux or `open` on MacOS.

Compile your document with `pdflatex/biber`:

	make

Display the generated pdf:

	make viewpdf

Remove all generated files, pdf included:

	make clean


#### Particularities of a multilanguage document

The list of used languages is defined in `these-dbl.cls` where the package `babel` is imported.
As the back cover contains both French and English, it is necessary to keep at least both these languages in the list.
Use `\selectlanguage{x}` (where x is `french` or `english`) to switch language after its usage.

If the main language of your document is English, you must apply the following changes to the provided template:

- replace `\selectlanguage{french}` by `\selectlanguage{english}` in `main.tex`
- edit line 488 of `these-dbl.cls` to replace `Partie` by `Part` in the headers
- include a summary in French of at least 4 pages


### Change the content font

The required font for the covers is Arial but you can use another font for the content of the thesis by redefining the commands `\rmdefault` and `\sfdefault` as commented out in `these-dbl.cls`.
Currently the latex default font is the one used for the content.


-----

# ![(git logo)](https://yousername.gitlab.io/img/logo_git_50x50.png) Contribute

To propose changes, (1) you first have to request access to this repository (top page link, [HOWTO](https://docs.gitlab.com/ee/user/project/members/#project-membership-and-requesting-access)), (2) push your branch to this repository once access is granted, and finally (3) create a pull request with your proposed changes. Or just create an issue.

* Maintainers: Pierre-Louis Roman (pierre-louis.roman@epfl.ch).

* Contributors: Louiza Yala (original & main developer), Josquin Debaz, Pierre-Louis Roman, Lucas Bourneuf, Corentin Guezenoc, Clément Elbaz, Florian Arrestier, Alexandre Honorat.

* Upstream git repository: https://gitlab.inria.fr/ed-mathstic/latex-template

