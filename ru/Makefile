LUALATEX = lualatex --shell-escape %O %S
LUALATEX2 = lualatex --jobname=%B "\input{structure-wrapper} \input{%S}"
LUALATEX3 = lualatex --jobname=%B "\input{beamer-wrapper} \input{%S}"

all: part1.pdf part2.pdf part3.pdf

#
# Part 1
#
part1.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX)' $(@:%.pdf=%.tex)

#
# Part 2
#
part2.pdf: structure-title.pdf structure-sections.pdf \
	   structure-crossref.pdf structure-exercise-solution.pdf \
	   structure-exercise-full-solution.pdf media-graphics.pdf bib-example.pdf
	latexmk -pdf -pdflatex='$(LUALATEX)' $(@:%.pdf=%.tex)

structure-title.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

structure-sections.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

structure-crossref.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

structure-exercise-solution.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

structure-exercise-full-solution.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

media-graphics.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

bib-example.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

#
# Part 3
#
part3.pdf: recap-structure.pdf recap-exercise.pdf \
	   recap-exercise-solution.pdf beamer-minimal.pdf beamer-theme.pdf \
	   beamer-exercise-solution.pdf todonotes-example.pdf
	latexmk -pdf -pdflatex='$(LUALATEX)' $(@:%.pdf=%.tex)

recap-structure.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX2)' $(@:%.pdf=%.tex)

recap-exercise.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

recap-exercise-solution.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

beamer-minimal.pdf:
	latexmk -pdf -pdflatex='$(LUALATEX3)' $(@:%.pdf=%.tex)

beamer-theme.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

beamer-exercise-solution.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

todonotes-example.pdf:
	latexmk -lualatex $(@:%.pdf=%.tex)

latex-course.tgz: part1.pdf part2.pdf part3.pdf basics-exercise-1-solution.tex \
		  basics-exercise-1.tex basics-exercise-2-solution.tex \
		  basics-exercise-2.tex basics.tex bib-example.tex preamble.tex \
		  structure-exercise-solution.tex structure-exercise-solution.pdf \
		  structure-exercise-full-solution.tex structure-exercise.tex \
		  big_chick.png bib-exercise.bib recap-exercise.tex \
		  recap-exercise-solution.pdf beamer-minimal.tex beamer-exercise.tex \
		  beamer-exercise-solution.tex beamer-exercise-solution.pdf
	tar czf latex-course.tgz $^

clean:
	rm -rf *.log *.aux *.out *.nav *.snm *.toc *.vrb *.pyg *.bbl *.blg \
		*.listing *.fdb_latexmk *.fls *.tdo *.bcf *.run.xml _minted-* \
		structure-crossref.pdf structure-sections.pdf structure-title.pdf \
		media-graphics.pdf bib-example.pdf recap-structure.pdf

clobber: clean
	rm -f part1.pdf part2.pdf part3.pdf

.PHONY: part1.pdf \
	part2.pdf structure-title.pdf structure-sections.pdf structure-crossref.pdf \
	structure-exercise-solution.pdf structure-exercise-full-solution.pdf \
	media-graphics.pdf bib-example.pdf \
	part3.pdf recap-structure.pdf recap-exercise.pdf recap-exercise-solution.pdf \
	beamer-minimal.pdf beamer-theme.pdf beamer-exercise-solution.pdf \
	todonotes-example.pdf clean clobber all
