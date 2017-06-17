LUALATEX = lualatex --shell-escape %O %S
LUALATEX2 = lualatex --jobname=%B "\input{structure-wrapper} \input{%S}"
LUALATEX3 = lualatex --jobname=%B "\input{beamer-wrapper} \input{%S}"

all: part1.pdf part2.pdf part3.pdf

#
# Part 1
#
part1.pdf: part1.tex preamble.tex
	latexmk -pdf -pdflatex='$(LUALATEX)' $<

#
# Part 2
#
part2.pdf: part2.tex preamble.tex structure-title.pdf structure-sections.pdf \
	   structure-crossref.pdf structure-exercise-solution.pdf \
	   structure-exercise-full-solution.pdf media-graphics.pdf bib-example.pdf
	latexmk -pdf -pdflatex='$(LUALATEX)' $<

structure-title.pdf: structure-title.tex structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

structure-sections.pdf: structure-sections.tex structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

structure-crossref.pdf: structure-crossref.tex structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

structure-exercise-solution.pdf: structure-exercise-solution.tex
	latexmk -lualatex $<

structure-exercise-full-solution.pdf: structure-exercise-full-solution.tex
	latexmk -lualatex $<

media-graphics.pdf: media-graphics.tex structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

bib-example.pdf: bib-example.tex bib-example.bib structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

#
# Part 3
#
part3.pdf: part3.tex preamble.tex rotated-triangle.tex \
	   escher-brick-penrose-triangle.tex computer-science-mindmap.tex \
	   gajski-kuhn-y-chart.tex recap-structure.pdf recap-exercise.pdf \
	   recap-exercise-solution.pdf beamer-minimal.pdf beamer-theme.pdf \
	   beamer-exercise.pdf beamer-exercise-solution.pdf todonotes-example.pdf
	latexmk -pdf -pdflatex='$(LUALATEX)' $<

recap-structure.pdf: recap-structure.tex structure-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX2)' $<

recap-exercise.pdf: recap-exercise.tex
	latexmk -lualatex $<

recap-exercise-solution.pdf: recap-exercise-solution.tex
	latexmk -lualatex $<

beamer-minimal.pdf: beamer-minimal.tex beamer-wrapper.tex
	latexmk -pdf -pdflatex='$(LUALATEX3)' $<

beamer-theme.pdf: beamer-theme.tex
	latexmk -lualatex $<

beamer-exercise.pdf: beamer-exercise.tex
	latexmk -lualatex $<

beamer-exercise-solution.pdf: beamer-exercise-solution.tex
	latexmk -lualatex $<

todonotes-example.pdf: todonotes-example.tex
	latexmk -lualatex $<

latex-course.tgz: part1.pdf part2.pdf part3.pdf basics-exercise-1-solution.tex \
		  basics-exercise-1.tex basics-exercise-2-solution.tex \
		  basics-exercise-2.tex basics.tex bib-example.tex preamble.tex \
		  structure-exercise-solution.tex structure-exercise-solution.pdf \
		  structure-exercise.tex big_chick.png bib-exercise.bib \
		  recap-exercise.tex recap-exercise-solution.pdf beamer-minimal.tex \
		  beamer-exercise.tex beamer-exercise-solution.pdf
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
	structure-exercise-solution.pdf media-graphics.pdf bib-example.pdf \
	part3.pdf recap-structure.pdf recap-exercise.pdf recap-exercise-solution.pdf \
	beamer-minimal.pdf beamer-theme.pdf beamer-exercise.pdf \
	beamer-exercise-solution.pdf todonotes-example.pdf \
	clean clobber
